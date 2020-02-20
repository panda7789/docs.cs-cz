---
title: Sítě – gRPC pro vývojáře WCF
description: Použití sítě k směrování a vyrovnání požadavků na služby gRPC Services v clusteru Kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503382"
---
# <a name="service-meshes"></a><span data-ttu-id="9b2a7-103">Sítě – sítě</span><span class="sxs-lookup"><span data-stu-id="9b2a7-103">Service meshes</span></span>

<span data-ttu-id="9b2a7-104">Síť je součást infrastruktury, která přebírá řízení žádostí o služby směrování v rámci sítě.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="9b2a7-105">Sítě sítí mohou zpracovávat všechny druhy obav na úrovni sítě v rámci clusteru Kubernetes, včetně těchto:</span><span class="sxs-lookup"><span data-stu-id="9b2a7-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="9b2a7-106">Zjišťování služby</span><span class="sxs-lookup"><span data-stu-id="9b2a7-106">Service discovery</span></span>
- <span data-ttu-id="9b2a7-107">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="9b2a7-107">Load balancing</span></span>
- <span data-ttu-id="9b2a7-108">Odolnost proti chybám</span><span class="sxs-lookup"><span data-stu-id="9b2a7-108">Fault tolerance</span></span>
- <span data-ttu-id="9b2a7-109">Šifrování</span><span class="sxs-lookup"><span data-stu-id="9b2a7-109">Encryption</span></span>
- <span data-ttu-id="9b2a7-110">Monitorování</span><span class="sxs-lookup"><span data-stu-id="9b2a7-110">Monitoring</span></span>

<span data-ttu-id="9b2a7-111">Sítě Kubernetes fungují přidáním dalšího kontejneru, který se označuje jako *proxy vozíku*, do každého pod tím, co je zahrnuto do sítě.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="9b2a7-112">Proxy přebírá všechny příchozí a odchozí síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="9b2a7-113">Pak můžete udržovat konfiguraci a správu otázek sítě odděleně od kontejnerů aplikací.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-113">You can then keep configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="9b2a7-114">V mnoha případech toto oddělení nevyžaduje žádné změny kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="9b2a7-115">V [příkladu předchozí kapitoly](kubernetes.md#test-the-application)byly požadavky gRPC z webové aplikace směrovány do jediné instance služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="9b2a7-116">Důvodem je, že název hostitele služby se přeloží na IP adresu a tato IP adresa se uloží do mezipaměti po dobu života instance `HttpClientHandler`.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="9b2a7-117">Toto řešení může být možné vyřešit ručním zpracováním vyhledávání DNS nebo vytvořením několika klientů.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-117">It might be possible to work around this by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="9b2a7-118">Toto řešení ale může zkomplikovat kód aplikace bez nutnosti přidat jakoukoli firmu nebo zákaznickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="9b2a7-119">Když použijete síť, požadavky z kontejneru aplikace se odešlou na proxy postranní vozík.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="9b2a7-120">Proxy z postranového vozíku je pak může inteligentně rozmístit napříč všemi instancemi jiné služby.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="9b2a7-121">Síť může také:</span><span class="sxs-lookup"><span data-stu-id="9b2a7-121">The mesh can also:</span></span>

- <span data-ttu-id="9b2a7-122">Bez problémů můžete reagovat na selhání jednotlivých instancí služby.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="9b2a7-123">Zpracovat sémantiku opakování pro neúspěšná volání nebo vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="9b2a7-124">Přesměrovat neúspěšné požadavky na alternativní instanci bez návratu do klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="9b2a7-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="9b2a7-125">Následující snímek obrazovky ukazuje aplikaci StockWeb běžící s mřížkou linkeru služby.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="9b2a7-126">V kódu aplikace nejsou žádné změny a image Docker se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="9b2a7-127">Jediná požadovaná změna byla přidání poznámky k nasazení v souborech YAML pro služby `stockdata` a `stockweb`.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![StockWeb s sítí služby](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="9b2a7-129">Můžete vidět ze sloupce **Server** , že požadavky z aplikace StockWeb byly směrovány do obou replik služby StockData, a to i v případě, že pocházejí z jediné instance `HttpClient` v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="9b2a7-130">Pokud zkontrolujete kód, uvidíte, že všechny požadavky 100 na službu StockData se provádějí současně pomocí stejné instance `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="9b2a7-131">S sítí služby budou tyto požadavky vyrovnávány napříč celou řadou instancí služby, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="9b2a7-132">Sítě se vztahují jenom na přenosy v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="9b2a7-133">U externích klientů si přečtěte další kapitolu [Vyrovnávání zatížení](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="9b2a7-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="9b2a7-134">Možnosti sítě</span><span class="sxs-lookup"><span data-stu-id="9b2a7-134">Service mesh options</span></span>

