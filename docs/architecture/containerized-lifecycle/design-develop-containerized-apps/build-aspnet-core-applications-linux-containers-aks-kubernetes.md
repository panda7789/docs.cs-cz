---
title: Sestavování aplikací ASP.NET Core 2,2 nasazených jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848751"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="d1522-103">Sestavování aplikací ASP.NET Core 2,2 nasazených jako kontejnery Linux do AKS/Kubernetes Orchestrator</span><span class="sxs-lookup"><span data-stu-id="d1522-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="d1522-104">Azure Kubernetes Services (AKS) jsou spravované služby Kubernetes orchestrace v Azure, které zjednodušují nasazení a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="d1522-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="d1522-105">AKS hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="d1522-105">AKS main features are:</span></span>

- <span data-ttu-id="d1522-106">Rovina řízení hostovaná v Azure</span><span class="sxs-lookup"><span data-stu-id="d1522-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="d1522-107">Automatizované upgrady</span><span class="sxs-lookup"><span data-stu-id="d1522-107">Automated upgrades</span></span>
- <span data-ttu-id="d1522-108">Samo – opravit</span><span class="sxs-lookup"><span data-stu-id="d1522-108">Self-healing</span></span>
- <span data-ttu-id="d1522-109">Uživatelsky konfigurovatelné škálování</span><span class="sxs-lookup"><span data-stu-id="d1522-109">User configurable scaling</span></span>
- <span data-ttu-id="d1522-110">Jednodušší uživatelské prostředí pro vývojáře i pro operátory clusterů.</span><span class="sxs-lookup"><span data-stu-id="d1522-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="d1522-111">Následující příklady Prozkoumejte vytvoření aplikace ASP.NET Core 2,2, která běží na platformě Linux a nasadí do clusteru AKS v Azure, zatímco vývoj se provádí pomocí sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d1522-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="d1522-112">Vytvoření projektu ASP.NET Core 2,2 pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d1522-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="d1522-113">ASP.NET Core je vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="d1522-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="d1522-114">Je to podpora pro různé platformy, Windows, macOS a Linux a dá se použít v scénářích zařízení, Cloud a integrovaných a IoT.</span><span class="sxs-lookup"><span data-stu-id="d1522-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="d1522-115">V tomto příkladu se používá jednoduchý projekt založený na šabloně webového rozhraní API sady Visual Studio, takže k vytvoření ukázky nepotřebujete žádné další znalosti.</span><span class="sxs-lookup"><span data-stu-id="d1522-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="d1522-116">Projekt je nutné vytvořit pouze pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s REST API pomocí technologie ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="d1522-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Přidejte nové okno projektu v aplikaci Visual Studio a vyberte ASP.NET Core webové aplikace.](media/create-aspnet-core-application.png)

<span data-ttu-id="d1522-118">**Obrázek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="d1522-118">**Figure 4-36**.</span></span> <span data-ttu-id="d1522-119">Vytváření ASP.NET Core aplikace</span><span class="sxs-lookup"><span data-stu-id="d1522-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="d1522-120">Chcete-li vytvořit ukázkový projekt v aplikaci Visual Studio, vyberte **soubor** > **Nový** > **projekt**, v levém podokně vyberte typy **webových** projektů a **ASP.NET Core webové aplikace**.</span><span class="sxs-lookup"><span data-stu-id="d1522-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="d1522-121">Visual Studio obsahuje šablony pro webové projekty.</span><span class="sxs-lookup"><span data-stu-id="d1522-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="d1522-122">V našem příkladu vyberte **rozhraní API** a vytvořte aplikaci webového rozhraní api pro ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1522-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="d1522-123">Ověřte, že jste vybrali ASP.NET Core 2,2 jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d1522-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="d1522-124">.NET Core 2,2 je součástí poslední verze sady Visual Studio 2017 a při instalaci sady Visual Studio 2017 se automaticky nainstaluje a nakonfiguruje.</span><span class="sxs-lookup"><span data-stu-id="d1522-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Dialog sady Visual Studio pro výběr typu ASP.NET Core webové aplikace s vybranou možností rozhraní API.](media/create-web-api-application.png)

