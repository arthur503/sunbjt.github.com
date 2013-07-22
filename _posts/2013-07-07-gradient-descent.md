--- 
layout: post
title: Gradient descent
tags: 
- bigdata
- business
status: publish
type: post
published: false
---


����

    1 1 7.97
    2 1 10.2
    3 1 14.2
    4 1 16.0
    5 1 21.2

�ű���

    A <- x[,1:2]
    b <- x[,3]
    C <- t(A) %*% A
    solve(C, t(A)%*%b)

���뽫����ת��Ϊ������ܽ���solve�����ͬ
    
    lm(b ~ A)


A <- read.csv(textConnection("
3 2 4 0 0 0 0
1 0 1 0 0 0 0
0 1 2 0 0 0 0
0 0 0 1 1 1 1
0 0 0 1 0 1 1
0 0 0 3 2 2 3
"), header = FALSE, sep = ' ')


������������ó�����޹�˾

http://www.quuxlabs.com/blog/2010/09/matrix-factorization-a-simple-tutorial-and-implementation-in-python/

# ����ֽ����ѧԭ��

����Լ��һ�·��ţ������û���users���ļ��� $$U$$���Լ���Ʒ�ļ��� $$D$$����$$R$$ ����ʾ�û���Ʒ��Ϣ�Ĺ��֣�$$U \times D $$�����������������ҳ� K ��Ǳ�ڵ������������ҵ������¾���P��$$U \times K$$����Q��$$D \times K$$����ʹ�ã�

$R = P \times Q^T = \hat{R}$

��ʱ��P���������е��û���U���������Ϣ������������Q���������Ʒ�������Ϣ����������������ҵ������������أ�

���е�һ�ַ��������ݶ��½���gradient descent���������ȸ�P��QһЩ��ʼֵ��Ȼ�����R��$$P \times Q$$�Ĳ��죬����ͨ��������С�����ߵĲ��졣�����������һ�������µķ�ʽ��ʾ��

$e_{ij}^2 = (r_{ij} - \hat{r}_{ij})^2 = (r_{ij} - \sum_{k=1}^K p_{ik} q_{kj})^2$ 

������ʽ�����Ǳ����ҵ�һ���������Ż�$$p_{ik},q_{kj}$$�����仰˵��������Ҫ֪����ǰֵ���ݶ��½�����

$\frac{\partial}{\partial p_{ik} e_{ij}^2} = -2(r_{ij} - \hat{r}_{ij})(q_{kj}) = -2 e_{ij}q_{kj}$
 
$\frac{\partial}{\partial q_{ik} e_{ij}^2} = -2(r_{ij} - \hat{r}_{ij})(p_{ik}) = -2 e_{ij}p_{ik}$

��Ȼ�Լ��ҵ��ݶȣ�������

$p_{ik}^' = p_{ik} + 2\alpha e_{ij} q_{kj}$

$q_{kj}^' = q_{kj} + 2\alpha e_{ij} p_{ik}$

����$$\alpha$$ ��һ�������������ݶȵĲ�����Ϊ�˱���Խ���ֲ�����ֵ������$$\alpha$$һ�㶼��һ����С����������0.0002��

����һ�����������ˣ�

> ���������õ�P��Q�ĳ˻�ͬR��ȫһ�£���ôδ�۲��ֵ����ʾΪ�����Ϊ�����������㡣

������Ҫ����һ�£�`����ֻ��ԭʼ���ݲ�Ϊ���Ԫ�������߲��죬������ȫ����Ԫ�ء�`


# ������ Regularization

Ϊ�˱������ϣ�����һ�������Regularization����Ϊ�ͷ��һ��������һ��$$\beta$$���޸�����ƽ����


$e_{ij}^2 = (r_{ij} - \sum_{k=1}^K p_{ik} q_{kj})^2 + \frac{\beta}{2} \sum_{k=1}^K(||P||^2 + ||Q||^2)$

$$\beta$$���������û���������Ʒ�����ĳ̶ȣ�magnitudes������֤P��Q��R�Ľ��ƣ����������̫�����ֵ��

�����ݶ��½��Ĺ���ͱ�������£�

$p_{ik}^' = p_{ik} + 2\alpha e_{ij} q_{kj} - \beta p_{ik}$

$q_{kj}^' = q_{kj} + 2\alpha e_{ij} p_{ik} - \beta q_{kj}$




