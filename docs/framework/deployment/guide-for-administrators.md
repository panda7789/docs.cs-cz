---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f56ccbf549ce8f1750ba0bf9cf4a945007694258
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502363"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="0a0ee-102">.NET Framework – průvodce nasazením pro administrátory</span><span class="sxs-lookup"><span data-stu-id="0a0ee-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="0a0ee-103">Tento článek popisuje, jak může správce systému nasadit [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho systémové závislosti napříč sítí pomocí nástroje System Center Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="0a0ee-104">V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="0a0ee-105">Seznam všech softwarových a hardwarových požadavků pro instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], naleznete v tématu [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a0ee-106">Software zmíněný v tomto dokumentu, včetně mimo jiné [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager a služby Active Directory, se vztahují licenční podmínky a ujednání.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="0a0ee-107">V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="0a0ee-108">Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="0a0ee-109">Informace o podpoře pro rozhraní .NET Framework najdete v tématu [podporu zásad životního cyklu Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) na webu Microsoft Support.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](https://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="0a0ee-110">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="0a0ee-111">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="0a0ee-111">The deployment process</span></span>](#the_deployment_process)  
 [<span data-ttu-id="0a0ee-112">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0a0ee-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)  
 [<span data-ttu-id="0a0ee-113">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="0a0ee-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="0a0ee-114">Vytvoření balíčku a programu</span><span class="sxs-lookup"><span data-stu-id="0a0ee-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="0a0ee-115">Vyberte distribuční bod</span><span class="sxs-lookup"><span data-stu-id="0a0ee-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="0a0ee-116">Nasazení balíčku</span><span class="sxs-lookup"><span data-stu-id="0a0ee-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="0a0ee-117">Prostředky</span><span class="sxs-lookup"><span data-stu-id="0a0ee-117">Resources</span></span>](#resources)  
[<span data-ttu-id="0a0ee-118">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="0a0ee-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="0a0ee-119">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="0a0ee-119">The deployment process</span></span>  
 <span data-ttu-id="0a0ee-120">Pokud je k dispozici podpůrná infrastruktura, lze distribuovatelný balíček rozhraní .NET Framework nasadit na počítače v síti pomocí nástroje System Center 2012 Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="0a0ee-121">Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="0a0ee-122">**Kolekce** jsou skupiny prostředků nástroje Configuration Manager, jako jsou uživatelé, skupiny uživatelů nebo počítačů, u kterých je nasazení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="0a0ee-123">Další informace najdete v tématu [kolekcí v nástroji Configuration Manager](https://technet.microsoft.com/library/gg682169.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-123">For more information, see [Collections in Configuration Manager](https://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="0a0ee-124">**Balíčky a programy** představují většinou softwarové aplikace nainstalovat na klientský počítač, ale mohou také obsahovat jednotlivé soubory, aktualizace nebo dokonce jednotlivé příkazy.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="0a0ee-125">Další informace najdete v tématu [balíčků a programů v nástroji Configuration Manager](https://technet.microsoft.com/library/gg699369.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-125">For more information, see [Packages and Programs in Configuration Manager](https://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="0a0ee-126">**Distribuční body** lokalitu nástroje Configuration Manager jsou role systému, které ukládají soubory nezbytné pro ke spuštění softwaru na klientských počítačích.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="0a0ee-127">Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="0a0ee-128">Další informace najdete v tématu [Úvod do správy obsahu v nástroji Configuration Manager](https://technet.microsoft.com/library/gg682083.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-128">For more information, see [Introduction to content Management in Configuration Manager](https://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="0a0ee-129">**Nasazení** pověří příslušné členy zadané cílové kolekce k instalaci softwarového balíčku.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="0a0ee-130">Další informace najdete v tématu [nasazení aplikací v nástroji Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-130">For more information, see [How to Deploy Applications in Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a0ee-131">Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="0a0ee-132">Další možnosti nasazení nástroje Configuration Manager, najdete v článku [knihovně dokumentace nástroje Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="0a0ee-133">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0a0ee-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="0a0ee-134">System Center 2012 Configuration Manager můžete použít k nasazení tiché instalace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kde uživatelé nespolupracují s instalačním procesem.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="0a0ee-135">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="0a0ee-136">[Vytvoření kolekce](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="0a0ee-137">[Vytvoření balíčku a programu pro rozhraní .NET Framework redistributable](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="0a0ee-138">[Vyberte distribuční bod](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="0a0ee-139">[Nasazení balíčku](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="0a0ee-140">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="0a0ee-140">Create a collection</span></span>  
 <span data-ttu-id="0a0ee-141">V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="0a0ee-142">Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="0a0ee-143">Další informace o pravidlech členství, včetně dotazů a přímých pravidel, naleznete v tématu [seznámení s kolekcemi v nástroji Configuration Manager](https://technet.microsoft.com/library/gg682177.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](https://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="0a0ee-144">Postup vytvoření kolekce:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="0a0ee-145">V konzole nástroje Configuration Manager, zvolte **prostředky a Kompatibilita**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="0a0ee-146">V **prostředky a Kompatibilita** pracovního prostoru, zvolte **kolekce zařízení**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="0a0ee-147">Na **Domů** kartu **vytvořit** skupině, zvolte **vytvořit kolekci zařízení**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="0a0ee-148">Na **Obecné** stránku **Průvodce vytvořením kolekce zařízení**, zadejte název kolekce.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="0a0ee-149">Zvolte **Procházet** určit limitující kolekci.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="0a0ee-150">Na **pravidla členství** zvolte **přidat pravidlo**a klikněte na tlačítko **přímého pravidla** otevřít **vytvořením pravidla přímého členství**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="0a0ee-151">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="0a0ee-152">Na **hledat prostředky** stránku, **třídy prostředků** klikněte na položku **systémový prostředek**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="0a0ee-153">V **název atributu** klikněte na položku **název**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="0a0ee-154">V **hodnotu** zadejte `%`a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="0a0ee-155">Na **vyberte prostředky** stránce, zaškrtněte políčko pro každý počítač, který chcete nasadit rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="0a0ee-156">Zvolte **Další**a poté průvodce dokončete.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="0a0ee-157">Na **pravidla členství** stránku **Průvodce vytvořením kolekce zařízení**, zvolte **Další**a poté průvodce dokončete.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="0a0ee-158">Další informace o kolekcích najdete v tématu [kolekcí v nástroji Configuration Manager](https://technet.microsoft.com/library/bb693730.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-158">For more information about collections, see [Collections in Configuration Manager](https://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="0a0ee-159">Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0a0ee-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="0a0ee-160">Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="0a0ee-161">Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="0a0ee-162">Postup vytvoření balíčku:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="0a0ee-163">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**...</span><span class="sxs-lookup"><span data-stu-id="0a0ee-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="0a0ee-164">V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="0a0ee-165">Na **Domů** kartě **vytvořit** skupině, zvolte **vytvořit balíček**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="0a0ee-166">Na **balíčku** stránku **Průvodce vytvoření balíčku a programu**, zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="0a0ee-167">Jméno: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0a0ee-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="0a0ee-168">Výrobce: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="0a0ee-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="0a0ee-169">Jazyk.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="0a0ee-170">Zvolte **tento balíček obsahuje zdrojové soubory**a klikněte na tlačítko **Procházet** vyberte místní nebo síťovou složku, která obsahuje instalační soubory rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="0a0ee-171">Když vyberete složku, zvolte **OK**a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="0a0ee-172">Na **typ programu** stránku průvodce, zvolte **standardní Program**a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="0a0ee-173">Na **Program** stránku **Průvodce vytvoření balíčku a programu**, zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="0a0ee-174">**Jméno:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="0a0ee-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="0a0ee-175">**Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Možnosti příkazového řádku jsou popsané v tabulce po provedení těchto kroků)</span><span class="sxs-lookup"><span data-stu-id="0a0ee-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="0a0ee-176">**Spustit:** zvolte **skryté**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="0a0ee-177">**Program lze spustit:** zvolit možnost, která určuje, že program může běžet bez ohledu na to, zda je přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="0a0ee-178">Na **požadavky** zvolte **Další** přijmout výchozí hodnoty a pak dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="0a0ee-179">Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="0a0ee-180">Možnost</span><span class="sxs-lookup"><span data-stu-id="0a0ee-180">Option</span></span>|<span data-ttu-id="0a0ee-181">Popis</span><span class="sxs-lookup"><span data-stu-id="0a0ee-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0a0ee-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-182">**/q**</span></span>|<span data-ttu-id="0a0ee-183">Nastaví tichý režim.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-183">Sets quiet mode.</span></span> <span data-ttu-id="0a0ee-184">Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="0a0ee-185">**/ norestart /**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-185">**/norestart**</span></span>|<span data-ttu-id="0a0ee-186">Zabrání instalačnímu programu v automatickém restartování.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="0a0ee-187">Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="0a0ee-188">**chainingpackage** *název balíčku*</span><span class="sxs-lookup"><span data-stu-id="0a0ee-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="0a0ee-189">Určuje název balíčku, který provádí řetězení.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="0a0ee-190">Tato informace je oznámena spolu s dalšími informacemi relace instalace pro ty, kteří se přihlásili k odběru [Microsoft zkušeností zlepšování Program uživatelů (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="0a0ee-191">Pokud název balíčku obsahuje mezery, použijte uvozovky jako oddělovače; Příklad: **chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="0a0ee-192">Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="0a0ee-193">Program provede nasazení tiché instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="0a0ee-194">V případě tiché instalace uživatelé nespolupracují s instalačním procesem a zřetězující aplikace musí zachytit návratový kód a zpracovat restartování; Zobrazit [získávání informací o průběhu z instalačního balíčku](https://go.microsoft.com/fwlink/?LinkId=179606).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://go.microsoft.com/fwlink/?LinkId=179606).</span></span>  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="0a0ee-195">Výběr distribučního bodu</span><span class="sxs-lookup"><span data-stu-id="0a0ee-195">Select a distribution point</span></span>  
 <span data-ttu-id="0a0ee-196">Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="0a0ee-197">Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="0a0ee-198">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="0a0ee-199">V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="0a0ee-200">Ze seznamu balíčků vyberte balíček **rozhraní .NET Framework 4.5** , kterou jste vytvořili v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="0a0ee-201">Na **Domů** kartě **nasazení** skupině, zvolte **distribuovat obsah**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="0a0ee-202">Na **Obecné** karty **Průvodce distribucí obsahu**, zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="0a0ee-203">Na **cílové umístění obsahu** stránku průvodce, zvolte **přidat**a klikněte na tlačítko **distribuční bod**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="0a0ee-204">V **přidat distribuční body** dialogového okna, vyberte distribuční body, který bude hostovat balíček a program a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="0a0ee-205">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="0a0ee-206">Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-206">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="0a0ee-207">Před nasazením balíčku a programu ověřte, zda byl nainstalován v distribučním bodě; naleznete v části "Monitorování obsahu" [operace a údržba pro správu obsahu v nástroji Configuration Manager](https://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](https://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="0a0ee-208">Nasazení balíčku</span><span class="sxs-lookup"><span data-stu-id="0a0ee-208">Deploy the package</span></span>  
 <span data-ttu-id="0a0ee-209">Postup nasazení balíčku a programu .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="0a0ee-210">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="0a0ee-211">V **softwarová knihovna** pracovního prostoru, rozbalte **správy aplikací**a klikněte na tlačítko **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="0a0ee-212">Ze seznamu balíčků vyberte balíček, je vytvořena s názvem **rozhraní .NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="0a0ee-213">Na **Domů** kartě **nasazení** skupině, zvolte **nasadit**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="0a0ee-214">Na **Obecné** stránku **Průvodce nasazením softwaru**, zvolte **Procházet**a pak vyberte aplikaci, kterou jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="0a0ee-215">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="0a0ee-216">Na **obsahu** stránku průvodce, ověřte, zda se zobrazí bodu, ze kterého chcete software distribuovat a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="0a0ee-217">Na **nastavení nasazení** stránku průvodce, ujistěte se, že **akce** je nastavena na **nainstalovat**, a **účel** je nastavena na **Vyžaduje**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="0a0ee-218">Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="0a0ee-219">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="0a0ee-220">Na **plánování** stránku průvodce, určete, kdy má být nainstalované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="0a0ee-221">Můžete zvolit **nový** přiřadit čas instalace nebo dáte pokyn, aby software pro instalaci, když se uživatel přihlásí na nebo vypnutá nebo co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="0a0ee-222">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="0a0ee-223">Na **činnost koncového uživatele** stránku průvodce, použijte výchozí hodnoty a vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="0a0ee-224">Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="0a0ee-225">Informace o těchto možnostech najdete v tématu [vlastnosti názvu ohlášení: Záložka plánu](https://technet.microsoft.com/library/bb694016.aspx) v knihovně TechNet.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="0a0ee-226">Na **distribučních bodů** stránku průvodce, použijte výchozí hodnoty a vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="0a0ee-227">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-227">Complete the wizard.</span></span> <span data-ttu-id="0a0ee-228">Průběh nasazení můžete monitorovat **nasazení** uzlu **monitorování** pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="0a0ee-229">Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="0a0ee-230">Informace o chybových kódech instalace rozhraní .NET Framework 4.5, najdete v článku [návratové kódy](#return_codes) později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="0a0ee-231">Prostředky</span><span class="sxs-lookup"><span data-stu-id="0a0ee-231">Resources</span></span>  
 <span data-ttu-id="0a0ee-232">Další informace o infrastruktuře pro testovaní nasazení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Distribuovatelný balíček, najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="0a0ee-233">**Služba Active Directory, DNS a DHCP.**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="0a0ee-234">Active Directory Domain Services pro systém Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="0a0ee-234">Active Directory Domain Services for Windows Server 2008</span></span>](https://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="0a0ee-235">DNS Server</span><span class="sxs-lookup"><span data-stu-id="0a0ee-235">DNS Server</span></span>](https://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="0a0ee-236">DHCP Server</span><span class="sxs-lookup"><span data-stu-id="0a0ee-236">DHCP Server</span></span>](https://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="0a0ee-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="0a0ee-238">Instalace systému SQL Server 2008 (Video o systému SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0a0ee-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](https://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="0a0ee-239">Přehled zabezpečení služby SQL Server 2008 pro správce databáze</span><span class="sxs-lookup"><span data-stu-id="0a0ee-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="0a0ee-240">**System Center 2012 Configuration Manager (bod správy, distribuční bod):**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="0a0ee-241">Správa lokality pro System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="0a0ee-241">Site Administration for System Center 2012 Configuration Manager</span></span>](https://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="0a0ee-242">Na jednom webu nástroje Configuration Manager plánování a nasazení</span><span class="sxs-lookup"><span data-stu-id="0a0ee-242">Configuration Manager Single Site Planning and Deployment</span></span>](https://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="0a0ee-243">**Klient System Center 2012 Configuration Manager pro počítače s Windows:**</span><span class="sxs-lookup"><span data-stu-id="0a0ee-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="0a0ee-244">Nasazení klientů pro System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="0a0ee-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="0a0ee-245">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="0a0ee-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="0a0ee-246">Umístění souborů protokolu</span><span class="sxs-lookup"><span data-stu-id="0a0ee-246">Log file locations</span></span>  
 <span data-ttu-id="0a0ee-247">Následující soubory protokolu jsou generovány během instalace rozhraní .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-247">The following log files are generated during .NET Framework setup:</span></span>  
  
 <span data-ttu-id="0a0ee-248">%temp%\Microsoft rozhraní .NET framework *verze*\*txt</span><span class="sxs-lookup"><span data-stu-id="0a0ee-248">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>  
 <span data-ttu-id="0a0ee-249">%temp%\Microsoft rozhraní .NET framework *verze*\*HTML</span><span class="sxs-lookup"><span data-stu-id="0a0ee-249">%temp%\Microsoft .NET Framework *version*\*.html</span></span>  
  
 <span data-ttu-id="0a0ee-250">kde *verze* je verze rozhraní .NET Framework, které chcete instalovat, jako je například 4.5 nebo 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-250">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>  
 
 <span data-ttu-id="0a0ee-251">Můžete také zadat adresář, do protokolu, které soubory jsou zapsány pomocí `/log` možnost příkazového řádku v příkazu instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-251">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="0a0ee-252">Další informace najdete v tématu [rozhraní .NET Framework – Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-252">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span> 
 
 <span data-ttu-id="0a0ee-253">Můžete použít [nástroj pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) shromažďovat soubory protokolů rozhraní .NET Framework a vytvořte komprimovaný soubor CAB (.cab) soubor, který redukuje velikost souborů.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-253">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="0a0ee-254">Návratové kódy</span><span class="sxs-lookup"><span data-stu-id="0a0ee-254">Return codes</span></span>  
 <span data-ttu-id="0a0ee-255">Následující tabulka obsahuje nejběžnější návratové kódy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalačního programu opětovné distribuce.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-255">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="0a0ee-256">Návratové kódy jsou stejné pro všechny verze instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-256">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="0a0ee-257">Odkazy na podrobné informace najdete v další části [kódy chyb stahování](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="0a0ee-257">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="0a0ee-258">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="0a0ee-258">Return code</span></span>|<span data-ttu-id="0a0ee-259">Popis</span><span class="sxs-lookup"><span data-stu-id="0a0ee-259">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0a0ee-260">0</span><span class="sxs-lookup"><span data-stu-id="0a0ee-260">0</span></span>|<span data-ttu-id="0a0ee-261">Instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-261">Installation completed successfully.</span></span>|  
|<span data-ttu-id="0a0ee-262">1602</span><span class="sxs-lookup"><span data-stu-id="0a0ee-262">1602</span></span>|<span data-ttu-id="0a0ee-263">Instalace byla zrušena uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-263">The user canceled installation.</span></span>|  
|<span data-ttu-id="0a0ee-264">1603</span><span class="sxs-lookup"><span data-stu-id="0a0ee-264">1603</span></span>|<span data-ttu-id="0a0ee-265">Při instalaci došlo k závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-265">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="0a0ee-266">1641</span><span class="sxs-lookup"><span data-stu-id="0a0ee-266">1641</span></span>|<span data-ttu-id="0a0ee-267">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="0a0ee-268">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-268">This message indicates success.</span></span>|  
|<span data-ttu-id="0a0ee-269">3010</span><span class="sxs-lookup"><span data-stu-id="0a0ee-269">3010</span></span>|<span data-ttu-id="0a0ee-270">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-270">A restart is required to complete the installation.</span></span> <span data-ttu-id="0a0ee-271">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-271">This message indicates success.</span></span>|  
|<span data-ttu-id="0a0ee-272">5100</span><span class="sxs-lookup"><span data-stu-id="0a0ee-272">5100</span></span>|<span data-ttu-id="0a0ee-273">Počítač uživatele nesplňuje požadavky systému.</span><span class="sxs-lookup"><span data-stu-id="0a0ee-273">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="0a0ee-274">Kódy chyb stahování</span><span class="sxs-lookup"><span data-stu-id="0a0ee-274">Download error codes</span></span>  
  
-   [<span data-ttu-id="0a0ee-275">Kódy chyb služby Background Intelligent Transfer Service (BITS)</span><span class="sxs-lookup"><span data-stu-id="0a0ee-275">Background Intelligent Transfer Service (BITS) error codes</span></span>](https://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="0a0ee-276">Kódy chyb monikeru URL:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-276">URL moniker error codes</span></span>](https://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="0a0ee-277">Kódy chyb služby WinHttp</span><span class="sxs-lookup"><span data-stu-id="0a0ee-277">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)  
  
 <span data-ttu-id="0a0ee-278">Další kódy chyb:</span><span class="sxs-lookup"><span data-stu-id="0a0ee-278">Other error codes:</span></span>  
  
-   [<span data-ttu-id="0a0ee-279">Kódy chyb Instalační služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="0a0ee-279">Windows Installer error codes</span></span>](https://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="0a0ee-280">Výsledné kódy agenta služby Windows Update</span><span class="sxs-lookup"><span data-stu-id="0a0ee-280">Windows Update Agent result codes</span></span>](https://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="0a0ee-281">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a0ee-281">See Also</span></span>  
 [<span data-ttu-id="0a0ee-282">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0a0ee-282">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="0a0ee-283">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="0a0ee-283">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
