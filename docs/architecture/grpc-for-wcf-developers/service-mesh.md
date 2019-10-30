---
title: Sítě – gRPC pro vývojáře WCF
description: Použití sítě k směrování a vyrovnání požadavků na služby gRPC Services v clusteru Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6bdfa57ba47ba0105092d1c140705599b7023c78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090177"
---
# <a name="service-meshes"></a><span data-ttu-id="a5638-103">Sítě – sítě</span><span class="sxs-lookup"><span data-stu-id="a5638-103">Service meshes</span></span>

<span data-ttu-id="a5638-104">Síť je součást infrastruktury, která přebírá řízení žádostí o služby směrování v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="a5638-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="a5638-105">Sítě sítí mohou zpracovávat všechny druhy obav na úrovni sítě v rámci clusteru Kubernetes, včetně těchto:</span><span class="sxs-lookup"><span data-stu-id="a5638-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="a5638-106">Zjišťování služby</span><span class="sxs-lookup"><span data-stu-id="a5638-106">Service discovery</span></span>
- <span data-ttu-id="a5638-107">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="a5638-107">Load balancing</span></span>
- <span data-ttu-id="a5638-108">Odolnost proti chybám</span><span class="sxs-lookup"><span data-stu-id="a5638-108">Fault tolerance</span></span>
- <span data-ttu-id="a5638-109">Šifr</span><span class="sxs-lookup"><span data-stu-id="a5638-109">Encryption</span></span>
- <span data-ttu-id="a5638-110">Sledovaný</span><span class="sxs-lookup"><span data-stu-id="a5638-110">Monitoring</span></span>

<span data-ttu-id="a5638-111">Sítě Kubernetes fungují přidáním dalšího kontejneru, který se označuje jako *proxy vozíku*, do každého pod tím, co je zahrnuto do sítě.</span><span class="sxs-lookup"><span data-stu-id="a5638-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="a5638-112">Proxy přebírá všechny příchozí a odchozí síťové požadavky, což umožňuje, aby konfigurace a Správa síťových aspektů byly oddělené od kontejnerů aplikací a v mnoha případech bez nutnosti provádět změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5638-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="a5638-113">Proveďte [příklad předchozí kapitoly](kubernetes.md#testing-the-application), ve kterém byly všechny požadavky gRPC z webové aplikace směrovány do jediné instance služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="a5638-113">Take the [previous chapter's example](kubernetes.md#testing-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="a5638-114">Důvodem je, že název hostitele služby se přeloží na IP adresu a tato IP adresa se uloží do mezipaměti po dobu života instance `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="a5638-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="a5638-115">Můžete to vyřešit tak, že ručně vyřešíte vyhledávání DNS nebo vytváříte více klientů, ale tím se kód aplikace významně nemění bez nutnosti přidat jakoukoli firmu nebo hodnotu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="a5638-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="a5638-116">Pomocí sítě služby se požadavky z kontejneru aplikace odesílají na proxy vozík, který je může rozmístit inteligentně napříč všemi instancemi jiné služby.</span><span class="sxs-lookup"><span data-stu-id="a5638-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="a5638-117">Síť může také:</span><span class="sxs-lookup"><span data-stu-id="a5638-117">The mesh can also:</span></span>

