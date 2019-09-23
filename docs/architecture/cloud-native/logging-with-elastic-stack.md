---
title: Protokolování pomocí elastického zásobníku
description: Protokolování pomocí elastického zásobníku, Logstash a Kibana
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182830"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="3fa95-103">Protokolování pomocí elastického zásobníku</span><span class="sxs-lookup"><span data-stu-id="3fa95-103">Logging with Elastic Stack</span></span> 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3fa95-104">Existuje mnoho dobře centralizovaných nástrojů protokolování, které se liší od bezplatného, open-source nástrojů až po dražší možnosti.</span><span class="sxs-lookup"><span data-stu-id="3fa95-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="3fa95-105">V mnoha případech jsou bezplatné nástroje jako dobrá nebo lepší než placené nabídky.</span><span class="sxs-lookup"><span data-stu-id="3fa95-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="3fa95-106">Jedním z těchto nástrojů je kombinace tří open-source komponent: Elastické vyhledávání, Logstash a Kibana.</span><span class="sxs-lookup"><span data-stu-id="3fa95-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span> <span data-ttu-id="3fa95-107">Souhrn těchto nástrojů je známý jako elastický zásobník nebo zásobník ELK.</span><span class="sxs-lookup"><span data-stu-id="3fa95-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="3fa95-108">Jaké jsou výhody elastického zásobníku?</span><span class="sxs-lookup"><span data-stu-id="3fa95-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="3fa95-109">Elastický zásobník poskytuje centralizované protokolování s nízkými náklady, škálovatelným a uživatelsky přívětivým způsobem.</span><span class="sxs-lookup"><span data-stu-id="3fa95-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="3fa95-110">Jeho uživatelské rozhraní zjednodušuje analýzu dat, takže můžete strávit vaše data získat z vašich dat místo boje proti clunky rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3fa95-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="3fa95-111">Podporuje širokou škálu vstupů, takže vaše distribuovaná aplikace zahrnuje více a různé druhy služeb, můžete očekávat, že budete moci zamezit data protokolů a metrik do systému.</span><span class="sxs-lookup"><span data-stu-id="3fa95-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="3fa95-112">Elastický zásobník také podporuje rychlé vyhledávání i napříč velkými datovými sadami, což umožňuje, aby i velké aplikace mohly protokolovat podrobná data a pořád je mohli mít v takovém důsledku lepší viditelnost.</span><span class="sxs-lookup"><span data-stu-id="3fa95-112">The Elastic Stack also supports fast searches even across large data sets, making it possible to for even large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="3fa95-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="3fa95-113">Logstash</span></span>

