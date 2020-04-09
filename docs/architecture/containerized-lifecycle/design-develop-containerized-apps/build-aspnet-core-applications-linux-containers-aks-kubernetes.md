---
title: Vytváření aplikací ASP.NET Core 2.2 nasazených jako linuxové kontejnery do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: 83d4d0a60db4bdc112bb35bfbf61c0396646ad31
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989022"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="463e0-103">Vytvářejte ASP.NET aplikace Core 2.2 nasazené jako linuxové kontejnery do orchestrátoru AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="463e0-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="463e0-104">Azure Kubernetes Services (AKS) je spravované služby Orchestraations Kubernetes v Azure, které zjednodušují nasazení a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="463e0-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="463e0-105">AKS hlavní rysy jsou:</span><span class="sxs-lookup"><span data-stu-id="463e0-105">AKS main features are:</span></span>

- <span data-ttu-id="463e0-106">Rovina ovládacího prvku hostované v Azure</span><span class="sxs-lookup"><span data-stu-id="463e0-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="463e0-107">Automatické upgrady</span><span class="sxs-lookup"><span data-stu-id="463e0-107">Automated upgrades</span></span>
- <span data-ttu-id="463e0-108">Samoopravení</span><span class="sxs-lookup"><span data-stu-id="463e0-108">Self-healing</span></span>
- <span data-ttu-id="463e0-109">Uživatelsky konfigurovatelné škálování</span><span class="sxs-lookup"><span data-stu-id="463e0-109">User configurable scaling</span></span>
- <span data-ttu-id="463e0-110">Jednodušší uživatelské prostředí pro vývojáře i operátory clusteru.</span><span class="sxs-lookup"><span data-stu-id="463e0-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="463e0-111">Následující příklady zkoumají vytvoření aplikace ASP.NET Core 2.2, která běží na Linuxu a nasadí se do clusteru AKS v Azure, zatímco vývoj se provádí pomocí Visual Studia 2017.</span><span class="sxs-lookup"><span data-stu-id="463e0-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="463e0-112">Vytvoření projektu ASP.NET Jádra 2.2 pomocí Visual Studia 2017</span><span class="sxs-lookup"><span data-stu-id="463e0-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="463e0-113">ASP.NET Core je univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="463e0-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="463e0-114">Je to multiplatformní, podporuje Windows, macOS a Linux a dá se používat ve scénářích zařízení, cloudu a embedded/IoT.</span><span class="sxs-lookup"><span data-stu-id="463e0-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="463e0-115">Tento příklad používá jednoduchý projekt, který je založen na šabloně webového rozhraní API sady Visual Studio, takže k vytvoření ukázky nepotřebujete žádné další znalosti.</span><span class="sxs-lookup"><span data-stu-id="463e0-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="463e0-116">Projekt je třeba vytvořit pouze pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s rozhraním REST API pomocí technologie ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="463e0-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Přidejte nové okno projektu v sadě Visual Studio a vyberte ASP.NET základní webovou aplikaci.](media/create-aspnet-core-application.png)

<span data-ttu-id="463e0-118">**Obrázek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="463e0-118">**Figure 4-36**.</span></span> <span data-ttu-id="463e0-119">Vytváření ASP.NET základní aplikace</span><span class="sxs-lookup"><span data-stu-id="463e0-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="463e0-120">Chcete-li vytvořit ukázkový projekt v sadě Visual Studio, vyberte **možnost Soubor** > **nový** > **projekt**, vyberte typy **webových** projektů v levém podokně následované **ASP.NET základní webové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="463e0-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="463e0-121">Visual Studio uvádí šablony pro webové projekty.</span><span class="sxs-lookup"><span data-stu-id="463e0-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="463e0-122">V našem příkladu vyberte **rozhraní API** a vytvořte ASP.NET webovou aplikaci rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="463e0-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="463e0-123">Ověřte, zda jste jako framework vybrali ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="463e0-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="463e0-124">.NET Core 2.2 je součástí poslední verze Visual Studia 2017 a je automaticky nainstalován a nakonfigurován pro vás při instalaci Sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="463e0-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Visual Studio dialogové okno pro výběr typu ASP.NET základní webové aplikace s vybranou možností rozhraní API.](media/create-web-api-application.png)

