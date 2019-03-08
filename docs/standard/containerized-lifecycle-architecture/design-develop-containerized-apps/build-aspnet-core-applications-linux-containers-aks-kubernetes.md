---
title: Sestavení aplikace ASP.NET Core 2.1 nasazené jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676652"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="dba06-103">Sestavení aplikace ASP.NET Core 2.1 nasazené jako kontejnery Linux do AKS/Kubernetes produktu orchestrator</span><span class="sxs-lookup"><span data-stu-id="dba06-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="dba06-104">Služby Azure Kubernetes (AKS) je spravované Kubernetes Orchestrace služeb Azure, které zjednodušují nasazování kontejnerů a správu.</span><span class="sxs-lookup"><span data-stu-id="dba06-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="dba06-105">AKS hlavní funkce patří:</span><span class="sxs-lookup"><span data-stu-id="dba06-105">AKS main features are:</span></span>

- <span data-ttu-id="dba06-106">Rovina řízení hostovanou v Azure</span><span class="sxs-lookup"><span data-stu-id="dba06-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="dba06-107">Automatizované upgrady</span><span class="sxs-lookup"><span data-stu-id="dba06-107">Automated upgrades</span></span>
- <span data-ttu-id="dba06-108">Opravy</span><span class="sxs-lookup"><span data-stu-id="dba06-108">Self-healing</span></span>
- <span data-ttu-id="dba06-109">Uživatel konfigurovatelné škálování</span><span class="sxs-lookup"><span data-stu-id="dba06-109">User configurable scaling</span></span>
- <span data-ttu-id="dba06-110">Jednodušší uživatelské prostředí pro vývojáře i operátory clusteru.</span><span class="sxs-lookup"><span data-stu-id="dba06-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="dba06-111">Následující příklady prozkoumat vytvoření aplikace ASP.NET Core 2.1, která běží na Linuxu a nasadí do clusteru AKS v Azure, zatímco probíhá vývoj pomocí sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="dba06-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="dba06-112">Vytváří se projekt ASP.NET Core 2.1 pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dba06-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="dba06-113">ASP.NET Core je pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na Githubu.</span><span class="sxs-lookup"><span data-stu-id="dba06-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="dba06-114">Je multiplatformní, podpora Windows, macOS a Linux a je možné v zařízení, cloud a scénáře vložené a IoT.</span><span class="sxs-lookup"><span data-stu-id="dba06-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="dba06-115">Tento příklad používá jednoduchý projekt, který je založen na šabloně webového rozhraní API Visual Studio, takže není nutné žádné další znalostní báze k vytvoření vzorku.</span><span class="sxs-lookup"><span data-stu-id="dba06-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="dba06-116">Stačí vytvořit projekt pomocí standardní šablonu, která obsahuje všechny prvky malém projektu pomocí rozhraní REST API, technologií ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="dba06-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Přidáte okno nového projektu v sadě Visual Studio, vyberte webovou aplikaci ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="dba06-118">**Obrázek 4 – 36**.</span><span class="sxs-lookup"><span data-stu-id="dba06-118">**Figure 4-36**.</span></span> <span data-ttu-id="dba06-119">Vytvoření aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dba06-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="dba06-120">Chcete-li vytvořit ukázkový projekt v sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**, vyberte **webové**typů projektů v levém podokně, za nímž následuje **webové aplikace ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="dba06-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="dba06-121">Visual Studio obsahuje šablony pro webové projekty.</span><span class="sxs-lookup"><span data-stu-id="dba06-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="dba06-122">V našem příkladu vyberte **API** k vytvoření aplikace ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="dba06-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="dba06-123">Ověřte, že jste vybrali ASP.NET Core 2.1 jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dba06-123">Verify that you've selected ASP.NET Core 2.1 as the framework.</span></span> <span data-ttu-id="dba06-124">.NET core 2.1 je zahrnuta v poslední verzi sady Visual Studio 2017 a je automaticky nainstalovat a nakonfigurovat za vás při instalaci sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="dba06-124">.NET Core 2.1 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Visual Studio dialogové okno pro výběr typu webové aplikace ASP.NET Core s vybranou možností rozhraní API.](media/create-web-api-application.png)