<span data-ttu-id="d1522-126">**Obrázek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="d1522-126">**Figure 4-37**.</span></span> <span data-ttu-id="d1522-127">Výběr typu projektu ASP.NET CORE 2,2 a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d1522-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="d1522-128">Pokud máte předchozí verzi .NET Core, můžete si stáhnout a nainstalovat verzi 2,2 z <https://dotnet.microsoft.com/download>.</span><span class="sxs-lookup"><span data-stu-id="d1522-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="d1522-129">Můžete přidat podporu Docker při vytváření projektu nebo následně, abyste mohli projekt kdykoli "ukotvovat".</span><span class="sxs-lookup"><span data-stu-id="d1522-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="d1522-130">Chcete-li přidat podporu Docker po vytvoření projektu, klikněte pravým tlačítkem myši na uzel projektu v Průzkumník řešení a v místní nabídce vyberte **Přidat** **podporu > Docker** .</span><span class="sxs-lookup"><span data-stu-id="d1522-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Možnost místní nabídky pro přidání podpory Docker do existujícího projektu: klikněte pravým tlačítkem (na projekt) > přidat podporu > Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="d1522-132">**Obrázek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="d1522-132">**Figure 4-38**.</span></span> <span data-ttu-id="d1522-133">Přidání podpory Docker do existujícího projektu</span><span class="sxs-lookup"><span data-stu-id="d1522-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="d1522-134">Pokud chcete dokončit přidávání podpory Docker, můžete zvolit Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="d1522-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="d1522-135">V takovém případě vyberte **Linux**, protože AKS nepodporuje kontejnery Windows (od nejnovějšího 2018).</span><span class="sxs-lookup"><span data-stu-id="d1522-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Dialog možností pro výběr cílového OS pro souboru Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="d1522-137">**Obrázek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="d1522-137">**Figure 4-39**.</span></span> <span data-ttu-id="d1522-138">Výběr kontejnerů Linux.</span><span class="sxs-lookup"><span data-stu-id="d1522-138">Selecting Linux containers.</span></span>

<span data-ttu-id="d1522-139">V těchto jednoduchých krocích máte aplikaci ASP.NET Core 2,2 běžící v kontejneru Linux.</span><span class="sxs-lookup"><span data-stu-id="d1522-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="d1522-140">Jak vidíte, integrace mezi Visual Studio 2017 a Docker je zcela zaměřená na produktivitu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="d1522-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="d1522-141">Nyní můžete spustit aplikaci pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát** .</span><span class="sxs-lookup"><span data-stu-id="d1522-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="d1522-142">Po spuštění projektu můžete zobrazit seznam imagí pomocí příkazu `docker images`.</span><span class="sxs-lookup"><span data-stu-id="d1522-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="d1522-143">Měli byste vidět `mssampleapplication` image vytvořenou automatickým nasazením našeho projektu pomocí sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d1522-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Výstup konzoly z příkazu Docker images zobrazuje seznam s: úložiště, značka, ID obrázku, Vytvořeno (datum) a velikost.](media/docker-images-command.png)

<span data-ttu-id="d1522-145">**Obrázek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="d1522-145">**Figure 4-40**.</span></span> <span data-ttu-id="d1522-146">Zobrazení imagí Docker</span><span class="sxs-lookup"><span data-stu-id="d1522-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="d1522-147">Zaregistrujte řešení v Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d1522-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="d1522-148">Nahrajte image do libovolného registru Docker, jako je [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hub, aby bylo možné image nasadit do clusteru AKS z tohoto registru.</span><span class="sxs-lookup"><span data-stu-id="d1522-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="d1522-149">V tomto případě nahrajeme obrázek do Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="d1522-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="d1522-150">Vytvoření image v režimu vydání</span><span class="sxs-lookup"><span data-stu-id="d1522-150">Create the image in Release mode</span></span>

<span data-ttu-id="d1522-151">Nyní vytvoříme bitovou kopii v režimu **vydání** (připraveno pro produkční prostředí) tak, že se změní na **release**, jak je znázorněno na obrázku 4-41 a aplikace se spustí stejně jako dřív.</span><span class="sxs-lookup"><span data-stu-id="d1522-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Možnost panelu nástrojů v sadě VS k sestavení v režimu vydání.](media/select-release-mode.png)

<span data-ttu-id="d1522-153">**Obrázek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="d1522-153">**Figure 4-41**.</span></span> <span data-ttu-id="d1522-154">Výběr režimu vydání</span><span class="sxs-lookup"><span data-stu-id="d1522-154">Selecting Release Mode</span></span>

<span data-ttu-id="d1522-155">Pokud spustíte příkaz `docker image`, zobrazí se oba vytvořené bitové kopie, jeden pro `debug` a druhý pro `release` režim.</span><span class="sxs-lookup"><span data-stu-id="d1522-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="d1522-156">Vytvořit novou značku pro obrázek</span><span class="sxs-lookup"><span data-stu-id="d1522-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="d1522-157">Každá image kontejneru musí být označena názvem `loginServer` registru.</span><span class="sxs-lookup"><span data-stu-id="d1522-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="d1522-158">Tato značka se používá pro směrování při vkládání imagí kontejneru do registru imagí.</span><span class="sxs-lookup"><span data-stu-id="d1522-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="d1522-159">Název `loginServer` můžete zobrazit z Azure Portal a přebírat informace z Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d1522-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![V prohlížeči se zobrazí název služby Azure Container Registry v pravém horním rohu.](media/loginServer-name.png)

<span data-ttu-id="d1522-161">**Obrázek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="d1522-161">**Figure 4-42**.</span></span> <span data-ttu-id="d1522-162">Zobrazení názvu registru</span><span class="sxs-lookup"><span data-stu-id="d1522-162">View of the name of the Registry</span></span>

<span data-ttu-id="d1522-163">Nebo spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="d1522-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu](media/az-cli-loginServer-name.png)

