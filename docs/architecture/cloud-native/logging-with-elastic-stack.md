---
title: Protokolování pomocí řešení Elastic Stack
description: Protokolování pomocí elastického zásobníku, Logstash a Kibana
ms.date: 05/13/2020
ms.openlocfilehash: 32d9d0dae175d8d45d48b56d17f133b4cc432363
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811168"
---
# <a name="logging-with-elastic-stack"></a>Protokolování pomocí řešení Elastic Stack

Existuje mnoho dobře centralizovaných nástrojů protokolování, které se liší od bezplatného, open-source nástrojů až po dražší možnosti. V mnoha případech jsou bezplatné nástroje jako dobrá nebo lepší než placené nabídky. Jedním z těchto nástrojů je kombinace tří open-source komponent: elastické vyhledávání, Logstash a Kibana.

Souhrn těchto nástrojů je známý jako elastický zásobník nebo zásobník ELK.

## <a name="elastic-stack"></a>Elastický zásobník

Elastický zásobník je efektivní možností pro shromažďování informací z clusteru Kubernetes. Kubernetes podporuje odesílání protokolů do koncového bodu Elasticsearch a ve [většině případů](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)je potřeba začít s nastavením proměnných prostředí, jak je znázorněno na obrázku 7-5:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Obrázek 7-5**. Proměnné konfigurace pro Kubernetes

Tím se do clusteru nainstaluje Elasticsearch a do něj budou odesílány všechny protokoly clusteru.

![Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které se ingestují z Kubernetes ](./media/kibana-dashboard.png)
 **obrázku 7-6**. Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které jsou ingestované z Kubernetes

## <a name="what-are-the-advantages-of-elastic-stack"></a>Jaké jsou výhody elastického zásobníku?

Elastický zásobník poskytuje centralizované protokolování s nízkými náklady, škálovatelným a uživatelsky přívětivým způsobem. Jeho uživatelské rozhraní zjednodušuje analýzu dat, takže můžete strávit vaše data získat z vašich dat místo boje proti clunky rozhraní. Podporuje širokou škálu vstupů, takže vaše distribuovaná aplikace zahrnuje více a různé druhy služeb, můžete očekávat, že budete moci zamezit data protokolů a metrik do systému. Elastický zásobník podporuje také rychlé vyhledávání i napříč velkými datovými sadami, což umožňuje, aby velké aplikace protokoloval podrobné údaje a pořád je bylo možné vyhlížet způsobem.

## <a name="logstash"></a>Logstash

První součást je [Logstash](https://www.elastic.co/products/logstash). Tento nástroj slouží ke shromažďování informací protokolu z velkého množství různých zdrojů. Logstash může například číst protokoly z disku a také přijímat zprávy z knihoven protokolování, jako je [Serilog](https://serilog.net/). Logstash může v protokolech provést několik základních filtrů a rozšíření při jejich doručování. Například pokud vaše protokoly obsahují IP adresy, pak Logstash může být nakonfigurován tak, aby provede zeměpisné vyhledávání a získala zemi nebo dokonce město původu této zprávy.

Serilog je knihovna protokolování pro jazyky .NET, která umožňuje parametrizované protokolování. Namísto generování textové zprávy protokolu, která vkládá pole, jsou parametry oddělené. To umožňuje více inteligentních filtrování a hledání. Ukázková konfigurace Serilog pro zápis do Logstash se zobrazí na obrázku 7-7.

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**Obrázek 7-7**. Serilog config pro zápis informací protokolu přímo do logstash prostřednictvím protokolu HTTP

Logstash by používal konfiguraci, která je znázorněna na obrázku 7-8.

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

**Obrázek 7-8**. Konfigurace Logstash pro využívání protokolů z Serilog

V případech, kdy není potřeba rozsáhlá manipulace s protokolem, existuje alternativa k Logstash, která se označuje jako [Beats](https://www.elastic.co/products/beats). Beats je řada nástrojů, které mohou shromažďovat širokou škálu dat od protokolů až po informace o síti a dobu provozu. Mnohé aplikace budou používat Logstash i Beats.

Po shromáždění protokolů nástrojem Logstash je potřeba je umístit někam jinam. I když Logstash podporuje mnoho různých výstupů, je jedním z zajímavých hledání elastické.

## <a name="elastic-search"></a>Elastické vyhledávání

Elastické vyhledávání je výkonný vyhledávací modul, který umožňuje indexovat protokoly při jejich doručování. Díky rychlému spouštění dotazů v protokolech. Elastické vyhledávání může zpracovávat velké množství protokolů a v extrémních případech je možné škálovat napříč mnoha uzly.

Protokolované zprávy, které byly vytvořené tak, aby obsahovaly parametry nebo byly rozděleny pomocí parametrů prostřednictvím zpracování Logstash, se dají dotazovat přímo jako Elasticsearch, které tyto informace zachová.

Dotaz, který vyhledává prvních 10 navštívených stránek `jill@example.com` , se zobrazí na obrázku 7-9.

```json
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

**Obrázek 7-9**. Dotaz Elasticsearch pro vyhledání prvních 10 stránek navštívených uživatelem

## <a name="visualizing-information-with-kibana-web-dashboards"></a>Vizualizace informací pomocí webových řídicích panelů Kibana

Konečná součást zásobníku je Kibana. Tento nástroj slouží k zajištění interaktivních vizualizací na webovém řídicím panelu. Řídicí panely můžou být vytvořené i uživateli, kteří nejsou techničtí. Většina dat, která jsou rezidentem v indexu Elasticsearch, může být součástí řídicích panelů Kibana. Jednotliví uživatelé mohou mít různé požadované možnosti řídicího panelu a Kibana toto přizpůsobení umožňují prostřednictvím uživatelských řídicích panelů.

## <a name="installing-elastic-stack-on-azure"></a>Instalace elastického zásobníku v Azure

Elastický zásobník se dá nainstalovat do Azure mnoha různými způsoby. Jako vždy je možné [zřídit virtuální počítače a nainstalovat elastické zásobníky přímo](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch). Tato možnost je preferována některými zkušenými uživateli, protože nabízí nejvyšší stupeň úprav. Nasazení na infrastrukturu jako službu přináší významné nároky na správu, které přijímají tuto cestu, aby bylo možné převzít vlastnictví všech úkolů přidružených k infrastruktuře jako služby, jako je například zabezpečení počítačů a udržování aktuálnosti oprav.

Možnost s menší režií je použití jednoho z mnoha kontejnerů Docker, na kterých je elastický zásobník již nakonfigurován. Tyto kontejnery lze přetáhnout do existujícího clusteru Kubernetes a spustit společně s kódem aplikace. Kontejner [sebp/Elk](https://elk-docker.readthedocs.io/) je dobře dokumentovaný a testovaný kontejner elastického zásobníku.

Další možností je [nedávno ohlášená nabídka Elk jako služba](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).

## <a name="references"></a>Reference

- [Instalace elastického zásobníku v Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[Předchozí](observability-patterns.md) 
> [Další](monitoring-azure-kubernetes.md)
