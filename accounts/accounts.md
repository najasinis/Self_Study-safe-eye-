# __init__.py:

Python 패키지임을 나타내는 빈 파일
해당 디렉토리가 Python 패키지로 취급되도록 함


# admin.py:

Django 관리자 페이지 설정
모델을 관리자 페이지에 등록하고 커스터마이징

pythonCopyfrom django.contrib import admin
from .models import UserToken

admin.site.register(UserToken)

# apps.py:

앱의 기본 설정
AppConfig 클래스 포함

pythonCopyfrom django.apps import AppConfig

class AccountsConfig(AppConfig):
    name = 'accounts'
    verbose_name = '계정 관리'

# forms.py:

사용자 입력 폼 정의
회원가입, 로그인 등의 폼

pythonCopyfrom django import forms
from django.contrib.auth.forms import UserCreationForm

class SignUpForm(UserCreationForm):
    email = forms.EmailField()

# models.py:

데이터베이스 모델 정의
사용자 관련 데이터 구조

pythonCopyfrom django.db import models

class UserToken(models.Model):
    token = models.CharField(max_length=255)
    is_used = models.BooleanField(default=False)

# permissions.py:

사용자 권한 설정
접근 제어 로직

pythonCopyfrom rest_framework import permissions

class IsTokenValid(permissions.BasePermission):
    def has_permission(self, request, view):
        return request.user.token.is_valid()

# serializers.py:

API를 위한 데이터 직렬화
모델 데이터를 JSON으로 변환

pythonCopyfrom rest_framework import serializers
from .models import UserToken

class UserTokenSerializer(serializers.ModelSerializer):
    class Meta:
        model = UserToken
        fields = ['token', 'is_used']

# tests.py:

단위 테스트 코드
기능 테스트

pythonCopyfrom django.test import TestCase
from .models import UserToken

class UserTokenTests(TestCase):
    def test_token_creation(self):
        token = UserToken.objects.create(token="test")
        self.assertFalse(token.is_used)

# urls.py:

URL 패턴 정의
뷰와 URL 매핑

pythonCopyfrom django.urls import path
from . import views

urlpatterns = [
    path('login/', views.login_view, name='login'),
    path('signup/', views.signup_view, name='signup'),
]

# views.py:

뷰 로직 구현
요청 처리 및 응답 생성

pythonCopyfrom django.shortcuts import render
from .forms import SignUpForm

def signup_view(request):
    if request.method == 'POST':
        form = SignUpForm(request.POST)
        if form.is_valid():
            user = form.save()
            return redirect('login')
    else:
        form = SignUpForm()
    return render(request, 'signup.html', {'form': form})

# fixtures 폴더:

초기 데이터를 위한 JSON/YAML 파일들
테스트나 개발 환경 설정에 사용

jsonCopy// initial_data.json
{
    "model": "accounts.usertoken",
    "pk": 1,
    "fields": {
        "token": "initial_token",
        "is_used": false
    }
}
