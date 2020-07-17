# Criando um salt-formula no SUMA: telegraf-exporter

*Documentação disponível em <a href="https://docs.influxdata.com/telegraf/v1.14/">documentação Telegraf</a>

Esse exemplo utiliza um host conectado no SUSE Manager. A instalação do Prometheus e do Grafana foram feito através do salt, no SUMA. A formula é implementada para ser utilizada com o SUSE Manager para ser aplciado diretamente nos salt-minions através da interface web.
Esse tutorial foi feito para um host Ubuntu, 32bits (i386).

Aplicar passo-a-passo no server SUSE Manager:

# Passo a passo
1. **Download**: No site do <a href="https://portal.influxdata.com/downloads/">Telegraf</a>, procurar pela distribuição do seu SO e baixe: 
```
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/lsb-release
echo "deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
```

2. **Instalação**: 
```
sudo apt-get update && sudo apt-get install telegraf
sudo service telegraf start
```

3. **Configuration**: Criar um arquivo default inicial de configuração
```
telegraf config > telegraf.conf
```

4. **Editar o arquivo config**: Para as métricas serem exportadas para o Prometheus, é necessário descomentar a parte de configuração de output. O arquivo de configuração fica em /etc/telegraf/telegraf.conf
Em <a href="https://github.com/gbrlins/telegraf-exporter-formula/blob/master/telegraf.conf">telegraf.conf</a> possui um exemplo de configurações para teste. (Atentar-se em trocar as variáveis)