<span data-ttu-id="9b2a7-135">Tři implementace sítě pro obecné účely jsou aktuálně k dispozici pro použití s Kubernetes: [Istio](https://istio.io), [linkerem](https://linkerd.io)a [Consul připojit](https://consul.io/mesh.html).</span><span class="sxs-lookup"><span data-stu-id="9b2a7-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="9b2a7-136">Všechny tři poskytují požadavky na směrování a proxy, šifrování provozu, odolnost, ověřování od hostitele do hostitele a řízení provozu.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="9b2a7-137">Volba sítě služby závisí na několika faktorech:</span><span class="sxs-lookup"><span data-stu-id="9b2a7-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="9b2a7-138">Specifické požadavky organizace na náklady, dodržování předpisů, placené plány podpory atd.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="9b2a7-139">Povaha clusteru, jeho velikost, počet nasazených služeb a objem přenosů v rámci sítě s clustery.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="9b2a7-140">Snadné nasazení a Správa sítě a její použití se službami</span><span class="sxs-lookup"><span data-stu-id="9b2a7-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="9b2a7-141">Příklad: Přidání linkeru do nasazení</span><span class="sxs-lookup"><span data-stu-id="9b2a7-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="9b2a7-142">V tomto příkladu se dozvíte, jak používat síť s propojovacími službami s aplikací *StockKube* z [předchozí části](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="9b2a7-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="9b2a7-143">Chcete-li postupovat podle tohoto příkladu, je nutné [nainstalovat linkered CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="9b2a7-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="9b2a7-144">Binární soubory Windows si můžete stáhnout z části, kde jsou uvedené verze GitHubu.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="9b2a7-145">Ujistěte se, že používáte nejnovější *stabilní* verzi a ne jednu z hraničních vydání.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="9b2a7-146">Po instalaci rozhraní příkazového řádku, postupujte podle pokynů [Začínáme](https://linkerd.io/2/getting-started/index.html) a nainstalujte linkerované komponenty do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="9b2a7-147">Pokyny jsou jednoduché a v místní instanci Kubernetes by instalace měla trvat jenom pár minut.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-147">The instructions are straightforward, and installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="9b2a7-148">Přidat linkery do nasazení Kubernetes</span><span class="sxs-lookup"><span data-stu-id="9b2a7-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="9b2a7-149">Linkerované rozhraní příkazového řádku poskytuje `inject` příkaz pro přidání nezbytných oddílů a vlastností do souborů Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="9b2a7-150">Můžete spustit příkaz a zapsat výstup do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="9b2a7-151">Můžete zkontrolovat nové soubory a zjistit, jaké změny byly provedeny.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="9b2a7-152">Pro objekty nasazení je přidána anotace metadat, která přihlašuje linker pro vložení kontejneru proxy vozíku do objektu pod při jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="9b2a7-153">Je také možné přesměrovat výstup příkazu `linkerd inject` na `kubectl` přímo.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="9b2a7-154">Následující příkazy budou fungovat v PowerShellu nebo v jakémkoli prostředí Linux.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="9b2a7-155">Kontrola služeb v řídicím panelu linkeru</span><span class="sxs-lookup"><span data-stu-id="9b2a7-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="9b2a7-156">Otevřete Linkerový řídicí panel pomocí rozhraní příkazového řádku `linkerd`.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="9b2a7-157">Řídicí panel poskytuje podrobné informace o všech službách, které jsou připojené k síti.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Linkerový řídicí panel zobrazující aplikace StockKube](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="9b2a7-159">Pokud zvýšíte počet replik služby StockData gRPC, jak je znázorněno v následujícím příkladu, a aktualizovat stránku StockWeb v prohlížeči, měla by se zobrazit kombinace identifikátorů ve sloupci **Server** .</span><span class="sxs-lookup"><span data-stu-id="9b2a7-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="9b2a7-160">Tato kombinace znamená, že všechny dostupné instance obsluhují požadavky.</span><span class="sxs-lookup"><span data-stu-id="9b2a7-160">This mix indicates that all the available instances are serving requests.</span></span>

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
><span data-ttu-id="9b2a7-161">[Předchozí](kubernetes.md)
>[Další](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="9b2a7-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
