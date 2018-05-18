---
layout: post
title:  "aws vpc, subnet 개념정리"
date:   2018-05-16 12:00:00 +0900
ategories: AWS
---
[https://docs.aws.amazon.com/ko_kr/AmazonVPC/latest/UserGuide/VPC_Subnets.html](https://docs.aws.amazon.com/ko_kr/AmazonVPC/latest/UserGuide/VPC_Subnets.html) 의 내용을 요약한 내용입니다.

VPC(Virtual Private Cloud) AWS계정 전용 가상 네트워크이다.\\
AWS 클라우드에서 다른 가상 네트워크와 논리적으로 분리 생성시 CIDR 블록을 지정해야 한다.\\

그 범위의 블록에 대해서는 VPC 내부의 subnet 끼리 통신 할 수 있다. \\

VPC는 리전의 모든 가용 영역에 적용된다. 

각 가용영역에 하나 이상의 서브넷을 추가할 수 있다.

가용영역이란 것은 분리가 되어있기 때문에 하나의 가용영역에서 장애가 발생해도 다른 서브넷에 영향을 끼치지 않는다.

따라서, 애플리케이션을 다른 가용영역에 따로 넣어두면 가용영역의 장애에도 보호 받을수 있다.

서브넷 생성시에도 CIDR 블록을 지정하는데 이때 CIDR 블록은 VPC블록 범위의 내이다.

![Image](https://docs.aws.amazon.com/ko_kr/AmazonVPC/latest/UserGuide/images/subnets-diagram.png)

VPC 10.0.0.0/16

Subnet1 10.0.0.0/24

Subnet2 10.0.1.0/24

각 서브넷은 route table을 가지고 있는데

만약에 route table을 통해 internet GW와 연결이 된 subnet이라면? 

__public subnet__

만약에 route table을 통해 internet GW과 연결이 되지않은 subnet이라면? 

__private subnet__

만약에 route table을 통해 internet GW과 연결이 되지않고 VPN과 연결된 subnet이라면?

__vpn 전용 subnet__






VPC의 IPv4 CIDR 블록의 크기 /16 ~ /28

권장하는 private IPv4 주소 범위에 속하는 CIDR (물론 이것 이외에 것도 CIDR블록으로 사용해서 VPC를 생성 할 수 있음)

10.0.0.0 - 10.255.255.255 (10/8 접두사)

172.16.0.0 - 172.31.255.255 (172.16/12 접두사)

192.168.0.0 - 192.168.255.255 (192.168/16 접두사)

출처 : https://docs.aws.amazon.com/ko_kr/AmazonVPC/latest/UserGuide/VPC_Scenario2.html

Security Group - 인스턴스용 인바운드 아웃바운드 트래픽 제어

Network ACL - 서브넷용 인바운드 아웃바운드 트래픽 제어