<span data-ttu-id="463e0-126">**Obrázek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="463e0-126">**Figure 4-37**.</span></span> <span data-ttu-id="463e0-127">Výběr ASP.NET typu projektu CORE 2.2 a Web API</span><span class="sxs-lookup"><span data-stu-id="463e0-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="463e0-128">Pokud máte předchozí verzi rozhraní .NET Core, můžete si stáhnout <https://dotnet.microsoft.com/download>a nainstalovat verzi 2.2 z aplikace .</span><span class="sxs-lookup"><span data-stu-id="463e0-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="463e0-129">Podporu Dockeru můžete přidat při vytváření projektu nebo později, takže můžete "Dockerize" váš projekt kdykoli.</span><span class="sxs-lookup"><span data-stu-id="463e0-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="463e0-130">Chcete-li přidat podporu Dockeru po vytvoření projektu, klikněte pravým tlačítkem myši na uzel projektu v Průzkumníku řešení a v místní nabídce vyberte **Přidat** > **podporu Dockeru.**</span><span class="sxs-lookup"><span data-stu-id="463e0-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Možnost kontextové nabídky pro přidání podpory Dockeru do existujícího projektu: Klikněte pravým tlačítkem myši (na projektu) > Přidat podporu > Dockeru.](media/add-docker-support-to-project.png)

<span data-ttu-id="463e0-132">**Obrázek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="463e0-132">**Figure 4-38**.</span></span> <span data-ttu-id="463e0-133">Přidání podpory Dockeru do existujícího projektu</span><span class="sxs-lookup"><span data-stu-id="463e0-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="463e0-134">Chcete-li dokončit přidání podpory Dockeru, můžete si vybrat Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="463e0-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="463e0-135">V takovém případě vyberte **Linux**, protože AKS nepodporuje kontejnery Windows (ke konci roku 2018).</span><span class="sxs-lookup"><span data-stu-id="463e0-135">In this case, select **Linux**, because AKS doesn't support Windows Containers (as of late 2018).</span></span>