<span data-ttu-id="3fa95-114">První součást je [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="3fa95-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="3fa95-115">Tento nástroj slouží ke shromažďování informací protokolu z velkého množství různých zdrojů.</span><span class="sxs-lookup"><span data-stu-id="3fa95-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="3fa95-116">Logstash může například číst protokoly z disku a také přijímat zprávy z knihoven protokolování, jako je [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="3fa95-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="3fa95-117">Logstash může v protokolech provést několik základních filtrů a rozšíření při jejich doručování.</span><span class="sxs-lookup"><span data-stu-id="3fa95-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="3fa95-118">Například pokud vaše protokoly obsahují IP adresy, pak Logstash může být nakonfigurován tak, aby provede zeměpisné vyhledávání a získala zemi nebo dokonce město původu této zprávy.</span><span class="sxs-lookup"><span data-stu-id="3fa95-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span> 

<span data-ttu-id="3fa95-119">Serilog je knihovna protokolování pro jazyky .NET, která umožňuje parametrizované protokolování.</span><span class="sxs-lookup"><span data-stu-id="3fa95-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="3fa95-120">Namísto generování textové zprávy protokolu, která vkládá pole, jsou parametry oddělené.</span><span class="sxs-lookup"><span data-stu-id="3fa95-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="3fa95-121">To umožňuje více inteligentních filtrování a hledání.</span><span class="sxs-lookup"><span data-stu-id="3fa95-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="3fa95-122">Ukázková konfigurace Serilog pro zápis do Logstash se zobrazí na obrázku 7-2.</span><span class="sxs-lookup"><span data-stu-id="3fa95-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="3fa95-123">**Obrázek 7-2** Serilog config pro zápis informací protokolu přímo do logstash prostřednictvím protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="3fa95-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="3fa95-124">Logstash by používal konfiguraci, která je znázorněna na obrázku 7-3.</span><span class="sxs-lookup"><span data-stu-id="3fa95-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span> 

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

<span data-ttu-id="3fa95-125">**Obrázek 7-3** – konfigurace Logstash pro využívání protokolů z Serilog</span><span class="sxs-lookup"><span data-stu-id="3fa95-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="3fa95-126">V případech, kdy není potřeba rozsáhlá manipulace s protokolem, existuje alternativa k Logstash, která se označuje jako [Beats](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="3fa95-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="3fa95-127">Beats je řada nástrojů, které mohou shromažďovat širokou škálu dat od protokolů až po informace o síti a dobu provozu.</span><span class="sxs-lookup"><span data-stu-id="3fa95-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="3fa95-128">Mnohé aplikace budou používat Logstash i Beats.</span><span class="sxs-lookup"><span data-stu-id="3fa95-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="3fa95-129">Po shromáždění protokolů nástrojem Logstash je potřeba je umístit někam jinam.</span><span class="sxs-lookup"><span data-stu-id="3fa95-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="3fa95-130">I když Logstash podporuje mnoho různých výstupů, je jedním z zajímavých hledání elastické.</span><span class="sxs-lookup"><span data-stu-id="3fa95-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="3fa95-131">Elastické hledání</span><span class="sxs-lookup"><span data-stu-id="3fa95-131">Elastic search</span></span>

<span data-ttu-id="3fa95-132">Elastické vyhledávání je výkonný vyhledávací modul, který umožňuje indexovat protokoly při jejich doručování.</span><span class="sxs-lookup"><span data-stu-id="3fa95-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="3fa95-133">Díky rychlému spouštění dotazů v protokolech.</span><span class="sxs-lookup"><span data-stu-id="3fa95-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="3fa95-134">Elastické vyhledávání může zpracovávat velké množství protokolů a v extrémních případech je možné škálovat napříč mnoha uzly.</span><span class="sxs-lookup"><span data-stu-id="3fa95-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span> 

<span data-ttu-id="3fa95-135">Protokolované zprávy, které byly vytvořené tak, aby obsahovaly parametry nebo byly rozděleny pomocí parametrů prostřednictvím zpracování Logstash, se dají dotazovat přímo jako Elasticsearch, které tyto informace zachová.</span><span class="sxs-lookup"><span data-stu-id="3fa95-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="3fa95-136">Dotaz, který vyhledává prvních 10 navštívených `jill@example.com`stránek, se zobrazí na obrázku 7-4.</span><span class="sxs-lookup"><span data-stu-id="3fa95-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

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

<span data-ttu-id="3fa95-137">**Obrázek 7-4** – dotaz Elasticsearch pro vyhledání prvních 10 stránek navštívených uživatelem</span><span class="sxs-lookup"><span data-stu-id="3fa95-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="3fa95-138">Vizualizace informací pomocí webových řídicích panelů Kibana</span><span class="sxs-lookup"><span data-stu-id="3fa95-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="3fa95-139">Konečná součást zásobníku je Kibana.</span><span class="sxs-lookup"><span data-stu-id="3fa95-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="3fa95-140">Tento nástroj slouží k zajištění interaktivních vizualizací na webovém řídicím panelu.</span><span class="sxs-lookup"><span data-stu-id="3fa95-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="3fa95-141">Řídicí panely můžou být vytvořené i uživateli, kteří nejsou techničtí.</span><span class="sxs-lookup"><span data-stu-id="3fa95-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="3fa95-142">Většina dat, která jsou rezidentem v indexu Elasticsearch, může být součástí řídicích panelů Kibana.</span><span class="sxs-lookup"><span data-stu-id="3fa95-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="3fa95-143">Jednotliví uživatelé mohou mít různé požadované možnosti řídicího panelu a Kibana toto přizpůsobení umožňují prostřednictvím uživatelských řídicích panelů.</span><span class="sxs-lookup"><span data-stu-id="3fa95-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span> 

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="3fa95-144">Instalace elastického zásobníku v Azure</span><span class="sxs-lookup"><span data-stu-id="3fa95-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="3fa95-145">Elastický zásobník se dá nainstalovat do Azure mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="3fa95-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="3fa95-146">Jako vždy je možné [zřídit virtuální počítače a nainstalovat elastické zásobníky přímo](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="3fa95-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="3fa95-147">Tato možnost je preferována některými zkušenými uživateli, protože nabízí nejvyšší stupeň úprav.</span><span class="sxs-lookup"><span data-stu-id="3fa95-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="3fa95-148">Nasazení na infrastrukturu jako službu přináší významné nároky na správu, které přijímají tuto cestu, aby bylo možné převzít vlastnictví všech úkolů přidružených k infrastruktuře jako služby, jako je například zabezpečení počítačů a udržování aktuálnosti oprav.</span><span class="sxs-lookup"><span data-stu-id="3fa95-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span> 

<span data-ttu-id="3fa95-149">Možnost s menší režií je použití jednoho z mnoha kontejnerů Docker, na kterých je elastický zásobník již nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="3fa95-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="3fa95-150">Tyto kontejnery lze přetáhnout do existujícího clusteru Kubernetes a spustit společně s kódem aplikace.</span><span class="sxs-lookup"><span data-stu-id="3fa95-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="3fa95-151">Kontejner [sebp/Elk](https://elk-docker.readthedocs.io/) je dobře dokumentovaný a testovaný kontejner elastického zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3fa95-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="3fa95-152">Další možností je [nedávno ohlášená nabídka Elk jako služba](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="3fa95-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="3fa95-153">Odkazy</span><span class="sxs-lookup"><span data-stu-id="3fa95-153">References</span></span>

- [<span data-ttu-id="3fa95-154">Instalace elastického zásobníku v Azure</span><span class="sxs-lookup"><span data-stu-id="3fa95-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="3fa95-155">[Předchozí](observability-patterns.md)
>[Další](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="3fa95-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
