🛡️ Laboratório de Defesa Ativa: pfSense + Suricata (IDS/IPS)
1. Visão Geral do Projeto
Este projeto consistiu na implementação e configuração de um sistema de detecção e prevenção de intrusão (IDS/IPS) utilizando o motor Suricata v7.0.8 integrado ao firewall pfSense.

Evidência do Software: Figura 1: Gerenciador de pacotes do pfSense confirmando a instalação do Suricata 7.0.8_5.

2. Topologia e Configuração
Firewall: pfSense operando em ambiente virtualizado (Oracle VirtualBox).

Interfaces: Configuração de interfaces WAN (192.168.0.25) e LAN (192.168.1.1) para segmentação de rede.

3. Etapas de Implementação
A. Configuração do Motor e Regras
O motor foi configurado para processar um conjunto robusto de assinaturas. Durante a inicialização, foram carregadas com sucesso 47.458 regras do repositório Emerging Threats.

Log de Inicialização: ![Log do Suricata](Captura de tela 2026-01-18 102908.png) Figura 2: Logs do sistema confirmando o carregamento bem-sucedido de milhares de assinaturas de segurança.

B. Ativação do Modo de Prevenção (IPS)
Diferente de um IDS padrão, a interface WAN foi colocada em LEGACY MODE, permitindo a resposta automática a incidentes.

Status da Interface: Figura 3: Interface WAN operando em modo de prevenção ativa (IPS).

4. Validação e Resultados (POC)
Para validar o sistema, foi realizado um teste de acesso ao site testmyids.com, que simula um comando de root via HTTP.

Detecção: O sensor capturou o tráfego e gerou múltiplos alertas em tempo real.

Bloqueio: O IPS baniu automaticamente o IP do host agressor (217.160.0.187).

Evidência do Bloqueio Ativo: Figura 4: Tabela de 'Blocked Hosts' confirmando o banimento do IP externo após a detecção do ataque.
