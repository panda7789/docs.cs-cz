---
title: Kubernetes-gRPC pro vývojáře WCF
description: Spuštění ASP.NET Core gRPC Services v clusteru Kubernetes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 8a04e59bb23b802af6907a369e2c278f64f3fa9d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770503"
---
# <a name="kubernetes"></a><span data-ttu-id="7a7d3-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7a7d3-103">Kubernetes</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7a7d3-104">Přestože je možné ručně spustit kontejnery na hostitelích Docker, pro spolehlivé provozní systémy je vhodnější použít modul orchestrace kontejnerů ke správě více instancí spuštěných v několika serverech v clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's preferable to use a Container Orchestration Engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="7a7d3-105">K dispozici jsou různé moduly pro orchestraci kontejnerů, včetně Kubernetes, Docker Swarm a Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-105">There are various Container Orchestration Engines available, including Kubernetes, Docker Swarm and Apache Mesos.</span></span> <span data-ttu-id="7a7d3-106">V těchto modulech ale Kubernetes je daleko a nejvíce využíváno, takže bude tato kapitola zaměřena.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="7a7d3-107">Kubernetes obsahuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="7a7d3-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="7a7d3-108">**Plánování** spouští kontejnery na více uzlech v rámci clusteru, což zajišťuje vyvážené využití dostupného prostředku, udržování kontejnerů běžících v případě výpadků a zpracování kumulativních aktualizací pro nové verze imagí nebo nové konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="7a7d3-109">**Kontroly stavu** monitorují kontejnery, aby bylo zajištěno pokračování služby.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="7a7d3-110">**Služba DNS & Service Discovery** zpracovává směrování mezi službami v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="7a7d3-111">Příchozí **zpřístupňuje** vybrané služby externě a obecně poskytuje vyrovnávání zatížení napříč instancemi těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-111">**Ingress** exposes selected services externally, and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="7a7d3-112">**Správa prostředků** připojuje externí prostředky, jako je třeba úložiště, do kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-112">**Resource management** attaches external resources such as storage to containers.</span></span>