- <span data-ttu-id="a5638-118">Bez problémů můžete reagovat na selhání jednotlivých instancí služby.</span><span class="sxs-lookup"><span data-stu-id="a5638-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="a5638-119">Zpracovat sémantiku opakování pro neúspěšná volání nebo vypršení časových limitů</span><span class="sxs-lookup"><span data-stu-id="a5638-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="a5638-120">Přesměrovat neúspěšné požadavky na alternativní instanci bez návratu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5638-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="a5638-121">Na následujícím snímku obrazovky se zobrazuje aplikace StockWeb běžící s mřížkou linkeru služby bez jakýchkoli změn v kódu aplikace nebo i v případě, že se používá Image Docker.</span><span class="sxs-lookup"><span data-stu-id="a5638-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="a5638-122">Jediná požadovaná změna byla přidání poznámky k nasazení v souborech YAML pro služby `stockdata` a `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="a5638-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb s sítí služby](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="a5638-124">Můžete vidět ze sloupce Server, že požadavky z aplikace StockWeb byly směrovány do obou replik služby StockData, a to i v případě, že pocházejí z jediné instance `HttpClient` v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5638-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="a5638-125">Pokud zkontrolujete kód, uvidíte, že všechny požadavky 100 na službu StockData se současně používají stejnou instanci `HttpClient`, ale i s sítí služby, tyto požadavky budou vyvážené i v případě, že jsou dostupné spousty instancí služby.</span><span class="sxs-lookup"><span data-stu-id="a5638-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="a5638-126">Sítě se vztahují jenom na přenosy v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="a5638-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="a5638-127">U externích klientů si přečtěte [další kapitolu vyrovnávání zatížení](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="a5638-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="a5638-128">Možnosti sítě</span><span class="sxs-lookup"><span data-stu-id="a5638-128">Service mesh options</span></span>

<span data-ttu-id="a5638-129">Existují tři implementace sítě pro obecné účely, které jsou aktuálně k dispozici pro použití s Kubernetes: Istio, linkerem a Consul Connect.</span><span class="sxs-lookup"><span data-stu-id="a5638-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="a5638-130">Všechny tři poskytují požadavky na směrování a proxy, šifrování provozu, odolnost, ověřování od hostitele do hostitele a řízení provozu.</span><span class="sxs-lookup"><span data-stu-id="a5638-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="a5638-131">Volba sítě služby závisí na několika faktorech:</span><span class="sxs-lookup"><span data-stu-id="a5638-131">Choosing a service mesh depends multiple factors:</span></span>

- <span data-ttu-id="a5638-132">Specifické požadavky organizace na náklady, dodržování předpisů, placené plány podpory atd.</span><span class="sxs-lookup"><span data-stu-id="a5638-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="a5638-133">Povaha clusteru, jeho velikost, počet nasazených služeb a objem přenosů v rámci sítě s clustery.</span><span class="sxs-lookup"><span data-stu-id="a5638-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="a5638-134">Snadné nasazení a Správa sítě a její použití se službami</span><span class="sxs-lookup"><span data-stu-id="a5638-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="a5638-135">Další informace o každé síti služby jsou k dispozici na příslušných webech.</span><span class="sxs-lookup"><span data-stu-id="a5638-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="a5638-136">**Istio** – istio.IO</span><span class="sxs-lookup"><span data-stu-id="a5638-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="a5638-137">**Linkered** – linkerd.IO</span><span class="sxs-lookup"><span data-stu-id="a5638-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="a5638-138">**Consul** – Consul.IO/Mesh.html</span><span class="sxs-lookup"><span data-stu-id="a5638-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="a5638-139">Příklad: Přidání linkeru do nasazení</span><span class="sxs-lookup"><span data-stu-id="a5638-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="a5638-140">V tomto příkladu se dozvíte, jak používat síť s propojovacími službami s aplikací *StockKube* z [předchozí části](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="a5638-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="a5638-141">Chcete-li postupovat podle tohoto příkladu, je nutné [nainstalovat linkered CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="a5638-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="a5638-142">Binární soubory Windows se dají stáhnout z oddílu verze GitHubu. Ujistěte se, že používáte nejnovější **stabilní** verzi a ne jednu z hraničních vydání.</span><span class="sxs-lookup"><span data-stu-id="a5638-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="a5638-143">Po nainstalování linkeru rozhraní příkazového řádku, postupujte podle pokynů [*Začínáme* na linkeru webu] a nainstalujte linkerované komponenty do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a5638-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="a5638-144">Pokyny jsou přímo předávány a instalace by v místní instanci Kubernetes měla trvat několik minut.</span><span class="sxs-lookup"><span data-stu-id="a5638-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="a5638-145">Přidat linkery do nasazení Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a5638-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="a5638-146">Linkerované rozhraní příkazového řádku poskytuje `inject` příkaz pro přidání nezbytných oddílů a vlastností do souborů Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a5638-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="a5638-147">Můžete spustit příkaz a zapsat výstup do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="a5638-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="a5638-148">Můžete zkontrolovat nové soubory a zjistit, jaké změny byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="a5638-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="a5638-149">Pro objekty nasazení je přidána anotace metadat, která přihlašuje linker pro vložení kontejneru proxy vozíku do objektu pod při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a5638-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="a5638-150">Je také možné přesměrovat výstup příkazu `linkerd inject` na `kubectl` přímo.</span><span class="sxs-lookup"><span data-stu-id="a5638-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="a5638-151">Následující příkazy budou fungovat v PowerShellu nebo v jakémkoli prostředí Linux.</span><span class="sxs-lookup"><span data-stu-id="a5638-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="a5638-152">Kontrola služeb v řídicím panelu linkeru</span><span class="sxs-lookup"><span data-stu-id="a5638-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="a5638-153">Spusťte Linkerový řídicí panel pomocí rozhraní příkazového řádku `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="a5638-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="a5638-154">Řídicí panel poskytuje podrobné informace o všech službách, které jsou připojené k síti.</span><span class="sxs-lookup"><span data-stu-id="a5638-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Linkerový řídicí panel zobrazující aplikace StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="a5638-156">Pokud zvýšíte počet replik služby StockData gRPC, jak je znázorněno v následujícím příkladu, a aktualizovat stránku StockWeb v prohlížeči, měla by se zobrazit kombinace identifikátorů ve sloupci Server, což značí, že požadavky jsou obsluhovány všemi dostupnými instancemi. .</span><span class="sxs-lookup"><span data-stu-id="a5638-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

>[!div class="step-by-step"]
><span data-ttu-id="a5638-157">[Předchozí](kubernetes.md)
>[Další](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="a5638-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