<span data-ttu-id="dba06-126">**Obrázek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="dba06-126">**Figure 4-37**.</span></span> <span data-ttu-id="dba06-127">Typ projektu výběrem ASP.NET CORE 2.1 a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dba06-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="dba06-128">Pokud máte jakékoli předchozí verze .NET Core, můžete stáhnout a nainstalovat z verze 2.1 <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="dba06-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="dba06-129">Při vytváření projektu můžete přidat podporu Dockeru nebo později, tak je můžete "Dockerizace" svůj projekt v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="dba06-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="dba06-130">Chcete-li přidat podporu Dockeru po vytvoření projektu, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a vyberte **přidat** > **podporu Dockeru** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="dba06-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Možnost místní nabídky do existujícího projektu přidat podporu Dockeru: Klikněte pravým tlačítkem (na projekt) > Přidat > podpory Dockeru.](media/add-docker-support-to-project.png)

<span data-ttu-id="dba06-132">**Obrázek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="dba06-132">**Figure 4-38**.</span></span> <span data-ttu-id="dba06-133">Přidání podpory Dockeru do existujícího projektu</span><span class="sxs-lookup"><span data-stu-id="dba06-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="dba06-134">Abyste mohli dokončit přidávání podpory Docker, můžete Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="dba06-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="dba06-135">V tomto případě vyberte **Linux**, protože služba AKS nepodporuje kontejnery Windows (jako opožděné 2018).</span><span class="sxs-lookup"><span data-stu-id="dba06-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Dialogové okno Možnosti a vyberte cílový operační systém pro soubor Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="dba06-137">**Obrázek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="dba06-137">**Figure 4-39**.</span></span> <span data-ttu-id="dba06-138">Výběr kontejnery Linuxu.</span><span class="sxs-lookup"><span data-stu-id="dba06-138">Selecting Linux containers.</span></span>

<span data-ttu-id="dba06-139">Pomocí tohoto jednoduchého postupu mít vaše aplikace ASP.NET Core 2.1 běžící v kontejneru Linuxu.</span><span class="sxs-lookup"><span data-stu-id="dba06-139">With these simple steps, you have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="dba06-140">Jak vidíte, je zcela orientovaný produktivity pro vývojáře integraci mezi Visual Studio 2017 a Dockeru.</span><span class="sxs-lookup"><span data-stu-id="dba06-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="dba06-141">Nyní můžete spustit aplikaci **F5** klíče nebo pomocí **Přehrát** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="dba06-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="dba06-142">Po spuštění projektu, můžete vytvořit seznam imagí pomocí `docker images` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dba06-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="dba06-143">Měli byste vidět `mssampleapplication` image vytvořil automatické nasazení našich projekt pomocí sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="dba06-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Výstup konzoly z příkazu imagí dockeru, zobrazí se seznam s: Úložiště, značky, ID bitové kopie, vytvořeno (datum) a velikost.](media/docker-images-command.png)

