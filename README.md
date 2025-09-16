# 🌐 Cloud Computing

Cloud computing é o modelo que oferece recursos de TI — como servidores, armazenamento, banco de dados, redes, software e inteligência artificial — pela internet, sob demanda e geralmente com pagamento baseado no uso.  

---

## ⚖️ On-Premise x Nuvem  

| Aspecto            | On-Premise                                                 |               Nuvem (Cloud)|
|--------------------|------------------------------------------------------------|------------------------------------------|
| **Localização**    | Infraestrutura física dentro da empresa                    | Recursos hospedados em datacenters do provedor|
| **Custos**         | Alto investimento inicial (CAPEX) e manutenção contínua    | Pagamento sob demanda (OPEX), menor investimento inicial|
| **Controle**       | Maior controle e personalização                            | Dependência do provedor|
| **Escalabilidade** | Limitada, exige novos investimentos em hardware            | Escalável rapidamente conforme a necessidade|
| **Manutenção**     | Responsabilidade da equipe interna de TI                   | Provedor cuida da manutenção e atualização|

---

## ☁️ Modelos de Serviço em Nuvem  

### 1. **IaaS (Infrastructure as a Service)**
- Infraestrutura básica de TI: servidores virtuais, armazenamento e redes.  
- Cliente gerencia sistemas operacionais e aplicações.  

### 2. **PaaS (Platform as a Service)**
- Plataforma para desenvolvimento, testes e implantação de aplicações.  
- Provedor cuida da infraestrutura; usuário foca apenas no código.  

### 3. **SaaS (Software as a Service)**
- Aplicações prontas acessadas pela internet.  
- Provedor gerencia toda a infraestrutura, plataforma e software.  

---

## ✅ Resumindo
- **On-Premise** → mais controle, mas mais custos e responsabilidades.  
- **Nuvem** → mais flexibilidade, escalabilidade e custo otimizado.  
- **IaaS** = infraestrutura, **PaaS** = plataforma, **SaaS** = software pronto.

----------------------------------------------------
# ☁️ Criação de Recursos na Nuvem Azure: SLAs e Custo-Benefício

## 🛠️ Criação de recursos
Na Azure, criar recursos significa provisionar serviços (VMs, bancos de dados, storage, redes, etc.) dentro de uma **subscription**.  
Cada recurso vem com opções de configuração que influenciam diretamente preço, desempenho e disponibilidade.  

## 📊 SLAs (Service Level Agreements)
A Microsoft define **SLAs** como garantias contratuais de disponibilidade. Exemplos:

- **VM única:** até 99,9% de disponibilidade.  
- **VMs em Availability Set:** até 99,95%.  
- **VMs em Availability Zones diferentes:** até 99,99%.  
- **Serviços gerenciados (ex: Azure SQL Database Premium):** podem chegar a 99,99% ou mais.  

### ⏱️ Downtime máximo permitido por ano
| SLA        | Indisponibilidade anual        |
|------------|--------------------------------|
| **99,9%**  | ~8h 45min 57s                 |
| **99,95%** | ~4h 22min 58s                 |
| **99,99%** | ~52min 35s                    |
| **99,999%**| ~5min 15s                     |

## 💰 Análise de custo-benefício
O dilema é simples: **quanto pagar para reduzir minutos de indisponibilidade?**

- 👨‍💻 Aplicações internas → 99% ou 99,9% podem ser suficientes.  
- 🏦 Sistemas críticos (e-commerce, financeiro, hospitalar) → cada minuto de downtime custa caro, então **redundância compensa** (availability zones, regiões diferentes, failover).  

### 🔍 Estratégia prática
1. **Mapeie o impacto do downtime**: quanto custa 1h fora do ar para o negócio?  
2. **Compare com o custo da redundância** (VM extra, replicação de banco, load balancer).  
3. **Ache o ponto ótimo**: não existe *zero downtime* barato, mas sempre dá para equilibrar custo e disponibilidade.  

--------------------------------------------------------
# 🗄️ Configurando uma Instância de Banco de Dados na Azure

## ⚙️ Criação e configuração
Na Azure, serviços de banco de dados são oferecidos em versões **PaaS** e **IaaS**:

- **IaaS (VM + SQL Server instalado):** mais flexibilidade, mas você gerencia patching, backup e alta disponibilidade.  
- **PaaS (Azure SQL Database, Cosmos DB, PostgreSQL, MySQL, etc.):** gerenciado pela Microsoft, com escalabilidade, backup automático e SLAs mais altos.  

Passos comuns de configuração:
1. **Escolha a região** (latência e conformidade regulatória).  
2. **Defina o tier** (Basic, Standard, Premium, Hyperscale).  
3. **Configure segurança** (firewall rules, autenticação, identidade gerenciada, criptografia em repouso).  
4. **Monitore** com métricas de desempenho, alertas e auditoria de acessos.  

## 📊 SLAs (Service Level Agreements)
Cada serviço tem seu SLA, que varia de acordo com o modelo de implantação e redundância:

- **SQL Server em VM (IaaS):** 99,9% com infraestrutura básica.  
- **Azure SQL Database – Single Instance:** até 99,99%.  
- **Azure SQL Database – com redundância em zonas:** até 99,995%.  
- **Cosmos DB:** 99,999% de disponibilidade globalmente.  

### ⏱️ Downtime máximo permitido por ano
| SLA        | Indisponibilidade anual        |
|------------|--------------------------------|
| **99,9%**  | ~8h 45min 57s                 |
| **99,95%** | ~4h 22min 58s                 |
| **99,99%** | ~52min 35s                    |
| **99,995%**| ~26min 17s                    |
| **99,999%**| ~5min 15s                     |

## 💰 Análise de custo-benefício
O mesmo dilema: **quanto custa o downtime para o negócio?**

- Aplicações de **baixa criticidade** → tiers básicos e sem redundância já atendem.  
- Aplicações de **alta criticidade** (financeiro, saúde, e-commerce) → melhor investir em **geo-replicação, failover groups e redundância em zonas**.  

### 🔍 Estratégia prática
1. **Mapeie requisitos de negócio:** RTO (Recovery Time Objective) e RPO (Recovery Point Objective).  
2. **Compare preços dos tiers** com o custo de uma possível indisponibilidade.  
3. **Implemente segurança e redundância**: backup automático, replicação ativa, failover groups.  
4. **Monitore sempre**: alertas de performance, auditoria de acessos e consumo.  