<span data-ttu-id="7a7d3-113">Tato kapitola podrobně popisuje, jak nasadit službu ASP.NET Core gRPC a webovou stránku, která tuto službu spotřebovává do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="7a7d3-114">Použitá ukázková aplikace je k dispozici v úložišti [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-114">The sample application used is available from on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub,</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="7a7d3-115">Terminologie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7a7d3-115">Kubernetes terminology</span></span>

<span data-ttu-id="7a7d3-116">Kubernetes používá *konfiguraci požadovaného stavu*: rozhraní API se používá k popisu objektů, jako jsou *lusky*, *nasazení* a *služby*, a *Řídicí rovina* se stará o implementaci požadovaného stavu napříč všemi *uzly.* v *clusteru*.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-116">Kubernetes uses *desired state configuration*: the API is used to describe objects such as *Pods*, *Deployments* and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="7a7d3-117">Cluster Kubernetes má *Hlavní* uzel, který spouští *rozhraní Kubernetes API*, které se dá komunikovat prostřednictvím kódu programu nebo pomocí nástroje `kubectl`ho příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which can be communicated with programmatically or using the `kubectl` command-line tool.</span></span> <span data-ttu-id="7a7d3-118">`kubectl` může vytvářet a spravovat objekty pomocí argumentů příkazového řádku, ale nejlépe funguje s YAML soubory, které obsahují data deklarace pro objekty Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-118">`kubectl` can create and manage objects using command-line arguments, but works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="7a7d3-119">Soubory Kubernetes YAML</span><span class="sxs-lookup"><span data-stu-id="7a7d3-119">Kubernetes YAML files</span></span>

<span data-ttu-id="7a7d3-120">Každý soubor Kubernetes YAML bude mít alespoň tři vlastnosti nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-120">Every Kubernetes YAML file will have at least three top-level properties.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="7a7d3-121">Vlastnost `apiVersion` slouží k určení verze (a rozhraní API), pro který je soubor určen.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="7a7d3-122">Vlastnost `kind` určuje druh objektu, který představuje YAML.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="7a7d3-123">Vlastnost `metadata` obsahuje vlastnosti objektu, například `name`, `namespace` nebo `labels`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-123">The `metadata` property contains object properties such as `name`, `namespace`, or `labels`.</span></span>

<span data-ttu-id="7a7d3-124">Většina souborů YAML Kubernetes bude také obsahovat oddíl `spec`, který popisuje prostředky a konfiguraci potřebné k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="7a7d3-125">Podů</span><span class="sxs-lookup"><span data-stu-id="7a7d3-125">Pods</span></span>

<span data-ttu-id="7a7d3-126">Lusky jsou základními jednotkami spuštění v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="7a7d3-127">Můžou spouštět více kontejnerů, ale také se používají ke spouštění jednoduchých kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-127">They can run multiple containers, but are also used to run single containers.</span></span> <span data-ttu-id="7a7d3-128">Pod ní také najdete všechny prostředky úložiště, které jsou požadovány kontejnery, a síťovou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-128">The pod also includes any storage resources required by the container(s), and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="7a7d3-129">Služby</span><span class="sxs-lookup"><span data-stu-id="7a7d3-129">Services</span></span>

<span data-ttu-id="7a7d3-130">Služby jsou meta objekty, které popisují lusky (nebo sady lusků) a poskytují způsob, jak k nim přistupovat v rámci clusteru, jako je například mapování názvu služby na skupinu pod IP adresou pomocí služby DNS clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-130">Services are meta-objects that describe pods (or sets of pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="7a7d3-131">Nasazení</span><span class="sxs-lookup"><span data-stu-id="7a7d3-131">Deployments</span></span>

<span data-ttu-id="7a7d3-132">Nasazení jsou *popsány stavové* objekty pro lusky.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-132">Deployments are the *described state* objects for Pods.</span></span> <span data-ttu-id="7a7d3-133">Pokud vytvoříte v případě ručně, při jeho ukončení se nerestartuje.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-133">If you create a Pod manually, when it terminates it won't be restarted.</span></span> <span data-ttu-id="7a7d3-134">Nasazení se používají k tomu, aby cluster informoval a kolik replik v těchto luskech měl běžet v současné době.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-134">Deployments are used to tell the cluster which pods, and how many replicas of those pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="7a7d3-135">Další objekty</span><span class="sxs-lookup"><span data-stu-id="7a7d3-135">Other objects</span></span>

<span data-ttu-id="7a7d3-136">Lusky, služby a nasazení představují jenom tři základní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="7a7d3-137">Existují spousty dalších typů objektů, které jsou spravovány clusterem Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-137">There are dozens of other types of object that are managed by a Kubernetes cluster.</span></span> <span data-ttu-id="7a7d3-138">Další informace najdete v dokumentaci k [konceptům Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="7a7d3-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="7a7d3-139">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="7a7d3-139">Namespaces</span></span>

<span data-ttu-id="7a7d3-140">Clustery Kubernetes jsou navržené tak, aby se škálovat na stovky nebo tisíce uzlů a spouštěly podobné počty služeb.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes, and run similar numbers of services.</span></span> <span data-ttu-id="7a7d3-141">Aby nedocházelo ke konfliktům mezi názvy objektů, používají se obory názvů k seskupení objektů dohromady jako součást větších aplikací.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="7a7d3-142">Vlastní služby Kubernetes běží v oboru názvů `default`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-142">Kubernetes own services run in a `default` namespace.</span></span> <span data-ttu-id="7a7d3-143">Všechny uživatelské objekty by měly být vytvořeny ve vlastních oborech názvů, aby se předešlo potenciálním konfliktům s výchozími objekty nebo jinými klienty v clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="7a7d3-144">Začínáme s Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7a7d3-144">Get started with Kubernetes</span></span>

<span data-ttu-id="7a7d3-145">Pokud používáte Docker Desktop pro Windows nebo macOS, je Kubernetes již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-145">If you're running Docker Desktop for Windows or macOS, Kubernetes is already available.</span></span> <span data-ttu-id="7a7d3-146">Stačí ho povolit v části Kubernetes okna nastavení.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-146">Just enable it in the Kubernetes section of the Settings window.</span></span>

![Povolit Kubernetes v Docker desktopu](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="7a7d3-148">Chcete-li spustit místní cluster Kubernetes v systému Linux, podívejte se na [minikube](https://github.com/kubernetes/minikube), nebo [MicroK8s](https://microk8s.io/) , pokud je vaše distribuce systému Linux podporována [přichycení](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="7a7d3-148">To run a local Kubernetes cluster in Linux, look at [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="7a7d3-149">Chcete-li ověřit, zda je cluster spuštěný a přístupný, spusťte příkaz `kubectl version`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-149">To check that your cluster is running and accessible, run the `kubectl version` command.</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="7a7d3-150">V tomto příkladu jsou spuštěny `kubectl` CLI a server Kubernetes verze 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="7a7d3-151">Každá verze `kubectl` má podporovat předchozí a další verzi serveru, proto by `kubectl` 1,14 měla fungovat i na serverech verze 1,13 a 1,15.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="7a7d3-152">Spuštění služeb na Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7a7d3-152">Run services on Kubernetes</span></span>

<span data-ttu-id="7a7d3-153">Ukázková aplikace má `kube` adresář obsahující tři soubory YAML.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-153">The sample application has a `kube` directory containing three YAML files.</span></span> <span data-ttu-id="7a7d3-154">@No__t_0 soubor deklaruje vlastní obor názvů `stocks`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-154">The `namespace.yml` file declares a custom namespace, `stocks`.</span></span> <span data-ttu-id="7a7d3-155">@No__t_0 soubor deklaruje nasazení a službu pro aplikaci gRPC a soubor `stockweb.yml` deklaruje nasazení a službu pro webovou aplikaci ASP.NET Core 3,0 MVC, která využívá službu gRPC.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="7a7d3-156">Chcete-li použít soubor `YAML` s `kubectl`, použijte příkaz `apply -f`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-156">To use a `YAML` file with `kubectl`, use the `apply -f` command.</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="7a7d3-157">Příkaz `apply` zkontroluje platnost souboru YAML a zobrazí všechny chyby přijaté z rozhraní API, ale nečeká na vytvoření všech objektů deklarovaných v souboru, protože to může nějakou dobu trvat.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created as this can take some time.</span></span> <span data-ttu-id="7a7d3-158">Pomocí příkazu `kubectl get` s příslušnými typy objektů ověřte vytvoření objektu v clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="7a7d3-159">Deklarace oboru názvů</span><span class="sxs-lookup"><span data-stu-id="7a7d3-159">The namespace declaration</span></span>

<span data-ttu-id="7a7d3-160">Deklarace oboru názvů je jednoduchá a vyžaduje pouze přiřazení `name`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-160">Namespace declaration is simple and requires only assigning a `name`.</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="7a7d3-161">Pomocí `kubectl` použijte soubor `namespace.yml` a ověřte, jestli je obor názvů úspěšně vytvořený.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-161">Use `kubectl` to apply the `namespace.yml` file and check the namespace is created successfully.</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="7a7d3-162">Aplikace StockData</span><span class="sxs-lookup"><span data-stu-id="7a7d3-162">The StockData application</span></span>

<span data-ttu-id="7a7d3-163">@No__t_0 soubor deklaruje dva objekty: nasazení a službu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="7a7d3-164">Nasazení StockData</span><span class="sxs-lookup"><span data-stu-id="7a7d3-164">The StockData Deployment</span></span>

<span data-ttu-id="7a7d3-165">Část nasazení poskytuje `spec` samotného nasazení, včetně počtu požadovaných replik a `template` objektů pod, které se mají vytvořit a spravovat nasazením.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-165">The Deployment part provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="7a7d3-166">Všimněte si, že objekty nasazení jsou spravovány pomocí rozhraní `apps` API, jak je uvedeno v `apiVersion` a nikoli v hlavním rozhraní Kubernetes API.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-166">Note that Deployment objects are managed with the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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
  replicas: 1
  template:
    metadata:
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

<span data-ttu-id="7a7d3-167">Vlastnost `spec.selector` se používá ke spárování spuštěných lusků s nasazením.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="7a7d3-168">Vlastnost `metadata.labels` pod musí odpovídat vlastnosti `matchLabels` nebo volání rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="7a7d3-169">Oddíl `template.spec` deklaruje kontejner, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="7a7d3-170">Při práci s místním clusterem Kubernetes, jako je ten, který poskytuje Docker Desktop, můžete zadat obrázky, které byly vytvořeny místně, pokud mají značku verze.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-170">When working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7a7d3-171">Ve výchozím nastavení se Kubernetes vždycky pokusí vyhledat novou image a zkusit si ji stáhnout.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="7a7d3-172">Pokud nenalezne obrázek v žádné z jeho známých úložišť, vytvoření pod se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="7a7d3-173">Pokud chcete pracovat s místními imagemi, nastavte `imagePullPolicy` na `Never`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="7a7d3-174">Vlastnost `ports` určuje, které porty kontejneru by měly být publikovány na pod.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-174">The `ports` property specifies which container ports should be published on the Pod.</span></span>  <span data-ttu-id="7a7d3-175">Image `stockservice` spouští službu na standardním portu HTTP, takže je publikovaný port 80.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="7a7d3-176">Část `resources` aplikuje omezení prostředků na kontejner běžící v poli pod.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-176">The `resources` section applies resource limits to the container running within the pod.</span></span> <span data-ttu-id="7a7d3-177">To je dobrý postup, protože zabrání jednotlivcům pod spotřebou veškerého dostupného procesoru nebo paměti na uzlu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-177">This is good practice as it prevents an individual pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="7a7d3-178">ASP.NET Core 3,0 je optimalizované a vyladěné pro spouštění v kontejnerech s omezenými prostředky a image `dotnet/core/aspnet` Docker nastavuje proměnnou prostředí, která sděluje modulu runtime `dotnet`, že je v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers, and the `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="7a7d3-179">Služba StockData</span><span class="sxs-lookup"><span data-stu-id="7a7d3-179">The StockData Service</span></span>

<span data-ttu-id="7a7d3-180">Část služby YAML souboru deklaruje službu, která poskytuje přístup k Luskům v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-180">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="7a7d3-181">Specifikace služby používá vlastnost `selector` ke spárování se spuštěným `Pods` v tomto případě hledá lusky pomocí popisku `run: stockdata`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-181">The Service spec uses the `selector` property to match running `Pods`, in this case looking for Pods with a label `run: stockdata`.</span></span> <span data-ttu-id="7a7d3-182">Zadané `port` v porovnávacích Luskech jsou publikovány pomocí pojmenované služby.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-182">The specified `port` on matching Pods are published by the named service.</span></span> <span data-ttu-id="7a7d3-183">Jiné lusky spuštěné v oboru názvů `stocks` mají přístup k HTTP na této službě pomocí `http://stockdata` jako adresy.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-183">Other Pods running in the `stocks` namespace can access HTTP on this service using `http://stockdata` as the address.</span></span> <span data-ttu-id="7a7d3-184">Lusky běžící v jiných oborech názvů můžou používat `http://stockdata.stocks` název hostitele.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-184">Pods running in other namespaces can use the `http://stockdata.stocks` hostname.</span></span> <span data-ttu-id="7a7d3-185">Přístup ke službě mezi obory názvů můžete řídit pomocí [zásad sítě](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="7a7d3-185">You can control cross-namespace service access using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="7a7d3-186">Nasazení aplikace StockData</span><span class="sxs-lookup"><span data-stu-id="7a7d3-186">Deploy the StockData application</span></span>

<span data-ttu-id="7a7d3-187">Pomocí `kubectl` použijte soubor `stockdata.yml` a ověřte, že se vytvořilo nasazení a služba.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-187">Use `kubectl` to apply the `stockdata.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="7a7d3-188">Aplikace StockWeb</span><span class="sxs-lookup"><span data-stu-id="7a7d3-188">The StockWeb application</span></span>

<span data-ttu-id="7a7d3-189">@No__t_0 soubor deklaruje nasazení a službu pro aplikaci MVC.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-189">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="7a7d3-190">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="7a7d3-190">Environment variables</span></span>

<span data-ttu-id="7a7d3-191">Část `env` objektu nasazení určuje proměnné prostředí, které se mají nastavit v kontejneru, na kterém běží `stockweb:1.0.0` image.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-191">The `env` section of the Deployment object specifies environment variables to be set in the container running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="7a7d3-192">Proměnná prostředí **`StockData__Address`** bude namapována na nastavení konfigurace `StockData:Address` díky poskytovateli konfigurace EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-192">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="7a7d3-193">Toto nastavení používá pro samostatné oddíly dvojitá podtržítka mezi názvy.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-193">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="7a7d3-194">Adresa používá název služby `stockdata` služby, který běží ve stejném oboru názvů Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-194">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="7a7d3-195">Proměnná prostředí **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** nastaví přepínač <xref:System.AppContext>, který umožňuje nešifrované připojení HTTP/2 pro <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-195">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="7a7d3-196">Tato proměnná prostředí je ekvivalentem nastavení přepínače v kódu, jak je znázorněno zde.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-196">This environment variable is the equivalent of setting the switch in code as shown here.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="7a7d3-197">Použití proměnné prostředí pro přepínač znamená, že nastavení může být snadno změněno v závislosti na kontextu, ve kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-197">Using an environment variable for the switch means the setting can easily be changed depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="7a7d3-198">Typy služeb</span><span class="sxs-lookup"><span data-stu-id="7a7d3-198">Service types</span></span>

<span data-ttu-id="7a7d3-199">Pokud chcete, aby byla webová aplikace přístupná z vnějšku clusteru, použije se vlastnost `type: NodePort`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-199">To make the Web application accessible from outside the cluster, the `type: NodePort` property is used.</span></span> <span data-ttu-id="7a7d3-200">Tento typ vlastnosti způsobí, že Kubernetes publikuje port 80 ve službě na libovolný port na soketech externích sítí clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-200">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="7a7d3-201">Přiřazený port najdete pomocí příkazu `kubectl get service`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-201">The port assigned can be found using the `kubectl get service` command.</span></span>

<span data-ttu-id="7a7d3-202">Služba `stockdata` by neměla být přístupná z vnějšku clusteru, takže používala výchozí typ `ClusterIP`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-202">The `stockdata` service shouldn't be accessible from outside the cluster, so it used the default type, `ClusterIP`.</span></span>

<span data-ttu-id="7a7d3-203">Provozní systémy budou pravděpodobně využívat integrovaný nástroj pro vyrovnávání zatížení a zpřístupňují veřejné aplikace externím uživatelům.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-203">Production systems will most likely use an integrated load-balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="7a7d3-204">Služby, které jsou k dispozici tímto způsobem, by měly používat `LoadBalancer` typ.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-204">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="7a7d3-205">Další informace o typech služeb najdete v dokumentaci k [publikování služby Kubernetes](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="7a7d3-205">For more information on service types, see the [Kubernetes' Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="7a7d3-206">Nasazení aplikace StockWeb</span><span class="sxs-lookup"><span data-stu-id="7a7d3-206">Deploy the StockWeb application</span></span>

<span data-ttu-id="7a7d3-207">Pomocí `kubectl` použijte soubor `stockweb.yml` a ověřte, že se vytvořilo nasazení a služba.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-207">Use `kubectl` to apply the `stockweb.yml` file and check that the Deployment and Service were created.</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="7a7d3-208">Výstup z příkazu `get service` ukazuje, že port HTTP byl publikován do `32564` portu v externí síti; v případě Docker desktopu to bude localhost.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-208">The output from the `get service` command shows that the HTTP port has been published to port `32564` on the external network; for Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="7a7d3-209">K aplikaci lze přistupovat procházením `http://localhost:32564`.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-209">The application can be accessed by browsing to `http://localhost:32564`.</span></span>

### <a name="testing-the-application"></a><span data-ttu-id="7a7d3-210">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="7a7d3-210">Testing the application</span></span>

<span data-ttu-id="7a7d3-211">Aplikace StockWeb zobrazí seznam akcií NASDAQ, které se načítají z jednoduché služby Request-Reply.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-211">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="7a7d3-212">Pro demonstrační účely zobrazuje každý řádek také jedinečné ID instance služby, která ho vrátila.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-212">For demonstration purposes, each line also shows the unique ID of the service instance that returned it.</span></span>

![Snímek obrazovky StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="7a7d3-214">Pokud se počet replik služby `stockdata` zvýšil, může se stát, že se hodnota **serveru** změní z řádku na řádek, ale ve skutečnosti všechny 100 záznamy se vždycky vrátí ze stejné instance.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-214">If the number of replicas of the `stockdata` service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="7a7d3-215">Pokud aktualizujete stránku každých několik sekund, ID serveru zůstane stejné.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-215">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="7a7d3-216">Proč k tomu dochází?</span><span class="sxs-lookup"><span data-stu-id="7a7d3-216">Why does this happen?</span></span> <span data-ttu-id="7a7d3-217">Tady jsou dva faktory.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-217">There are two factors at play here.</span></span>

<span data-ttu-id="7a7d3-218">Nejprve systém zjišťování služby Kubernetes ve výchozím nastavení používá Vyrovnávání zatížení pomocí kruhového dotazování.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-218">First, the Kubernetes service discovery system uses "round-robin" load-balancing by default.</span></span> <span data-ttu-id="7a7d3-219">Při prvním dotazování serveru DNS se vrátí první vyhovující IP adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-219">The first time the DNS server is queried, it will return the first matching IP address for the service.</span></span> <span data-ttu-id="7a7d3-220">V dalším čase, další IP adresa v seznamu atd., až do konce, v tomto okamžiku se smyčkou vrátí zpět na začátek.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-220">The next time, the next IP address in the list, and so on, until the end, at which point it loops back to the start.</span></span>

<span data-ttu-id="7a7d3-221">Za druhé se `HttpClient` používané pro klienta gRPC aplikace StockWeb vytvoří a spravuje pomocí [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)a jedna instance tohoto klienta se používá pro každé volání stránky.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-221">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="7a7d3-222">Klient nástroje provádí pouze jedno vyhledání DNS, takže všechny požadavky jsou směrovány na stejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-222">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="7a7d3-223">Vzhledem k tomu, že `HttpClientHandler` ukládá do mezipaměti z důvodů výkonu, více požadavků v rychlém úspěchu *bude používat stejnou* IP adresu, dokud nevyprší platnost položky DNS uložené v mezipaměti nebo z nějakého důvodu neodstraníte instanci obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-223">Furthermore, because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="7a7d3-224">To znamená, že ve výchozím nastavení nejsou požadavky na službu gRPC vyvážené napříč všemi instancemi této služby v clusteru.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-224">This means that by default requests to a gRPC service aren't balanced across all instances of that service in the cluster.</span></span> <span data-ttu-id="7a7d3-225">Různí spotřebitelé budou používat různé instance, ale nezaručují dobrou distribuci požadavků a vyvážené používání prostředků.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-225">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests and a balanced use of resources.</span></span>

<span data-ttu-id="7a7d3-226">Další kapitola, [sítě a sítě](service-mesh.md), se podíváme na to, jak tento problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="7a7d3-226">The next chapter, [Service Meshes](service-mesh.md), will look at how to address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7a7d3-227">[Předchozí](docker.md)
>[Další](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="7a7d3-227">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
