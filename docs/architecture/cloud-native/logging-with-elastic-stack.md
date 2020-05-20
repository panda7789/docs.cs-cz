---
title: Protokolování pomocí řešení Elastic Stack
description: Protokolování pomocí elastického zásobníku, Logstash a Kibana
ms.date: 05/13/2020
ms.openlocfilehash: e886141fa691b75b882b5d67eae4ceb242e8089f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613847"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="b9c76-103">Protokolování pomocí řešení Elastic Stack</span><span class="sxs-lookup"><span data-stu-id="b9c76-103">Logging with Elastic Stack</span></span>

<span data-ttu-id="b9c76-104">Existuje mnoho dobře centralizovaných nástrojů protokolování, které se liší od bezplatného, open-source nástrojů až po dražší možnosti.</span><span class="sxs-lookup"><span data-stu-id="b9c76-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="b9c76-105">V mnoha případech jsou bezplatné nástroje jako dobrá nebo lepší než placené nabídky.</span><span class="sxs-lookup"><span data-stu-id="b9c76-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="b9c76-106">Jedním z těchto nástrojů je kombinace tří open-source komponent: elastické vyhledávání, Logstash a Kibana.</span><span class="sxs-lookup"><span data-stu-id="b9c76-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="b9c76-107">Souhrn těchto nástrojů je známý jako elastický zásobník nebo zásobník ELK.</span><span class="sxs-lookup"><span data-stu-id="b9c76-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="b9c76-108">Elastický zásobník</span><span class="sxs-lookup"><span data-stu-id="b9c76-108">Elastic Stack</span></span>

<span data-ttu-id="b9c76-109">Elastický zásobník je efektivní možností pro shromažďování informací z clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b9c76-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="b9c76-110">Kubernetes podporuje odesílání protokolů do koncového bodu Elasticsearch a ve [většině případů](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)je potřeba začít s nastavením proměnných prostředí, jak je znázorněno na obrázku 7-5:</span><span class="sxs-lookup"><span data-stu-id="b9c76-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="b9c76-111">**Obrázek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="b9c76-111">**Figure 7-5**.</span></span> <span data-ttu-id="b9c76-112">Proměnné konfigurace pro Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b9c76-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="b9c76-113">Tím se do clusteru nainstaluje Elasticsearch a do něj budou odesílány všechny protokoly clusteru.</span><span class="sxs-lookup"><span data-stu-id="b9c76-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="b9c76-114">![Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které se ingestují z Kubernetes ](./media/kibana-dashboard.png)
 **obrázku 7-6**.</span><span class="sxs-lookup"><span data-stu-id="b9c76-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="b9c76-115">Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které jsou ingestované z Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b9c76-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="b9c76-116">Jaké jsou výhody elastického zásobníku?</span><span class="sxs-lookup"><span data-stu-id="b9c76-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="b9c76-117">Elastický zásobník poskytuje centralizované protokolování s nízkými náklady, škálovatelným a uživatelsky přívětivým způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9c76-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="b9c76-118">Jeho uživatelské rozhraní zjednodušuje analýzu dat, takže můžete strávit vaše data získat z vašich dat místo boje proti clunky rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b9c76-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="b9c76-119">Podporuje širokou škálu vstupů, takže vaše distribuovaná aplikace zahrnuje více a různé druhy služeb, můžete očekávat, že budete moci zamezit data protokolů a metrik do systému.</span><span class="sxs-lookup"><span data-stu-id="b9c76-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="b9c76-120">Elastický zásobník podporuje také rychlé vyhledávání i napříč velkými datovými sadami, což umožňuje, aby velké aplikace protokoloval podrobné údaje a pořád je bylo možné vyhlížet způsobem.</span><span class="sxs-lookup"><span data-stu-id="b9c76-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="b9c76-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="b9c76-121">Logstash</span></span>

