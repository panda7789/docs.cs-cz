---
title: ".NET Framework – průvodce nasazením pro administrátory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: "40"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3af5e301e57350b72ac0ea50448c7a46ca6c5387
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="03c70-102">.NET Framework – průvodce nasazením pro administrátory</span><span class="sxs-lookup"><span data-stu-id="03c70-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="03c70-103">Tento článek podrobně popisuje, jak můžete nasadit správce systému [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a jeho závislé součásti systému přes síť pomocí Microsoft System Center Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="03c70-104">V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="03c70-105">Seznam softwarové a hardwarové požadavky pro instalaci [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], najdete v části [požadavky na systém](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03c70-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03c70-106">Software v tomto dokumentu, včetně, ale bez omezení, odkazuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager a služby Active Directory, jsou všechny vztahují licenční podmínky a ujednání.</span><span class="sxs-lookup"><span data-stu-id="03c70-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="03c70-107">V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je.</span><span class="sxs-lookup"><span data-stu-id="03c70-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="03c70-108">Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.</span><span class="sxs-lookup"><span data-stu-id="03c70-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="03c70-109">Informace o podpoře pro rozhraní .NET Framework najdete v tématu [podporu zásadách životního cyklu Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) na webu Microsoft Support.</span><span class="sxs-lookup"><span data-stu-id="03c70-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="03c70-110">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="03c70-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="03c70-111">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="03c70-111">The deployment process</span></span>](#the_deployment_process)  
 [<span data-ttu-id="03c70-112">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03c70-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)  
 [<span data-ttu-id="03c70-113">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="03c70-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="03c70-114">Vytvoření balíčku a programu</span><span class="sxs-lookup"><span data-stu-id="03c70-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="03c70-115">Vyberte distribuční bod</span><span class="sxs-lookup"><span data-stu-id="03c70-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="03c70-116">Nasazení balíčku</span><span class="sxs-lookup"><span data-stu-id="03c70-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="03c70-117">Prostředky</span><span class="sxs-lookup"><span data-stu-id="03c70-117">Resources</span></span>](#resources)  
[<span data-ttu-id="03c70-118">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="03c70-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="03c70-119">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="03c70-119">The deployment process</span></span>  
 <span data-ttu-id="03c70-120">Pokud je k dispozici podpůrná infrastruktura, lze distribuovatelný balíček rozhraní .NET Framework nasadit na počítače v síti pomocí nástroje System Center 2012 Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="03c70-121">Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.</span><span class="sxs-lookup"><span data-stu-id="03c70-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="03c70-122">**Kolekce** jsou skupiny prostředků nástroje Configuration Manager, jako jsou uživatelé, skupiny uživatelů nebo počítačů, na kterých je nasazená rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="03c70-123">Další informace najdete v tématu [kolekce v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-123">For more information, see [Collections in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="03c70-124">**Balíčky a programy** obvykle představují softwarové aplikace k instalaci na klientském počítači, ale může také obsahovat jednotlivé soubory, aktualizace nebo i jednotlivé příkazy.</span><span class="sxs-lookup"><span data-stu-id="03c70-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="03c70-125">Další informace najdete v tématu [balíčků a programů v nástroji Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-125">For more information, see [Packages and Programs in Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="03c70-126">**Distribuční body** lokality nástroje Configuration Manager jsou role systému, které obsahují soubory potřebné pro ke spuštění softwaru na klientských počítačích.</span><span class="sxs-lookup"><span data-stu-id="03c70-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="03c70-127">Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="03c70-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="03c70-128">Další informace najdete v tématu [Úvod do správy obsahu v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-128">For more information, see [Introduction to content Management in Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="03c70-129">**Nasazení** požádejte použít členy zadané cílové kolekce k instalaci balíčku softwaru.</span><span class="sxs-lookup"><span data-stu-id="03c70-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="03c70-130">Další informace najdete v tématu [nasazení aplikací v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-130">For more information, see [How to Deploy Applications in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03c70-131">Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení.</span><span class="sxs-lookup"><span data-stu-id="03c70-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="03c70-132">Další možnosti nasazení nástroje Configuration Manager najdete v tématu [knihovně dokumentace nástroje Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="03c70-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](http://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="03c70-133">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03c70-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="03c70-134">Můžete nasadit tichou instalaci produktu System Center 2012 Configuration Manager [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kde uživatelé nespolupracuje s proces instalace.</span><span class="sxs-lookup"><span data-stu-id="03c70-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="03c70-135">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="03c70-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="03c70-136">[Vytvořte kolekci](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="03c70-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="03c70-137">[Vytvoření balíčku a programu pro rozhraní .NET Framework redistributable](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="03c70-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="03c70-138">[Vyberte distribuční bod](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="03c70-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="03c70-139">[Nasazení balíčku](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="03c70-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="03c70-140">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="03c70-140">Create a collection</span></span>  
 <span data-ttu-id="03c70-141">V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení.</span><span class="sxs-lookup"><span data-stu-id="03c70-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="03c70-142">Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií).</span><span class="sxs-lookup"><span data-stu-id="03c70-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="03c70-143">Další informace o pravidla členství, včetně dotazů a přímá pravidla, najdete v části [seznámení s kolekcemi v nástroji Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="03c70-144">Postup vytvoření kolekce:</span><span class="sxs-lookup"><span data-stu-id="03c70-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="03c70-145">V konzole nástroje Configuration Manager, zvolte **prostředky a Kompatibilita**.</span><span class="sxs-lookup"><span data-stu-id="03c70-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="03c70-146">V **prostředky a Kompatibilita** prostoru vyberte **kolekce zařízení**.</span><span class="sxs-lookup"><span data-stu-id="03c70-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="03c70-147">Na **Domů** ve **vytvořit** skupiny, vyberte **vytvořit kolekci zařízení**.</span><span class="sxs-lookup"><span data-stu-id="03c70-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="03c70-148">Na **Obecné** stránky **Průvodce vytvořením kolekce zařízení**, zadejte název kolekce.</span><span class="sxs-lookup"><span data-stu-id="03c70-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="03c70-149">Zvolte **Procházet** určit limitující kolekci.</span><span class="sxs-lookup"><span data-stu-id="03c70-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="03c70-150">Na **pravidla členství** vyberte **přidat pravidlo**a potom zvolte **přímého pravidla** otevřete **přímé členství v Průvodci vytvořením pravidla**.</span><span class="sxs-lookup"><span data-stu-id="03c70-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="03c70-151">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="03c70-152">Na **hledat prostředky** stránky v **Třída prostředků** vyberte **systémový prostředek**.</span><span class="sxs-lookup"><span data-stu-id="03c70-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="03c70-153">V **název atributu** vyberte **název**.</span><span class="sxs-lookup"><span data-stu-id="03c70-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="03c70-154">V **hodnotu** zadejte `%`a potom zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="03c70-155">Na **vyberte prostředky** stránky, zaškrtněte políčko pro každý počítač, který chcete nasadit rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="03c70-156">Zvolte **Další**a pak dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="03c70-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="03c70-157">Na **pravidla členství** stránky **Průvodce vytvořením kolekce zařízení**, zvolte **Další**a pak dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="03c70-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="03c70-158">Další informace o kolekcích najdete v tématu [kolekce v nástroji Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-158">For more information about collections, see [Collections in Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="03c70-159">Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="03c70-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="03c70-160">Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="03c70-161">Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.</span><span class="sxs-lookup"><span data-stu-id="03c70-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="03c70-162">Postup vytvoření balíčku:</span><span class="sxs-lookup"><span data-stu-id="03c70-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="03c70-163">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**...</span><span class="sxs-lookup"><span data-stu-id="03c70-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="03c70-164">V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="03c70-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="03c70-165">Na **Domů** ve **vytvořit** skupiny, vyberte **vytvořit balíček**.</span><span class="sxs-lookup"><span data-stu-id="03c70-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="03c70-166">Na **balíček** stránky **Průvodce vytvoření balíčku a programu**, zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="03c70-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="03c70-167">Jméno:`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="03c70-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="03c70-168">Výrobce:`Microsoft`</span><span class="sxs-lookup"><span data-stu-id="03c70-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="03c70-169">Jazyk.</span><span class="sxs-lookup"><span data-stu-id="03c70-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="03c70-170">Zvolte **tento balíček obsahuje zdrojové soubory**a potom zvolte **Procházet** vybrat místní nebo síťové složky, která obsahuje instalační soubory rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="03c70-171">Pokud jste vybrali složce, vyberte **OK**a potom zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="03c70-172">Na **typ programu** stránky v průvodci vyberte **standardní Program**a potom vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="03c70-173">Na **programu** stránky **Průvodce vytvoření balíčku a programu**, zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="03c70-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="03c70-174">**Název:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="03c70-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="03c70-175">**Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (Možnosti příkazového řádku jsou popsané v tabulce po provedení těchto kroků)</span><span class="sxs-lookup"><span data-stu-id="03c70-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="03c70-176">**Spustit:** zvolte **skryté**.</span><span class="sxs-lookup"><span data-stu-id="03c70-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="03c70-177">**Program lze spustit:** zvolte možnost, která určuje, zda může program spustit, bez ohledu na to, zda je přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="03c70-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="03c70-178">Na **požadavky** vyberte **Další** přijmout výchozí hodnoty a pak dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="03c70-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="03c70-179">Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.</span><span class="sxs-lookup"><span data-stu-id="03c70-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="03c70-180">Možnost</span><span class="sxs-lookup"><span data-stu-id="03c70-180">Option</span></span>|<span data-ttu-id="03c70-181">Popis</span><span class="sxs-lookup"><span data-stu-id="03c70-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="03c70-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="03c70-182">**/q**</span></span>|<span data-ttu-id="03c70-183">Nastaví tichý režim.</span><span class="sxs-lookup"><span data-stu-id="03c70-183">Sets quiet mode.</span></span> <span data-ttu-id="03c70-184">Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="03c70-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="03c70-185">**/ norestart**</span><span class="sxs-lookup"><span data-stu-id="03c70-185">**/norestart**</span></span>|<span data-ttu-id="03c70-186">Zabrání instalačnímu programu v automatickém restartování.</span><span class="sxs-lookup"><span data-stu-id="03c70-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="03c70-187">Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="03c70-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="03c70-188">**/chainingpackage** *název balíčku*</span><span class="sxs-lookup"><span data-stu-id="03c70-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="03c70-189">Určuje název balíčku, který provádí řetězení.</span><span class="sxs-lookup"><span data-stu-id="03c70-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="03c70-190">Tyto informace, se použije v hlášení Další informace o instalaci relace pro ty, kteří si zaregistrovali [Microsoft zkušeností zlepšování Program uživatelů (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="03c70-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="03c70-191">Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače; Příklad: **/chainingpackage "Řetězení produkt"**.</span><span class="sxs-lookup"><span data-stu-id="03c70-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="03c70-192">Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="03c70-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="03c70-193">Program provede nasazení tiché instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="03c70-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="03c70-194">Při tiché instalaci uživatelé nespolupracuje s proces instalace a k získání návratového kódu a zpracovat restartování; má řetězení aplikace v tématu [získávání informace o průběhu z instalačního balíku](http://go.microsoft.com/fwlink/?LinkId=179606).</span><span class="sxs-lookup"><span data-stu-id="03c70-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](http://go.microsoft.com/fwlink/?LinkId=179606).</span></span>  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="03c70-195">Výběr distribučního bodu</span><span class="sxs-lookup"><span data-stu-id="03c70-195">Select a distribution point</span></span>  
 <span data-ttu-id="03c70-196">Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.</span><span class="sxs-lookup"><span data-stu-id="03c70-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="03c70-197">Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:</span><span class="sxs-lookup"><span data-stu-id="03c70-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="03c70-198">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="03c70-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="03c70-199">V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="03c70-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="03c70-200">Seznam balíčků, vyberte balíček **rozhraní .NET Framework 4.5** kterou jste vytvořili v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="03c70-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="03c70-201">Na **Domů** ve **nasazení** skupiny, vyberte **distribuovat obsah**.</span><span class="sxs-lookup"><span data-stu-id="03c70-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="03c70-202">Na **Obecné** kartě **Průvodce distribucí obsahu**, zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="03c70-203">Na **cílové umístění obsahu** stránku průvodce, zvolte **přidat**a potom zvolte **distribuční bod**.</span><span class="sxs-lookup"><span data-stu-id="03c70-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="03c70-204">V **přidat distribuční body** dialogovém okně vyberte distribuční body, který bude hostitelem balíčku a programu a potom zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="03c70-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="03c70-205">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="03c70-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="03c70-206">Packagenow obsahuje všechny informace, které potřebujete k bezobslužné nasazení rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="03c70-206">The packagenow contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="03c70-207">Před nasazením balíčku a programu, ověřte, zda byl nainstalován v distribučním bodě; najdete v části "Monitorování obsah" [operace a údržba pro správu obsahu v nástroji Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) v knihovně dokumentace nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="03c70-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="03c70-208">Nasazení balíčku</span><span class="sxs-lookup"><span data-stu-id="03c70-208">Deploy the package</span></span>  
 <span data-ttu-id="03c70-209">Postup nasazení balíčku a programu .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="03c70-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="03c70-210">V konzole nástroje Configuration Manager, zvolte **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="03c70-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="03c70-211">V **softwarová knihovna** pracovního prostoru, rozbalte položku **Správa aplikací**a potom zvolte **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="03c70-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="03c70-212">Seznam balíčků, vyberte balíček, který jste vytvořili pojmenované **rozhraní .NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="03c70-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="03c70-213">Na **Domů** ve **nasazení** skupiny, vyberte **nasadit**.</span><span class="sxs-lookup"><span data-stu-id="03c70-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="03c70-214">Na **Obecné** stránky **Průvodce nasazením softwaru**, zvolte **Procházet**a potom vyberte kolekci, kterou jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="03c70-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="03c70-215">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="03c70-216">Na **obsahu** stránku průvodce, ověřte, zda se zobrazí bod, ze kterého chcete distribuovat software a potom zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="03c70-217">Na **nastavení nasazení** stránku průvodce, potvrďte, že **akce** je nastaven na **nainstalovat**, a **účel** je nastaven na **Požadované**.</span><span class="sxs-lookup"><span data-stu-id="03c70-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="03c70-218">Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="03c70-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="03c70-219">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="03c70-220">Na **plánování** stránku průvodce, určete, kdy má být nainstalované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c70-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="03c70-221">Můžete zvolit **nový** pro přiřazení času instalace, nebo instruovat software, který chcete nainstalovat, když se uživatel přihlásí na nebo vypnutí nebo co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="03c70-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="03c70-222">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="03c70-223">Na **činnost koncového uživatele** stránce průvodce, použijte výchozí hodnoty a zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="03c70-224">Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení.</span><span class="sxs-lookup"><span data-stu-id="03c70-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="03c70-225">Informace o těchto možnostech najdete v tématu [oznámení o inzerovaném programu název vlastnosti: kartu plán](http://technet.microsoft.com/library/bb694016.aspx) v knihovně TechNet.</span><span class="sxs-lookup"><span data-stu-id="03c70-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](http://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="03c70-226">Na **distribuční body** stránce průvodce, použijte výchozí hodnoty a zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="03c70-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="03c70-227">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="03c70-227">Complete the wizard.</span></span> <span data-ttu-id="03c70-228">Můžete sledovat průběh nasazení v **nasazení** uzlu **monitorování** pracovního prostoru.</span><span class="sxs-lookup"><span data-stu-id="03c70-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="03c70-229">Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="03c70-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="03c70-230">Informace o kódy chyb instalace rozhraní .NET Framework 4.5, najdete v článku [návratové kódy](#return_codes) později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="03c70-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="03c70-231">Prostředky</span><span class="sxs-lookup"><span data-stu-id="03c70-231">Resources</span></span>  
 <span data-ttu-id="03c70-232">Další informace o infrastrukturu pro testování nasazení [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Distribuovatelný balíček, najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="03c70-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="03c70-233">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="03c70-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="03c70-234">Active Directory Domain Services pro systém Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="03c70-234">Active Directory Domain Services for Windows Server 2008</span></span>](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="03c70-235">DNS Server</span><span class="sxs-lookup"><span data-stu-id="03c70-235">DNS Server</span></span>](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="03c70-236">DHCP Server</span><span class="sxs-lookup"><span data-stu-id="03c70-236">DHCP Server</span></span>](http://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="03c70-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="03c70-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="03c70-238">Instalace systému SQL Server 2008 (Video serveru SQL Server)</span><span class="sxs-lookup"><span data-stu-id="03c70-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="03c70-239">Přehled zabezpečení SQL Server 2008 pro správce databáze</span><span class="sxs-lookup"><span data-stu-id="03c70-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="03c70-240">**System Center 2012 Configuration Manager (bod správy, distribuční bod):**</span><span class="sxs-lookup"><span data-stu-id="03c70-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="03c70-241">Správa lokality pro nástroj System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="03c70-241">Site Administration for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="03c70-242">Lokality nástroje Configuration Manager jedním plánování a nasazení</span><span class="sxs-lookup"><span data-stu-id="03c70-242">Configuration Manager Single Site Planning and Deployment</span></span>](http://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="03c70-243">**System Center 2012 Configuration Manager klienta pro počítače se systémem Windows:**</span><span class="sxs-lookup"><span data-stu-id="03c70-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="03c70-244">Nasazení klientů pro nástroj System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="03c70-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="03c70-245">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="03c70-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="03c70-246">Umístění souborů protokolu</span><span class="sxs-lookup"><span data-stu-id="03c70-246">Log file locations</span></span>  
 <span data-ttu-id="03c70-247">Následující soubory protokolu jsou generována během [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalace:</span><span class="sxs-lookup"><span data-stu-id="03c70-247">The following log files are generated during [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup:</span></span>  
  
 <span data-ttu-id="03c70-248">%temp%\Microsoft .NET Framework 4.5*.txt</span><span class="sxs-lookup"><span data-stu-id="03c70-248">%temp%\Microsoft .NET Framework 4.5*.txt</span></span>  
 <span data-ttu-id="03c70-249">%temp%\Microsoft rozhraní .NET framework 4.5\*.html</span><span class="sxs-lookup"><span data-stu-id="03c70-249">%temp%\Microsoft .NET Framework 4.5\*.html</span></span>  
  
 <span data-ttu-id="03c70-250">Můžete použít [nástroj kolekce protokol](http://www.microsoft.com/download/details.aspx?id=12493) ke shromažďování [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] soubory protokolu a k vytvoření souboru komprimovaný soubor CAB (.cab), která snižuje velikost souborů.</span><span class="sxs-lookup"><span data-stu-id="03c70-250">You can use the [log collection tool](http://www.microsoft.com/download/details.aspx?id=12493) to collect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="03c70-251">Návratové kódy</span><span class="sxs-lookup"><span data-stu-id="03c70-251">Return codes</span></span>  
 <span data-ttu-id="03c70-252">Následující tabulka uvádí nejběžnější návratové kódy z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable instalační program.</span><span class="sxs-lookup"><span data-stu-id="03c70-252">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="03c70-253">Návratové kódy jsou stejné pro všechny verze instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="03c70-253">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="03c70-254">Odkazy na podrobné informace naleznete v části Další [stáhnout kódy chyb](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="03c70-254">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="03c70-255">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="03c70-255">Return code</span></span>|<span data-ttu-id="03c70-256">Popis</span><span class="sxs-lookup"><span data-stu-id="03c70-256">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="03c70-257">0</span><span class="sxs-lookup"><span data-stu-id="03c70-257">0</span></span>|<span data-ttu-id="03c70-258">Instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="03c70-258">Installation completed successfully.</span></span>|  
|<span data-ttu-id="03c70-259">1602</span><span class="sxs-lookup"><span data-stu-id="03c70-259">1602</span></span>|<span data-ttu-id="03c70-260">Instalace byla zrušena uživatelem.</span><span class="sxs-lookup"><span data-stu-id="03c70-260">The user canceled installation.</span></span>|  
|<span data-ttu-id="03c70-261">1603</span><span class="sxs-lookup"><span data-stu-id="03c70-261">1603</span></span>|<span data-ttu-id="03c70-262">Při instalaci došlo k závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="03c70-262">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="03c70-263">1641</span><span class="sxs-lookup"><span data-stu-id="03c70-263">1641</span></span>|<span data-ttu-id="03c70-264">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="03c70-264">A restart is required to complete the installation.</span></span> <span data-ttu-id="03c70-265">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="03c70-265">This message indicates success.</span></span>|  
|<span data-ttu-id="03c70-266">3010</span><span class="sxs-lookup"><span data-stu-id="03c70-266">3010</span></span>|<span data-ttu-id="03c70-267">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="03c70-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="03c70-268">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="03c70-268">This message indicates success.</span></span>|  
|<span data-ttu-id="03c70-269">5100</span><span class="sxs-lookup"><span data-stu-id="03c70-269">5100</span></span>|<span data-ttu-id="03c70-270">Počítač uživatele nesplňuje požadavky systému.</span><span class="sxs-lookup"><span data-stu-id="03c70-270">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="03c70-271">Kódy chyb stahování</span><span class="sxs-lookup"><span data-stu-id="03c70-271">Download error codes</span></span>  
  
-   [<span data-ttu-id="03c70-272">Kódy chyb Background Intelligent Transfer Service (BITS)</span><span class="sxs-lookup"><span data-stu-id="03c70-272">Background Intelligent Transfer Service (BITS) error codes</span></span>](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="03c70-273">Adresa URL Přezdívka chybové kódy</span><span class="sxs-lookup"><span data-stu-id="03c70-273">URL moniker error codes</span></span>](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="03c70-274">Kódy chyb WinHttp</span><span class="sxs-lookup"><span data-stu-id="03c70-274">WinHttp error codes</span></span>](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 <span data-ttu-id="03c70-275">Další kódy chyb:</span><span class="sxs-lookup"><span data-stu-id="03c70-275">Other error codes:</span></span>  
  
-   [<span data-ttu-id="03c70-276">Kódy chyb Instalační služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="03c70-276">Windows Installer error codes</span></span>](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="03c70-277">Kódy výsledků agenta Windows Update Agent</span><span class="sxs-lookup"><span data-stu-id="03c70-277">Windows Update Agent result codes</span></span>](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="03c70-278">Viz také</span><span class="sxs-lookup"><span data-stu-id="03c70-278">See Also</span></span>  
 [<span data-ttu-id="03c70-279">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="03c70-279">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="03c70-280">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="03c70-280">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