![Dialogové okno Možnosti pro výběr cílového operačního systému pro dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="463e0-137">**Obrázek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="463e0-137">**Figure 4-39**.</span></span> <span data-ttu-id="463e0-138">Výběr linuxových kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="463e0-138">Selecting Linux containers.</span></span>

<span data-ttu-id="463e0-139">S těmito jednoduchými kroky máte ASP.NET aplikaci Core 2.2 spuštěnou v kontejneru Linuxu.</span><span class="sxs-lookup"><span data-stu-id="463e0-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="463e0-140">Jak můžete vidět, integrace mezi Visual Studio 2017 a Dockerem je zcela orientována na produktivitu vývojáře.</span><span class="sxs-lookup"><span data-stu-id="463e0-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer's productivity.</span></span>

<span data-ttu-id="463e0-141">Nyní můžete aplikaci spustit pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát.**</span><span class="sxs-lookup"><span data-stu-id="463e0-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="463e0-142">Po spuštění projektu můžete vypsat `docker images` obrázky pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="463e0-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="463e0-143">Měli byste `mssampleapplication` vidět image vytvořenou automatickým nasazením našeho projektu s Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="463e0-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Výstup konzoly z příkazu image dockeru zobrazuje seznam s: Úložiště, Značka, ID obrázku, Vytvořeno (datum) a Velikost.](media/docker-images-command.png)

<span data-ttu-id="463e0-145">**Obrázek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="463e0-145">**Figure 4-40**.</span></span> <span data-ttu-id="463e0-146">Zobrazení i0 bitových kopií Dockeru</span><span class="sxs-lookup"><span data-stu-id="463e0-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="463e0-147">Registrace řešení v registru kontejnerů Azure</span><span class="sxs-lookup"><span data-stu-id="463e0-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="463e0-148">Nahrajte image do libovolného registru Dockeru, jako je [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hub, takže image se dá nasadit do clusteru AKS z tohoto registru.</span><span class="sxs-lookup"><span data-stu-id="463e0-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="463e0-149">V takovém případě nahráváme image do registru kontejnerů Azure.</span><span class="sxs-lookup"><span data-stu-id="463e0-149">In this case, we're uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="463e0-150">Vytvoření obrazu v režimu vydání</span><span class="sxs-lookup"><span data-stu-id="463e0-150">Create the image in Release mode</span></span>

<span data-ttu-id="463e0-151">Nyní vytvoříme obrázek v režimu **vydání** (připraven k výrobě) změnou na **verzi**, jak je znázorněno na obrázku 4-41, a spuštěním aplikace jako předtím.</span><span class="sxs-lookup"><span data-stu-id="463e0-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Možnost panelu nástrojů ve VS pro sestavení v režimu vydání.](media/select-release-mode.png)

<span data-ttu-id="463e0-153">**Obrázek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="463e0-153">**Figure 4-41**.</span></span> <span data-ttu-id="463e0-154">Výběr režimu vydání</span><span class="sxs-lookup"><span data-stu-id="463e0-154">Selecting Release Mode</span></span>

<span data-ttu-id="463e0-155">Pokud spustíte `docker image` příkaz, uvidíte oba vytvořené obrazy, jeden `release` pro a druhý pro `debug` režim.</span><span class="sxs-lookup"><span data-stu-id="463e0-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="463e0-156">Vytvoření nové značky pro obrázek</span><span class="sxs-lookup"><span data-stu-id="463e0-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="463e0-157">Každá bitová kopie kontejneru `loginServer` musí být označena názvem registru.</span><span class="sxs-lookup"><span data-stu-id="463e0-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="463e0-158">Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.</span><span class="sxs-lookup"><span data-stu-id="463e0-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="463e0-159">Název můžete `loginServer` zobrazit z portálu Azure, přičemž informace z registru kontejnerů Azure</span><span class="sxs-lookup"><span data-stu-id="463e0-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Zobrazení prohlížeče názvu registru kontejneru Azure, v pravém horním rohu.](media/loginServer-name.png)

<span data-ttu-id="463e0-161">**Obrázek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="463e0-161">**Figure 4-42**.</span></span> <span data-ttu-id="463e0-162">Zobrazení názvu registru</span><span class="sxs-lookup"><span data-stu-id="463e0-162">View of the name of the Registry</span></span>

<span data-ttu-id="463e0-163">Nebo spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="463e0-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu.](media/az-cli-loginServer-name.png)

<span data-ttu-id="463e0-165">**Obrázek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="463e0-165">**Figure 4-43**.</span></span> <span data-ttu-id="463e0-166">Získání názvu registru pomocí prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="463e0-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="463e0-167">V obou případech získáte název.</span><span class="sxs-lookup"><span data-stu-id="463e0-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="463e0-168">V našem `mssampleacr.azurecr.io`příkladu .</span><span class="sxs-lookup"><span data-stu-id="463e0-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="463e0-169">Nyní můžete označit obrázek, přičemž nejnovější obrázek (release image), s příkazem:</span><span class="sxs-lookup"><span data-stu-id="463e0-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="463e0-170">Po spuštění `docker tag` příkazu uveďte `docker images` obrázky pomocí příkazu a obrázek byste měli vidět s novou značkou.</span><span class="sxs-lookup"><span data-stu-id="463e0-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Výstup konzoly z příkazu image dockeru.](media/tagged-docker-images-list.png)

<span data-ttu-id="463e0-172">**Obrázek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="463e0-172">**Figure 4-44**.</span></span> <span data-ttu-id="463e0-173">Zobrazení tagovaných obrázků</span><span class="sxs-lookup"><span data-stu-id="463e0-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="463e0-174">Zasunutí image do Azure ACR</span><span class="sxs-lookup"><span data-stu-id="463e0-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="463e0-175">Přihlášení do registru kontejnerů Azure</span><span class="sxs-lookup"><span data-stu-id="463e0-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="463e0-176">Zatlačte image do Azure ACR pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="463e0-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="463e0-177">Tento příkaz chvíli trvá, než obrázky nahraje, ale poskytne vám zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="463e0-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Výstup konzoly z příkazu push dockeru: zobrazuje pruh průběhu založený na znaku pro každou vrstvu.](media/uploading-image-to-acr.png)

<span data-ttu-id="463e0-179">**Obrázek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="463e0-179">**Figure 4-45**.</span></span> <span data-ttu-id="463e0-180">Nahrání obrázku do ACR</span><span class="sxs-lookup"><span data-stu-id="463e0-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="463e0-181">Níže můžete vidět výsledek, který byste měli získat po dokončení procesu:</span><span class="sxs-lookup"><span data-stu-id="463e0-181">You can see below the result you should get when the process completes:</span></span>

![Výstup konzoly z příkazu push dockeru, dokončený, zobrazující všechny hladiny nebo uzly.](media/uploading-docker-images-complete.png)

<span data-ttu-id="463e0-183">**Obrázek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="463e0-183">**Figure 4-46**.</span></span> <span data-ttu-id="463e0-184">Zobrazení uzlů</span><span class="sxs-lookup"><span data-stu-id="463e0-184">View of nodes</span></span>

<span data-ttu-id="463e0-185">Dalším krokem je nasazení kontejneru do clusteru AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="463e0-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="463e0-186">K tomu potřebujete soubor (**.yml deploy file),** který obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="463e0-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
        - name: mssample-services-app
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
> <span data-ttu-id="463e0-187">Další informace o nasazení s Kubernetes naleznete v:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="463e0-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="463e0-188">Nyní jste téměř připraveni k nasazení pomocí **Kubectl**, ale nejprve musíte získat pověření do clusteru AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="463e0-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup konzoly z výše uvedeného příkazu: Sloučený "MSSampleK8Cluster jako aktuální kontext v /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="463e0-190">**Obrázek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="463e0-190">**Figure 4-47**.</span></span> <span data-ttu-id="463e0-191">získání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="463e0-191">getting credentials</span></span>

<span data-ttu-id="463e0-192">Potom pomocí `kubectl create` příkazu spusťte nasazení.</span><span class="sxs-lookup"><span data-stu-id="463e0-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Konzolový výstup z výše uvedeného příkazu: nasazení "mssamplesbook" vytvořen.](media/kubectl-create-command.png)

<span data-ttu-id="463e0-195">**Obrázek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="463e0-195">**Figure 4-48**.</span></span> <span data-ttu-id="463e0-196">Nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="463e0-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="463e0-197">Po dokončení nasazení můžete přistupovat ke konzoli Kubernetes pomocí místního proxy serveru, ke kterému můžete dočasně přistupovat pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="463e0-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="463e0-198">A přístup k `http://127.0.0.1:8001`url .</span><span class="sxs-lookup"><span data-stu-id="463e0-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, pody, sady replik a služby.](media/kubernetes-cluster-information.png)

<span data-ttu-id="463e0-200">**Obrázek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="463e0-200">**Figure 4-49**.</span></span> <span data-ttu-id="463e0-201">Zobrazit informace o clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="463e0-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="463e0-202">Teď máte aplikaci nasazenou v Azure pomocí linuxového kontejneru a clusteru AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="463e0-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="463e0-203">K procházení aplikace můžete přistupovat k veřejné IP adrese vaší služby, kterou můžete získat z portálu Azure.</span><span class="sxs-lookup"><span data-stu-id="463e0-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="463e0-204">Můžete vidět, jak vytvořit clusterAKS pro tuto ukázku v části [**Nasazení do služby Azure Kubernetes (AKS)**](deploy-azure-kubernetes-service.md) v této příručce.</span><span class="sxs-lookup"><span data-stu-id="463e0-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="463e0-205">[Předchozí](set-up-windows-containers-with-powershell.md)
>[další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="463e0-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
