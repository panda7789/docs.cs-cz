---
title: Kubernetes-gRPC pro vývojáře WCF
description: Spuštění ASP.NET Core gRPC Services v clusteru Kubernetes.
ms.date: 09/02/2019
ms.openlocfilehash: 22271343f8f0d0454469b2f35e717f5b7e939294
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711292"
---
# <a name="kubernetes"></a><span data-ttu-id="b942a-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b942a-103">Kubernetes</span></span>

<span data-ttu-id="b942a-104">I když je možné ručně spustit kontejnery na hostitelích Docker, pro spolehlivé provozní systémy je lepší používat modul orchestrace kontejnerů ke správě více instancí spuštěných v několika serverech v clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="b942a-105">K dispozici jsou různé moduly pro orchestraci kontejnerů, včetně Kubernetes, Docker Swarm a Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="b942a-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="b942a-106">V těchto modulech ale Kubernetes je daleko a nejvíce využíváno, takže bude tato kapitola zaměřena.</span><span class="sxs-lookup"><span data-stu-id="b942a-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="b942a-107">Kubernetes obsahuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="b942a-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="b942a-108">**Plánování** spouští kontejnery na více uzlech v rámci clusteru, což zajišťuje vyvážené využití dostupného prostředku, udržování kontejnerů běžících v případě výpadků a zpracování kumulativních aktualizací pro nové verze imagí nebo nové konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b942a-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="b942a-109">**Kontroly stavu** monitorují kontejnery, aby bylo zajištěno pokračování služby.</span><span class="sxs-lookup"><span data-stu-id="b942a-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="b942a-110">**Služba DNS & Service Discovery** zpracovává směrování mezi službami v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="b942a-111">Příchozí **zpřístupňuje** vybrané služby externě a obecně poskytuje vyrovnávání zatížení napříč instancemi těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="b942a-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="b942a-112">**Správa prostředků** připojuje externí prostředky jako úložiště do kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="b942a-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="b942a-113">Tato kapitola podrobně popisuje, jak nasadit službu ASP.NET Core gRPC a webovou stránku, která tuto službu spotřebovává do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="b942a-114">Použitá ukázková aplikace je k dispozici v úložišti [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="b942a-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="b942a-115">Terminologie Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b942a-115">Kubernetes terminology</span></span>

<span data-ttu-id="b942a-116">Kubernetes používá *konfiguraci požadovaného stavu*: rozhraní API se používá k popisu objektů, jako jsou *lusky*, *nasazení*a *služby*, a *Řídicí rovina* se stará o implementaci požadovaného stavu napříč všemi *uzly* v *clusteru*.</span><span class="sxs-lookup"><span data-stu-id="b942a-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="b942a-117">Cluster Kubernetes má *Hlavní* uzel, který spouští *rozhraní Kubernetes API*, které můžete komunikovat pomocí programu nebo pomocí nástroje příkazového řádku `kubectl`.</span><span class="sxs-lookup"><span data-stu-id="b942a-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="b942a-118">`kubectl` může vytvářet a spravovat objekty pomocí argumentů příkazového řádku, ale funguje nejlépe s YAML soubory, které obsahují data deklarace pro objekty Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="b942a-119">Soubory Kubernetes YAML</span><span class="sxs-lookup"><span data-stu-id="b942a-119">Kubernetes YAML files</span></span>

<span data-ttu-id="b942a-120">Každý soubor Kubernetes YAML bude mít alespoň tři vlastnosti nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="b942a-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="b942a-121">Vlastnost `apiVersion` slouží k určení verze (a rozhraní API), pro který je soubor určen.</span><span class="sxs-lookup"><span data-stu-id="b942a-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="b942a-122">Vlastnost `kind` určuje druh objektu, který představuje YAML.</span><span class="sxs-lookup"><span data-stu-id="b942a-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="b942a-123">Vlastnost `metadata` obsahuje vlastnosti objektu jako `name`, `namespace`a `labels`.</span><span class="sxs-lookup"><span data-stu-id="b942a-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="b942a-124">Většina souborů YAML Kubernetes bude také obsahovat oddíl `spec`, který popisuje prostředky a konfiguraci potřebné k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="b942a-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="b942a-125">Podů</span><span class="sxs-lookup"><span data-stu-id="b942a-125">Pods</span></span>

<span data-ttu-id="b942a-126">Lusky jsou základními jednotkami spuštění v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="b942a-127">Můžou spouštět více kontejnerů, ale používají se také ke spouštění jednoduchých kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="b942a-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="b942a-128">V poli pod jsou také všechny prostředky úložiště vyžadované kontejnery a IP adresa sítě.</span><span class="sxs-lookup"><span data-stu-id="b942a-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="b942a-129">Služby</span><span class="sxs-lookup"><span data-stu-id="b942a-129">Services</span></span>

<span data-ttu-id="b942a-130">Služby jsou meta objekty, které popisují lusky (nebo sady lusků) a poskytují způsob, jak k nim přistupovat v rámci clusteru, jako je například mapování názvu služby na skupinu pod IP adresou pomocí služby DNS clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="b942a-131">Nasazení</span><span class="sxs-lookup"><span data-stu-id="b942a-131">Deployments</span></span>

<span data-ttu-id="b942a-132">Nasazení jsou objekty *požadovaného stavu* pro lusky.</span><span class="sxs-lookup"><span data-stu-id="b942a-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="b942a-133">Pokud vytvoříte v případě ručně, po ukončení se nerestartuje.</span><span class="sxs-lookup"><span data-stu-id="b942a-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="b942a-134">Nasazení se používají k tomu, aby cluster informoval a kolik replik v těchto Luskech měl běžet v současné době.</span><span class="sxs-lookup"><span data-stu-id="b942a-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="b942a-135">Další objekty</span><span class="sxs-lookup"><span data-stu-id="b942a-135">Other objects</span></span>

<span data-ttu-id="b942a-136">Lusky, služby a nasazení představují jenom tři základní typy objektů.</span><span class="sxs-lookup"><span data-stu-id="b942a-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="b942a-137">Existují spousty dalších typů objektů, které jsou spravovány clustery Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="b942a-138">Další informace najdete v dokumentaci k [konceptům Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="b942a-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="b942a-139">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="b942a-139">Namespaces</span></span>

<span data-ttu-id="b942a-140">Clustery Kubernetes jsou navržené tak, aby se škálovat na stovky nebo tisíce uzlů a spouštěly podobné počty služeb.</span><span class="sxs-lookup"><span data-stu-id="b942a-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="b942a-141">Aby nedocházelo ke konfliktům mezi názvy objektů, používají se obory názvů k seskupení objektů dohromady jako součást větších aplikací.</span><span class="sxs-lookup"><span data-stu-id="b942a-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="b942a-142">Vlastní služby Kubernetes běží v oboru názvů `default`.</span><span class="sxs-lookup"><span data-stu-id="b942a-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="b942a-143">Všechny uživatelské objekty by měly být vytvořeny ve vlastních oborech názvů, aby se předešlo potenciálním konfliktům s výchozími objekty nebo jinými klienty v clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="b942a-144">Začínáme s Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b942a-144">Get started with Kubernetes</span></span>

<span data-ttu-id="b942a-145">Pokud používáte Docker Desktop pro Windows nebo Docker Desktop for Mac, Kubernetes je už k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b942a-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="b942a-146">Stačí ho povolit v části **Kubernetes** okna **Nastavení** :</span><span class="sxs-lookup"><span data-stu-id="b942a-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Povolit Kubernetes v Docker desktopu](media/kubernetes/enable-kubernetes-docker-desktop.png)

<span data-ttu-id="b942a-148">Chcete-li spustit místní cluster Kubernetes v systému Linux, zvažte možnost [minikube](https://github.com/kubernetes/minikube)nebo [MicroK8s](https://microk8s.io/) , pokud je vaše distribuce systému Linux podporována [přichycení](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="b942a-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="b942a-149">Pokud chcete ověřit, že je cluster spuštěný a přístupný, spusťte příkaz `kubectl version`:</span><span class="sxs-lookup"><span data-stu-id="b942a-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="b942a-150">V tomto příkladu jsou spuštěny `kubectl` CLI a server Kubernetes verze 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="b942a-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="b942a-151">Každá verze `kubectl` má podporovat předchozí a další verzi serveru, proto by `kubectl` 1,14 měla fungovat i na serverech verze 1,13 a 1,15.</span><span class="sxs-lookup"><span data-stu-id="b942a-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="b942a-152">Spuštění služeb na Kubernetes</span><span class="sxs-lookup"><span data-stu-id="b942a-152">Run services on Kubernetes</span></span>

<span data-ttu-id="b942a-153">Ukázková aplikace má `kube` adresář, který obsahuje tři soubory YAML.</span><span class="sxs-lookup"><span data-stu-id="b942a-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="b942a-154">`namespace.yml` soubor deklaruje vlastní obor názvů: `stocks`.</span><span class="sxs-lookup"><span data-stu-id="b942a-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="b942a-155">`stockdata.yml` soubor deklaruje nasazení a službu pro aplikaci gRPC a soubor `stockweb.yml` deklaruje nasazení a službu pro webovou aplikaci ASP.NET Core 3,0 MVC, která využívá službu gRPC.</span><span class="sxs-lookup"><span data-stu-id="b942a-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 3.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="b942a-156">Chcete-li použít soubor `YAML` s `kubectl`, spusťte příkaz `apply -f`:</span><span class="sxs-lookup"><span data-stu-id="b942a-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="b942a-157">Příkaz `apply` zkontroluje platnost souboru YAML a zobrazí všechny chyby přijaté z rozhraní API, ale nečeká na vytvoření všech objektů deklarovaných v souboru, protože to může nějakou dobu trvat.</span><span class="sxs-lookup"><span data-stu-id="b942a-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this can take some time.</span></span> <span data-ttu-id="b942a-158">Pomocí příkazu `kubectl get` s příslušnými typy objektů ověřte vytvoření objektu v clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="b942a-159">Deklarace oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b942a-159">The namespace declaration</span></span>

<span data-ttu-id="b942a-160">Deklarace oboru názvů je jednoduchá a vyžaduje pouze přiřazení `name`:</span><span class="sxs-lookup"><span data-stu-id="b942a-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="b942a-161">Použijte `kubectl` k použití `namespace.yml` souboru a k potvrzení úspěšného vytvoření oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="b942a-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="b942a-162">Aplikace StockData</span><span class="sxs-lookup"><span data-stu-id="b942a-162">The StockData application</span></span>

<span data-ttu-id="b942a-163">`stockdata.yml` soubor deklaruje dva objekty: nasazení a službu.</span><span class="sxs-lookup"><span data-stu-id="b942a-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="b942a-164">Nasazení StockData</span><span class="sxs-lookup"><span data-stu-id="b942a-164">The StockData Deployment</span></span>

<span data-ttu-id="b942a-165">Část nasazení souboru YAML poskytuje `spec` pro samotné nasazení, včetně počtu požadovaných replik a `template` objektů pod, které se mají vytvořit a spravovat nasazením.</span><span class="sxs-lookup"><span data-stu-id="b942a-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="b942a-166">Všimněte si, že objekty nasazení jsou spravovány rozhraním API `apps`, jak je uvedeno v `apiVersion`namísto hlavního rozhraní API Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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

<span data-ttu-id="b942a-167">Vlastnost `spec.selector` se používá ke spárování spuštěných lusků s nasazením.</span><span class="sxs-lookup"><span data-stu-id="b942a-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="b942a-168">Vlastnost `metadata.labels` pod musí odpovídat vlastnosti `matchLabels` nebo volání rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b942a-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="b942a-169">Oddíl `template.spec` deklaruje kontejner, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="b942a-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="b942a-170">Když pracujete s místním clusterem Kubernetes, jako je například ten, který poskytuje Docker Desktop, můžete zadat obrázky, které byly vytvořeny místně, pokud mají značku verze.</span><span class="sxs-lookup"><span data-stu-id="b942a-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b942a-171">Ve výchozím nastavení se Kubernetes vždycky pokusí vyhledat novou image a zkusit si ji stáhnout.</span><span class="sxs-lookup"><span data-stu-id="b942a-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="b942a-172">Pokud nenalezne obrázek v žádné z jeho známých úložišť, vytvoření pod se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b942a-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="b942a-173">Pokud chcete pracovat s místními imagemi, nastavte `imagePullPolicy` na `Never`.</span><span class="sxs-lookup"><span data-stu-id="b942a-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="b942a-174">Vlastnost `ports` určuje, které porty kontejneru by měly být publikovány na pod.</span><span class="sxs-lookup"><span data-stu-id="b942a-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="b942a-175">Image `stockservice` spouští službu na standardním portu HTTP, takže je publikovaný port 80.</span><span class="sxs-lookup"><span data-stu-id="b942a-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="b942a-176">Část `resources` aplikuje omezení prostředků na kontejner běžící v poli pod.</span><span class="sxs-lookup"><span data-stu-id="b942a-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="b942a-177">To je dobrý postup, protože zabrání jednotlivcům pod spotřebou veškerého dostupného procesoru nebo paměti na uzlu.</span><span class="sxs-lookup"><span data-stu-id="b942a-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="b942a-178">ASP.NET Core 3,0 je optimalizované a vyladěné pro spouštění v kontejnerech s omezenými prostředky.</span><span class="sxs-lookup"><span data-stu-id="b942a-178">ASP.NET Core 3.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="b942a-179">Image `dotnet/core/aspnet` Docker nastavuje proměnnou prostředí pro informování modulu runtime `dotnet`, že je v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b942a-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="b942a-180">Služba StockData</span><span class="sxs-lookup"><span data-stu-id="b942a-180">The StockData Service</span></span>

<span data-ttu-id="b942a-181">Část služby YAML souboru deklaruje službu, která poskytuje přístup k Luskům v rámci clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

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

<span data-ttu-id="b942a-182">`spec` služby používá vlastnost `selector` ke shodě se spuštěným `Pods`, v tomto případě hledáte lusky, které mají `run: stockdata`popisku.</span><span class="sxs-lookup"><span data-stu-id="b942a-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="b942a-183">Zadaná `port` v porovnávacích Luskech je publikována pomocí pojmenované služby.</span><span class="sxs-lookup"><span data-stu-id="b942a-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="b942a-184">Jiné lusky spuštěné v oboru názvů `stocks` mají k HTTP v této službě přístup pomocí `http://stockdata` jako adresy.</span><span class="sxs-lookup"><span data-stu-id="b942a-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="b942a-185">Lusky běžící v jiných oborech názvů můžou používat `http://stockdata.stocks` název hostitele.</span><span class="sxs-lookup"><span data-stu-id="b942a-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="b942a-186">Přístup ke službě mezi obory názvů můžete řídit pomocí [zásad sítě](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="b942a-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="b942a-187">Nasazení aplikace StockData</span><span class="sxs-lookup"><span data-stu-id="b942a-187">Deploy the StockData application</span></span>

<span data-ttu-id="b942a-188">Použijte `kubectl` pro použití `stockdata.yml` souboru a potvrďte, že se vytvořilo nasazení a služba:</span><span class="sxs-lookup"><span data-stu-id="b942a-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

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

### <a name="the-stockweb-application"></a><span data-ttu-id="b942a-189">Aplikace StockWeb</span><span class="sxs-lookup"><span data-stu-id="b942a-189">The StockWeb application</span></span>

<span data-ttu-id="b942a-190">`stockweb.yml` soubor deklaruje nasazení a službu pro aplikaci MVC.</span><span class="sxs-lookup"><span data-stu-id="b942a-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

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

#### <a name="environment-variables"></a><span data-ttu-id="b942a-191">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="b942a-191">Environment variables</span></span>

<span data-ttu-id="b942a-192">Část `env` objektu nasazení určuje proměnné prostředí, které se mají nastavit v kontejneru, na kterém běží `stockweb:1.0.0` image.</span><span class="sxs-lookup"><span data-stu-id="b942a-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="b942a-193">Proměnná prostředí **`StockData__Address`** bude namapována na nastavení konfigurace `StockData:Address` díky poskytovateli konfigurace EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="b942a-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="b942a-194">Toto nastavení používá pro samostatné oddíly dvojitá podtržítka mezi názvy.</span><span class="sxs-lookup"><span data-stu-id="b942a-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="b942a-195">Adresa používá název služby `stockdata` služby, který běží ve stejném oboru názvů Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="b942a-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="b942a-196">Proměnná prostředí **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** nastaví přepínač <xref:System.AppContext>, který umožňuje nešifrované připojení HTTP/2 pro <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="b942a-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="b942a-197">Tato proměnná prostředí má stejný krok jako nastavení přepínače v kódu, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="b942a-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="b942a-198">Pokud pro přepínač použijete proměnnou prostředí, můžete snadno změnit kontext v závislosti na kontextu, ve kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="b942a-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="b942a-199">Typy služeb</span><span class="sxs-lookup"><span data-stu-id="b942a-199">Service types</span></span>

<span data-ttu-id="b942a-200">Vlastnost `type: NodePort` slouží k zajištění přístupu k webové aplikaci z vnějšku clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="b942a-201">Tento typ vlastnosti způsobí, že Kubernetes publikuje port 80 ve službě na libovolný port na soketech externích sítí clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="b942a-202">Přiřazený port můžete najít pomocí příkazu `kubectl get service`.</span><span class="sxs-lookup"><span data-stu-id="b942a-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="b942a-203">Služba `stockdata` by neměla být přístupná z vnějšku clusteru, takže používá výchozí typ `ClusterIP`.</span><span class="sxs-lookup"><span data-stu-id="b942a-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="b942a-204">Provozní systémy pravděpodobně využívají integrovaný nástroj pro vyrovnávání zatížení k vystavování veřejných aplikací externím spotřebitelům.</span><span class="sxs-lookup"><span data-stu-id="b942a-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="b942a-205">Služby, které jsou k dispozici tímto způsobem, by měly používat `LoadBalancer` typ.</span><span class="sxs-lookup"><span data-stu-id="b942a-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="b942a-206">Další informace o typech služeb najdete v dokumentaci ke [službě Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="b942a-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="b942a-207">Nasazení aplikace StockWeb</span><span class="sxs-lookup"><span data-stu-id="b942a-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="b942a-208">Použijte `kubectl` pro použití `stockweb.yml` souboru a potvrďte, že se vytvořilo nasazení a služba:</span><span class="sxs-lookup"><span data-stu-id="b942a-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

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

<span data-ttu-id="b942a-209">Výstupem příkazu `get service` se ukáže, že port HTTP byl na externí síti publikovaný na portu 32564.</span><span class="sxs-lookup"><span data-stu-id="b942a-209">The output of the `get service` command shows that the HTTP port has been published to port 32564 on the external network.</span></span> <span data-ttu-id="b942a-210">V případě Docker desktopu to bude localhost.</span><span class="sxs-lookup"><span data-stu-id="b942a-210">For Docker Desktop, this will be localhost.</span></span> <span data-ttu-id="b942a-211">Přístup k aplikaci můžete získat procházením `http://localhost:32564`.</span><span class="sxs-lookup"><span data-stu-id="b942a-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="b942a-212">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="b942a-212">Test the application</span></span>

<span data-ttu-id="b942a-213">Aplikace StockWeb zobrazí seznam akcií NASDAQ, které se načítají z jednoduché služby Request-Reply.</span><span class="sxs-lookup"><span data-stu-id="b942a-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="b942a-214">V této ukázce se v každém řádku zobrazí také jedinečné ID instance služby, která ho vrátila.</span><span class="sxs-lookup"><span data-stu-id="b942a-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![Snímek obrazovky StockWeb](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="b942a-216">Pokud se počet replik služby `stockdata` zvýšil, může se stát, že se hodnota **serveru** změní z řádku na řádek, ale ve skutečnosti všechny 100 záznamy se vždycky vrátí ze stejné instance.</span><span class="sxs-lookup"><span data-stu-id="b942a-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="b942a-217">Pokud aktualizujete stránku každých několik sekund, ID serveru zůstane stejné.</span><span class="sxs-lookup"><span data-stu-id="b942a-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="b942a-218">Proč k tomu dochází?</span><span class="sxs-lookup"><span data-stu-id="b942a-218">Why does this happen?</span></span> <span data-ttu-id="b942a-219">Tady jsou dva faktory.</span><span class="sxs-lookup"><span data-stu-id="b942a-219">There are two factors at play here.</span></span>

<span data-ttu-id="b942a-220">Nejprve systém zjišťování služby Kubernetes ve výchozím nastavení používá Vyrovnávání zatížení pomocí kruhového dotazování.</span><span class="sxs-lookup"><span data-stu-id="b942a-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="b942a-221">Při prvním dotazování serveru DNS se vrátí první vyhovující IP adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="b942a-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="b942a-222">Příště vrátí další IP adresu v seznamu a tak dále, až do konce.</span><span class="sxs-lookup"><span data-stu-id="b942a-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="b942a-223">V tomto okamžiku se smyčka vrátí na začátek.</span><span class="sxs-lookup"><span data-stu-id="b942a-223">At that point it loops back to the start.</span></span>

<span data-ttu-id="b942a-224">Za druhé se `HttpClient` používané pro klienta gRPC aplikace StockWeb vytvoří a spravuje pomocí [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)a jedna instance tohoto klienta se používá pro každé volání stránky.</span><span class="sxs-lookup"><span data-stu-id="b942a-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="b942a-225">Klient nástroje provádí pouze jedno vyhledání DNS, takže všechny požadavky jsou směrovány na stejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="b942a-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="b942a-226">A vzhledem k tomu, že `HttpClientHandler` ukládá do mezipaměti z důvodů výkonu, více požadavků v rychlém *úspěchu bude používat* stejnou IP adresu, dokud nevyprší platnost položky DNS v mezipaměti nebo z nějakého důvodu neodstraníte instanci obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="b942a-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="b942a-227">Výsledkem je, že ve výchozím nastavení nejsou požadavky na službu gRPC vyvážené napříč všemi instancemi této služby v clusteru.</span><span class="sxs-lookup"><span data-stu-id="b942a-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="b942a-228">Různí spotřebitelé budou používat různé instance, ale nezaručují dobrou distribuci požadavků nebo vyváženého využívání prostředků.</span><span class="sxs-lookup"><span data-stu-id="b942a-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="b942a-229">Tento problém bude řešit další kapitola, [sítě](service-mesh.md).</span><span class="sxs-lookup"><span data-stu-id="b942a-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b942a-230">[Předchozí](docker.md)
>[Další](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="b942a-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
