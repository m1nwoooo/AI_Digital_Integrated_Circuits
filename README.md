# AI_Digital_Integrated_Circuits
Hierarchical ASIC Full Flow Design &amp; Verification using Synopsys ICC2 on TSMC 28nm Process


각 과제의 상세한 설계 과정 및 분석 결과는 **Assignment#.pdf**로 첨부하였습니다.


## 📋 프로젝트 개요

본 프로젝트는 TSMC 공정 라이브러리를 활용하여 RCA 기반 8-bit multiplier부터 4×4 Systolic Array까지 디지털 회로의 Hierarchical Design Flow(Backend)을 학습한 과제입니다.

## 🎯 주요 학습 목표

- Hierarchical Synthesis를 통한 대규모 설계 최적화
- Static Timing Analysis (STA)와 Dynamic Simulation
- Physical Design (Place & Route) 
- Power, Performance, Area (PPA) 최적화

## 📂 과제 구성
---
### Assignment 1: RCA 기반 8-bit Multiplier 합성
**목표**: Design Compiler를 이용한 기본 합성 및 주파수별 PPA 분석

**주요 결과**:
- **Maximum Frequency**: 2.4GHz (timing violation 없는 최대 주파수)
- **Optimal Frequency**: 1GHz (PPA 균형점)
- **합성 범위**: 200MHz ~ 3GHz (200MHz 단위)

**핵심 학습 내용**:
- Behavior simulation → Logic synthesis 과정
- Timing report 분석 (Slack Violation)
- Frequency-Area-Power trade-off 관계
---
### Assignment 2: MAC (Multiply-Accumulate) 모듈 합성
**목표**: Hierarchical synthesis 및 PrimeTime을 이용한 정밀 STA

**주요 결과**:
- **Maximum Frequency**: 2.0GHz
- **Optimal Frequency**: 2.0GHz
- **Area**: 570.654 µm²
- **Power**: 0.665 mW

**핵심 학습 내용**:
- Submodule 기반 Hierarchical Synthesis
- Design Compiler vs PrimeTime 차이 분석
- Wire Load Model vs RC 기반 delay 계산
---
### Assignment 3: 4×4 Systolic Array 합성 및 Post-Synthesis Simulation
**목표**: SDF를 이용한 동적 타이밍 시뮬레이션 및 검증

**주요 결과**:
- **Maximum Frequency**: 2.4GHz (mac8_2.6GHz + mult8_2.4GHz 조합)
- **Optimal Frequency**: 2.2GHz
- **Area**: 13,900 µm²
- **Power**: 15.9 mW

**핵심 학습 내용**:
- QuestaSim을 이용한 gate-level simulation
- SDF back-annotation 기법
- STA vs Dynamic Simulation 차이점
- Submodule 합성 주파수 최적화
---
### Assignment 4: Physical Design (Place & Route)
**목표**: ICC2를 이용한 Chip Layout 생성 및 최종 PPA 최적화

**최종 PPA 결과**:
- **Performance**: 1.25 GHz
- **Power**: 8.88 mW
- **Area**: 12,067 µm²
- **Utilization**: 76.3%

**핵심 설계 결정**:
- Core size: 110µm × 110µm (정사각형 구조)
- I/O port 4면 분산 배치 (congestion 완화)
- Clock signal 위치: 중앙 (55µm)
- PG strap: M4/M5 layer, width 0.5µm, pitch 25µm

**최적화 과정**:
1. **Area 최적화**: Utilization 70-80% 목표로 core size 조정
2. **Performance 최적화**: I/O 배치, clock 위치, placement density 조절
3. **Power 최적화**: PG strap 파라미터 튜닝

## 🛠 기술 스택

### EDA Tools
- **Design Compiler**: Logic synthesis
- **PrimeTime**: Static Timing Analysis
- **QuestaSim**: Gate-level simulation
- **ICC2**: Physical design (Place & Route)

### 공정 기술
- **Technology**: TSMC 28nm
- **Library**: RVT (Regular Vth) standard cells
- **Metal layers**: M1 ~ M7

### 설계 언어
- **Verilog HDL**: RTL 설계
- **TCL**: EDA tool scripting
- **SDF**: Delay annotation

## 📊 주요 분석 방법론

### PPA 최적화 전략
- **Min-Max Normalization**: 서로 다른 단위의 PPA 지표 정규화(min-max normalization)
- **Multi-metric Evaluation**: F/(A+P), F/A + F/P, F/(A×P), F²/(A×P)
- **Trade-off Analysis**: 주파수별 PPA 곡선 분석

## 📝 참고사항

- 모든 합성 결과는 TSMC 28nm 공정 기준
- Optimal frequency는 설계 목표(저전력/고성능/균형)에 따라 달라질 수 있음
---