<span data-ttu-id="b9c76-122">První součást je [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="b9c76-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="b9c76-123">Tento nástroj slouží ke shromažďování informací protokolu z velkého množství různých zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b9c76-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="b9c76-124">Logstash může například číst protokoly z disku a také přijímat zprávy z knihoven protokolování, jako je [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="b9c76-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="b9c76-125">Logstash může v protokolech provést několik základních filtrů a rozšíření při jejich doručování.</span><span class="sxs-lookup"><span data-stu-id="b9c76-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="b9c76-126">Například pokud vaše protokoly obsahují IP adresy, pak Logstash může být nakonfigurován tak, aby provede zeměpisné vyhledávání a získala zemi nebo dokonce město původu této zprávy.</span><span class="sxs-lookup"><span data-stu-id="b9c76-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="b9c76-127">Serilog je knihovna protokolování pro jazyky .NET, která umožňuje parametrizované protokolování.</span><span class="sxs-lookup"><span data-stu-id="b9c76-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="b9c76-128">Namísto generování textové zprávy protokolu, která vkládá pole, jsou parametry oddělené.</span><span class="sxs-lookup"><span data-stu-id="b9c76-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="b9c76-129">To umožňuje více inteligentních filtrování a hledání.</span><span class="sxs-lookup"><span data-stu-id="b9c76-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="b9c76-130">Ukázková konfigurace Serilog pro zápis do Logstash se zobrazí na obrázku 7-7.</span><span class="sxs-lookup"><span data-stu-id="b9c76-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="b9c76-131">**Obrázek 7-7**.</span><span class="sxs-lookup"><span data-stu-id="b9c76-131">**Figure 7-7**.</span></span> <span data-ttu-id="b9c76-132">Serilog config pro zápis informací protokolu přímo do logstash prostřednictvím protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="b9c76-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="b9c76-133">Logstash by používal konfiguraci, která je znázorněna na obrázku 7-8.</span><span class="sxs-lookup"><span data-stu-id="b9c76-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

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

<span data-ttu-id="b9c76-134">**Obrázek 7-8**.</span><span class="sxs-lookup"><span data-stu-id="b9c76-134">**Figure 7-8**.</span></span> <span data-ttu-id="b9c76-135">Konfigurace Logstash pro využívání protokolů z Serilog</span><span class="sxs-lookup"><span data-stu-id="b9c76-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="b9c76-136">V případech, kdy není potřeba rozsáhlá manipulace s protokolem, existuje alternativa k Logstash, která se označuje jako [Beats](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="b9c76-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="b9c76-137">Beats je řada nástrojů, které mohou shromažďovat širokou škálu dat od protokolů až po informace o síti a dobu provozu.</span><span class="sxs-lookup"><span data-stu-id="b9c76-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="b9c76-138">Mnohé aplikace budou používat Logstash i Beats.</span><span class="sxs-lookup"><span data-stu-id="b9c76-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="b9c76-139">Po shromáždění protokolů nástrojem Logstash je potřeba je umístit někam jinam.</span><span class="sxs-lookup"><span data-stu-id="b9c76-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="b9c76-140">I když Logstash podporuje mnoho různých výstupů, je jedním z zajímavých hledání elastické.</span><span class="sxs-lookup"><span data-stu-id="b9c76-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="b9c76-141">Elastické vyhledávání</span><span class="sxs-lookup"><span data-stu-id="b9c76-141">Elastic search</span></span>

<span data-ttu-id="b9c76-142">Elastické vyhledávání je výkonný vyhledávací modul, který umožňuje indexovat protokoly při jejich doručování.</span><span class="sxs-lookup"><span data-stu-id="b9c76-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="b9c76-143">Díky rychlému spouštění dotazů v protokolech.</span><span class="sxs-lookup"><span data-stu-id="b9c76-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="b9c76-144">Elastické vyhledávání může zpracovávat velké množství protokolů a v extrémních případech je možné škálovat napříč mnoha uzly.</span><span class="sxs-lookup"><span data-stu-id="b9c76-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="b9c76-145">Protokolované zprávy, které byly vytvořené tak, aby obsahovaly parametry nebo byly rozděleny pomocí parametrů prostřednictvím zpracování Logstash, se dají dotazovat přímo jako Elasticsearch, které tyto informace zachová.</span><span class="sxs-lookup"><span data-stu-id="b9c76-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="b9c76-146">Dotaz, který vyhledává prvních 10 navštívených stránek `jill@example.com` , se zobrazí na obrázku 7-9.</span><span class="sxs-lookup"><span data-stu-id="b9c76-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```
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

<span data-ttu-id="b9c76-147">**Obrázek 7-9**.</span><span class="sxs-lookup"><span data-stu-id="b9c76-147">**Figure 7-9**.</span></span> <span data-ttu-id="b9c76-148">Dotaz Elasticsearch pro vyhledání prvních 10 stránek navštívených uživatelem</span><span class="sxs-lookup"><span data-stu-id="b9c76-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="b9c76-149">Vizualizace informací pomocí webových řídicích panelů Kibana</span><span class="sxs-lookup"><span data-stu-id="b9c76-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="b9c76-150">Konečná součást zásobníku je Kibana.</span><span class="sxs-lookup"><span data-stu-id="b9c76-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="b9c76-151">Tento nástroj slouží k zajištění interaktivních vizualizací na webovém řídicím panelu.</span><span class="sxs-lookup"><span data-stu-id="b9c76-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="b9c76-152">Řídicí panely můžou být vytvořené i uživateli, kteří nejsou techničtí.</span><span class="sxs-lookup"><span data-stu-id="b9c76-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="b9c76-153">Většina dat, která jsou rezidentem v indexu Elasticsearch, může být součástí řídicích panelů Kibana.</span><span class="sxs-lookup"><span data-stu-id="b9c76-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="b9c76-154">Jednotliví uživatelé mohou mít různé požadované možnosti řídicího panelu a Kibana toto přizpůsobení umožňují prostřednictvím uživatelských řídicích panelů.</span><span class="sxs-lookup"><span data-stu-id="b9c76-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="b9c76-155">Instalace elastického zásobníku v Azure</span><span class="sxs-lookup"><span data-stu-id="b9c76-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="b9c76-156">Elastický zásobník se dá nainstalovat do Azure mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="b9c76-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="b9c76-157">Jako vždy je možné [zřídit virtuální počítače a nainstalovat elastické zásobníky přímo](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="b9c76-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="b9c76-158">Tato možnost je preferována některými zkušenými uživateli, protože nabízí nejvyšší stupeň úprav.</span><span class="sxs-lookup"><span data-stu-id="b9c76-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="b9c76-159">Nasazení na infrastrukturu jako službu přináší významné nároky na správu, které přijímají tuto cestu, aby bylo možné převzít vlastnictví všech úkolů přidružených k infrastruktuře jako služby, jako je například zabezpečení počítačů a udržování aktuálnosti oprav.</span><span class="sxs-lookup"><span data-stu-id="b9c76-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="b9c76-160">Možnost s menší režií je použití jednoho z mnoha kontejnerů Docker, na kterých je elastický zásobník již nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="b9c76-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="b9c76-161">Tyto kontejnery lze přetáhnout do existujícího clusteru Kubernetes a spustit společně s kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9c76-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="b9c76-162">Kontejner [sebp/Elk](https://elk-docker.readthedocs.io/) je dobře dokumentovaný a testovaný kontejner elastického zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b9c76-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="b9c76-163">Další možností je [nedávno ohlášená nabídka Elk jako služba](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="b9c76-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="b9c76-164">Odkazy</span><span class="sxs-lookup"><span data-stu-id="b9c76-164">References</span></span>

- [<span data-ttu-id="b9c76-165">Instalace elastického zásobníku v Azure</span><span class="sxs-lookup"><span data-stu-id="b9c76-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="b9c76-166">[Předchozí](observability-patterns.md) 
> [Další](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="b9c76-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