<span data-ttu-id="d1522-165">**Obrázek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="d1522-165">**Figure 4-43**.</span></span> <span data-ttu-id="d1522-166">Získání názvu registru pomocí PowerShellu</span><span class="sxs-lookup"><span data-stu-id="d1522-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="d1522-167">V obou případech získáte název.</span><span class="sxs-lookup"><span data-stu-id="d1522-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="d1522-168">V našem příkladu `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="d1522-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="d1522-169">Nyní můžete označit Image pomocí nejnovější bitové kopie (obrázek verze) a příkazu:</span><span class="sxs-lookup"><span data-stu-id="d1522-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d1522-170">Po spuštění příkazu `docker tag` zobrazte seznam imagí pomocí příkazu `docker images` a měli byste vidět obrázek s novou značkou.</span><span class="sxs-lookup"><span data-stu-id="d1522-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Výstup konzoly z příkazu Docker images](media/tagged-docker-images-list.png)

<span data-ttu-id="d1522-172">**Obrázek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="d1522-172">**Figure 4-44**.</span></span> <span data-ttu-id="d1522-173">Zobrazení tagovaných obrázků</span><span class="sxs-lookup"><span data-stu-id="d1522-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="d1522-174">Vložení image do Azure ACR</span><span class="sxs-lookup"><span data-stu-id="d1522-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="d1522-175">Přihlášení k Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="d1522-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="d1522-176">Nahrajte image do Azure ACR pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="d1522-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="d1522-177">Tento příkaz při nahrávání imagí trvá, ale v procesu vám poskytne zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="d1522-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Výstup konzoly z příkazu Docker push: zobrazuje indikátor průběhu na základě znaků pro každou vrstvu.](media/uploading-image-to-acr.png)

<span data-ttu-id="d1522-179">**Obrázek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="d1522-179">**Figure 4-45**.</span></span> <span data-ttu-id="d1522-180">Obrázek se nahrává do ACR.</span><span class="sxs-lookup"><span data-stu-id="d1522-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="d1522-181">Vidíte pod výsledek, který byste měli získat po dokončení procesu:</span><span class="sxs-lookup"><span data-stu-id="d1522-181">You can see below the result you should get when the process completes:</span></span>

![Výstup konzoly z příkazu Docker push, dokončený, zobrazení všech vrstev nebo uzlů](media/uploading-docker-images-complete.png)

<span data-ttu-id="d1522-183">**Obrázek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="d1522-183">**Figure 4-46**.</span></span> <span data-ttu-id="d1522-184">Zobrazení uzlů</span><span class="sxs-lookup"><span data-stu-id="d1522-184">View of nodes</span></span>

<span data-ttu-id="d1522-185">Dalším krokem je nasazení kontejneru do clusteru AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d1522-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="d1522-186">V takovém případě potřebujete soubor (**soubor. yml Deploy**), který obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="d1522-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="d1522-187">Další informace o nasazení pomocí Kubernetes najdete v tématu: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="d1522-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="d1522-188">Teď jste skoro připraveni nasadit pomocí **Kubectl**, ale nejdřív musíte získat přihlašovací údaje do clusteru AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="d1522-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup z konzoly z výše uvedeného příkazu: sloučený MSSampleK8Cluster jako aktuální kontext v/root/.Kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="d1522-190">**Obrázek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="d1522-190">**Figure 4-47**.</span></span> <span data-ttu-id="d1522-191">získávání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="d1522-191">getting credentials</span></span>

<span data-ttu-id="d1522-192">Pak pomocí příkazu `kubectl create` spusťte nasazení.</span><span class="sxs-lookup"><span data-stu-id="d1522-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Výstup z konzoly z výše uvedeného příkazu: bylo vytvořeno nasazení mssamplesbook.](media/kubectl-create-command.png)

<span data-ttu-id="d1522-195">**Obrázek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="d1522-195">**Figure 4-48**.</span></span> <span data-ttu-id="d1522-196">Nasazení na Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d1522-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="d1522-197">Až se nasazení dokončí, můžete ke konzole Kubernetes přistupovat pomocí místního proxy serveru, ke kterému se můžete dostat do dočasného přístupu pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="d1522-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="d1522-198">A přístup k adrese URL `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="d1522-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, lusky, sady replik a služby.](media/kubernetes-cluster-information.png)

<span data-ttu-id="d1522-200">**Obrázek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="d1522-200">**Figure 4-49**.</span></span> <span data-ttu-id="d1522-201">Zobrazit informace o clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d1522-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="d1522-202">Nyní máte aplikaci nasazenou v Azure, pomocí kontejneru Linux a clusteru AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d1522-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="d1522-203">Přístup k vaší aplikaci můžete zpřístupnit do veřejné IP adresy vaší služby, kterou můžete získat z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="d1522-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="d1522-204">V této příručce najdete informace o tom, jak vytvořit cluster AKS pro tuto ukázku v oddílu [**nasazení do služby Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) .</span><span class="sxs-lookup"><span data-stu-id="d1522-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d1522-205">[Předchozí](set-up-windows-containers-with-powershell.md)
>[Další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="d1522-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
