Implantação e Diagnóstico de uma Rede Corporativa

Laboratório feito no Cisco Packet Tracer: uma rede com 4 departamentos (Administração, Financeiro, RH e TI), cada um com o seu switch, o seu servidor DHCP e a sua própria rede IP. O objetivo é implantar a rede, testar o funcionamento dentro de cada departamento e entender por que os departamentos não se comunicam entre si.

Regra do laboratório: os switches dos departamentos não são conectados entre si.

Topologia
Departamento	Cor na topologia	Switch
ADM – Administração	Azul claro	Switch0
FIN – Financeiro	Vermelho	Switch3
RH – Recursos Humanos	Amarelo	Switch4
TI – Tecnologia da Informação	Verde	Switch2

Padrão de nomes dos dispositivos: SIGLA-TIPO+NÚMERO. Tipos: PC (computador), LT (laptop), PR (impressora), SRV (servidor). Exemplos: RH-PC01, TI-LT01, FIN-PR01.

Plano de endereçamento (VLSM)

Cada rede foi dimensionada pela quantidade de dispositivos do departamento.

Departamento	Rede	Máscara	Endereços usáveis	Broadcast	Servidor DHCP
ADM	192.168.10.0/28	255.255.255.240	.1 a .14	.15	192.168.10.2
FIN	192.168.20.96/28	255.255.255.240	.97 a .110	.111	192.168.20.98
RH	192.168.30.96/27	255.255.255.224	.97 a .126	.127	a confirmar
TI	192.168.40.96/29	255.255.255.248	.97 a .102	.103	192.168.40.98

Como achar o endereço de rede e o de broadcast: o primeiro endereço do bloco é o da rede e o último é o de broadcast. Nenhum dos dois pode ser usado por um dispositivo.

Configuração do DHCP

Em cada servidor: Services → DHCP → On. O servidor usa IP fixo e o pool começa depois do IP do servidor, para o DHCP não entregar o endereço do servidor nem o de broadcast.

Departamento	Start IP Address	Maximum Number of Users
ADM	192.168.10.3	12
FIN	192.168.20.99	12
RH	192.168.30.99	28
TI	192.168.40.99	4