<span data-ttu-id="dba06-145">**Obrázek 4 – 40**.</span><span class="sxs-lookup"><span data-stu-id="dba06-145">**Figure 4-40**.</span></span> <span data-ttu-id="dba06-146">Zobrazení imagí Dockeru</span><span class="sxs-lookup"><span data-stu-id="dba06-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="dba06-147">Zaregistrujte toto řešení v Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="dba06-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="dba06-148">Tuto image odeslat do jakéhokoli registru Dockeru, jako je třeba [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hubu, takže Image se dají nasadit do clusteru AKS z tohoto registru.</span><span class="sxs-lookup"><span data-stu-id="dba06-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="dba06-149">V tomto případě jsme už nahráním image do služby Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="dba06-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="dba06-150">Vytvoření bitové kopie v režimu vydání</span><span class="sxs-lookup"><span data-stu-id="dba06-150">Create the image in Release mode</span></span>

<span data-ttu-id="dba06-151">Teď vytvoříme image v **vydání** režimu (připravena na produkční prostředí) tak, že změníte na **vydání**, jak ukazuje obrázek 4 – 41 a spuštění aplikace, jako jsme to udělali dříve.</span><span class="sxs-lookup"><span data-stu-id="dba06-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Možnosti panelu nástrojů v sadě Visual Studio vytvářet v režimu vydání.](media/select-release-mode.png)

<span data-ttu-id="dba06-153">**Obrázek 4 – 41**.</span><span class="sxs-lookup"><span data-stu-id="dba06-153">**Figure 4-41**.</span></span> <span data-ttu-id="dba06-154">Výběr režimu vydání</span><span class="sxs-lookup"><span data-stu-id="dba06-154">Selecting Release Mode</span></span>

<span data-ttu-id="dba06-155">Pokud je spuštěn `docker image` příkaz, zobrazí se vám i obrázky vytvořené, jeden pro `debug` a druhou pro `release` režimu.</span><span class="sxs-lookup"><span data-stu-id="dba06-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="dba06-156">Vytvořit novou značku pro bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="dba06-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="dba06-157">Každá image kontejneru musí být s klíčovým slovem `loginServer` název registru.</span><span class="sxs-lookup"><span data-stu-id="dba06-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="dba06-158">Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.</span><span class="sxs-lookup"><span data-stu-id="dba06-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="dba06-159">Můžete zobrazit `loginServer` jméno z portálu Azure portal, přičemž informace ze služby Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="dba06-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Zobrazení prohlížeče s názvem registru kontejnerů Azure, v pravém horním rohu.](media/loginServer-name.png)

<span data-ttu-id="dba06-161">**Obrázek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="dba06-161">**Figure 4-42**.</span></span> <span data-ttu-id="dba06-162">Zobrazit název registru</span><span class="sxs-lookup"><span data-stu-id="dba06-162">View of the name of the Registry</span></span>

<span data-ttu-id="dba06-163">Nebo spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="dba06-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup z výše uvedeného příkazu konzoly.](media/az-cli-loginServer-name.png)

<span data-ttu-id="dba06-165">**Obrázek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="dba06-165">**Figure 4-43**.</span></span> <span data-ttu-id="dba06-166">Získejte název registru pomocí Powershellu</span><span class="sxs-lookup"><span data-stu-id="dba06-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="dba06-167">V obou případech získáte název.</span><span class="sxs-lookup"><span data-stu-id="dba06-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="dba06-168">V našem příkladu `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="dba06-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="dba06-169">Teď můžete označit image, přičemž nejnovější image (verze image), pomocí příkazu:</span><span class="sxs-lookup"><span data-stu-id="dba06-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="dba06-170">Po spuštění `docker tag` příkazu, výpis všech imagí s `docker images` příkazu a měli byste vidět na obrázku s novou značku.</span><span class="sxs-lookup"><span data-stu-id="dba06-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Výstup z příkazu imagí dockeru konzoly.](media/tagged-docker-images-list.png)

<span data-ttu-id="dba06-172">**Obrázek 4 – 44**.</span><span class="sxs-lookup"><span data-stu-id="dba06-172">**Figure 4-44**.</span></span> <span data-ttu-id="dba06-173">Zobrazení označených imagí</span><span class="sxs-lookup"><span data-stu-id="dba06-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="dba06-174">Nahrání image do služby ACR Azure</span><span class="sxs-lookup"><span data-stu-id="dba06-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="dba06-175">Nahrání image do služby ACR Azure, pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="dba06-175">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="dba06-176">Tento příkaz chvíli trvat, než nahrání imagí, ale poskytuje zpětnou vazbu v procesu.</span><span class="sxs-lookup"><span data-stu-id="dba06-176">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Výstupu z příkazu push docker konzoly: zobrazuje indikátor průběhu znakový pro jednotlivé úrovně.](media/uploading-image-to-acr.png)

<span data-ttu-id="dba06-178">**Obrázek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="dba06-178">**Figure 4-45**.</span></span> <span data-ttu-id="dba06-179">Nahrání image služby ACR</span><span class="sxs-lookup"><span data-stu-id="dba06-179">Uploading the image to the ACR</span></span>

<span data-ttu-id="dba06-180">Můžete vidět dole výsledek, že by vám měl po dokončení procesu:</span><span class="sxs-lookup"><span data-stu-id="dba06-180">You can see below the result you should get when the process completes:</span></span>

![Výstup z dockeru push příkazu, dokončeno, zobrazující všechny vrstvy nebo uzlů konzoly.](media/uploading-docker-images-complete.png)

<span data-ttu-id="dba06-182">**Obrázek 4 – 46**.</span><span class="sxs-lookup"><span data-stu-id="dba06-182">**Figure 4-46**.</span></span> <span data-ttu-id="dba06-183">Zobrazení uzlů</span><span class="sxs-lookup"><span data-stu-id="dba06-183">View of nodes</span></span>

<span data-ttu-id="dba06-184">Dalším krokem je nasazení kontejneru do vašeho clusteru AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="dba06-184">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="dba06-185">K tomu budete potřebovat soubor (**nasaďte soubor .yml**), který obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="dba06-185">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="dba06-186">Další informace o nasazení s využitím Kubernetes najdete v článku: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="dba06-186">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="dba06-187">Nyní jste téměř připraveni k nasazení pomocí **Kubectl**, ale nejprve musíte získat přihlašovací údaje ke clusteru AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="dba06-187">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup z výše uvedeného příkazu konzoly: Sloučené "MSSampleK8Cluster jako aktuální kontext v /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="dba06-189">**Obrázek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="dba06-189">**Figure 4-47**.</span></span> <span data-ttu-id="dba06-190">získání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="dba06-190">getting credentials</span></span>

<span data-ttu-id="dba06-191">Potom použijte `kubectl create` příkaz ke spuštění nasazení.</span><span class="sxs-lookup"><span data-stu-id="dba06-191">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Konzole výstup z výše uvedeného příkazu: "mssamplesbook" vytvoří nasazení.](media/kubectl-create-command.png)

<span data-ttu-id="dba06-194">**Obrázek 4 – 48**.</span><span class="sxs-lookup"><span data-stu-id="dba06-194">**Figure 4-48**.</span></span> <span data-ttu-id="dba06-195">Nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="dba06-195">Deploy to Kubernetes</span></span>

<span data-ttu-id="dba06-196">Po dokončení nasazení můžete přístup ke konzole Kubernetes s místní proxy server, ke kterému jste dočasně přístup pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="dba06-196">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="dba06-197">A přístup k adresu url `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="dba06-197">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Zobrazení prohlížeče s řídicí panel Kubernetes, včetně nasazení, Podů, sady replik a služeb.](media/kubernetes-cluster-information.png)

<span data-ttu-id="dba06-199">**Obrázek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="dba06-199">**Figure 4-49**.</span></span> <span data-ttu-id="dba06-200">Zobrazit informace o clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="dba06-200">View Kubernetes cluster information</span></span>

<span data-ttu-id="dba06-201">Teď máte aplikaci nasazenou na Azure pomocí kontejneru Linuxu a Kubernetes Cluster ve službě AKS.</span><span class="sxs-lookup"><span data-stu-id="dba06-201">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="dba06-202">Můžete přistupovat k vaší aplikace na veřejné IP adresy vaší služby, který můžete získat z webu Azure portal.</span><span class="sxs-lookup"><span data-stu-id="dba06-202">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="dba06-203">Zobrazí se postup vytvoření clusteru AKS pro tuto ukázku v části [ **nasadit do Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) v této příručce.</span><span class="sxs-lookup"><span data-stu-id="dba06-203">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dba06-204">[Předchozí](set-up-windows-containers-with-powershell.md)
>[další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="dba06-204">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
