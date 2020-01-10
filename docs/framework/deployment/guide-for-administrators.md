---
title: .NET Framework – průvodce nasazením pro administrátory
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716529"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="183f4-102">.NET Framework – průvodce nasazením pro administrátory</span><span class="sxs-lookup"><span data-stu-id="183f4-102">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="183f4-103">V tomto podrobném článku se dozvíte, jak může správce systému nasadit .NET Framework 4,5 a jeho systémové závislosti v síti pomocí služby Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-103">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="183f4-104">V tomto článku se předpokládá, že všechny cílové klientské počítače splňují minimální požadavky rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="183f4-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="183f4-105">Seznam požadavků na software a hardware pro instalaci .NET Framework 4,5 najdete v tématu [požadavky na systém](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="183f4-105">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="183f4-106">Software odkazovaný v tomto dokumentu, včetně, bez omezení, .NET Framework 4,5, Configuration Manager a Active Directory, podléhá licenčním podmínkám a podmínkám.</span><span class="sxs-lookup"><span data-stu-id="183f4-106">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="183f4-107">V těchto pokynech se předpokládá, že nabyvatel licence k softwaru si tyto licenční podmínky přečetl a schválil je.</span><span class="sxs-lookup"><span data-stu-id="183f4-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="183f4-108">Tyto pokyny neodporují žádné z podmínek takovýchto licenčních smluv.</span><span class="sxs-lookup"><span data-stu-id="183f4-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="183f4-109">Informace o podpoře pro .NET Framework najdete v článku [.NET Framework oficiální zásady podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) na webu Podpora Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="183f4-109">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="183f4-110">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="183f4-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="183f4-111">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="183f4-111">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="183f4-112">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="183f4-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="183f4-113">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="183f4-113">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="183f4-114">Vytvoření balíčku a programu</span><span class="sxs-lookup"><span data-stu-id="183f4-114">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="183f4-115">Vyberte distribuční bod</span><span class="sxs-lookup"><span data-stu-id="183f4-115">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="183f4-116">Nasadit balíček</span><span class="sxs-lookup"><span data-stu-id="183f4-116">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="183f4-117">Prostředky</span><span class="sxs-lookup"><span data-stu-id="183f4-117">Resources</span></span>](#resources)
- [<span data-ttu-id="183f4-118">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="183f4-118">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="183f4-119">Proces nasazení</span><span class="sxs-lookup"><span data-stu-id="183f4-119">The deployment process</span></span>

<span data-ttu-id="183f4-120">Pokud máte nasazenou podpůrnou infrastrukturu, použijte Configuration Manager k nasazení .NET Framework Distribuovatelný balíček do počítačů v síti.</span><span class="sxs-lookup"><span data-stu-id="183f4-120">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="183f4-121">Vybudování infrastruktury zahrnuje vytvoření a definování pěti klíčových oblastí: kolekce, balíčku pro software, programu pro software, distribučních bodů a nasazení.</span><span class="sxs-lookup"><span data-stu-id="183f4-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="183f4-122">**Kolekce** jsou skupiny Configuration Manager prostředků, jako jsou uživatelé, skupiny uživatelů nebo počítače, do kterých se .NET Framework nasadí.</span><span class="sxs-lookup"><span data-stu-id="183f4-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="183f4-123">Další informace najdete v tématu [Úvod do kolekcí v Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-123">For more information, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="183f4-124">**Balíčky a programy** obvykle představují softwarové aplikace, které mají být nainstalovány v klientském počítači, ale mohou obsahovat také jednotlivé soubory, aktualizace nebo dokonce jednotlivé příkazy.</span><span class="sxs-lookup"><span data-stu-id="183f4-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="183f4-125">Další informace najdete v tématu [balíčky a programy v Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) v knihovně dokumentace Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-125">For more information, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="183f4-126">**Distribuční body** jsou Configuration Manager role systému lokality, které ukládají soubory požadované pro spuštění softwaru na klientských počítačích.</span><span class="sxs-lookup"><span data-stu-id="183f4-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="183f4-127">Pokud klient Správce konfigurace přijme a zpracuje nasazení softwaru, kontaktuje distribuční bod za účelem stažení obsahu spojeného s tímto softwarem a spuštění procesu instalace.</span><span class="sxs-lookup"><span data-stu-id="183f4-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="183f4-128">Další informace najdete v tématu [základní koncepty správy obsahu v Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) v knihovně dokumentace Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-128">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="183f4-129">**Nasazení** instruují příslušné členy zadané cílové kolekce k instalaci softwarového balíčku.</span><span class="sxs-lookup"><span data-stu-id="183f4-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="183f4-130">Postupy uvedené v tomto tématu obsahují typická nastavení pro vytváření a nasazení balíčku a programu a nemusí zahrnovat všechna možná nastavení.</span><span class="sxs-lookup"><span data-stu-id="183f4-130">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="183f4-131">Další možnosti nasazení Configuration Manager najdete v [knihovně dokumentace Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="183f4-131">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="183f4-132">Nasazení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="183f4-132">Deploying the .NET Framework</span></span>

<span data-ttu-id="183f4-133">Configuration Manager můžete použít k nasazení tiché instalace .NET Framework 4,5, kde uživatelé nepracují s procesem instalace.</span><span class="sxs-lookup"><span data-stu-id="183f4-133">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="183f4-134">Postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="183f4-134">Follow these steps:</span></span>

1. <span data-ttu-id="183f4-135">[Vytvořte kolekci](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="183f4-135">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="183f4-136">[Vytvořte balíček a program pro .NET Framework redistributable](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="183f4-136">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="183f4-137">[Vyberte distribuční bod](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="183f4-137">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="183f4-138">[Nasaďte balíček](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="183f4-138">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="183f4-139">Vytvoření kolekce</span><span class="sxs-lookup"><span data-stu-id="183f4-139">Create a collection</span></span>

<span data-ttu-id="183f4-140">V tomto kroku vyberte počítače, na které chcete balíček a program nasadit, a seskupte je do kolekce zařízení.</span><span class="sxs-lookup"><span data-stu-id="183f4-140">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="183f4-141">Chcete-li vytvořit kolekci v nástroji Správce konfigurace, můžete použít pravidla přímého členství (kde členy kolekce zadáte ručně) nebo pravidla dotazů (kde členy kolekce určí nástroj Správce konfigurace podle zadaných kritérií).</span><span class="sxs-lookup"><span data-stu-id="183f4-141">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="183f4-142">Další informace o pravidlech členství, včetně dotazů a přímých pravidel, najdete v tématu [Úvod do kolekcí v Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) v knihovně dokumentace Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-142">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="183f4-143">Postup vytvoření kolekce:</span><span class="sxs-lookup"><span data-stu-id="183f4-143">To create a collection:</span></span>

1. <span data-ttu-id="183f4-144">V konzole Configuration Manager vyberte **prostředky a kompatibilita**.</span><span class="sxs-lookup"><span data-stu-id="183f4-144">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="183f4-145">V pracovním prostoru **prostředky a kompatibilita** vyberte **kolekce zařízení**.</span><span class="sxs-lookup"><span data-stu-id="183f4-145">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="183f4-146">Na kartě **Domů** ve skupině **vytvořit** vyberte možnost **vytvořit kolekci zařízení**.</span><span class="sxs-lookup"><span data-stu-id="183f4-146">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="183f4-147">Na stránce **Obecné** v **Průvodci vytvořením kolekce zařízení**zadejte název kolekce.</span><span class="sxs-lookup"><span data-stu-id="183f4-147">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="183f4-148">Zvolte **Procházet** a zadejte omezující kolekci.</span><span class="sxs-lookup"><span data-stu-id="183f4-148">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="183f4-149">Na stránce **pravidla členství** zvolte možnost **Přidat pravidlo**a pak zvolte možnost **přímé pravidlo** . otevře se **Průvodce vytvořením pravidla přímého členství**.</span><span class="sxs-lookup"><span data-stu-id="183f4-149">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="183f4-150">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-150">Choose **Next**.</span></span>

7. <span data-ttu-id="183f4-151">Na stránce **Hledat prostředky** v seznamu **Třída prostředků** vyberte položku **systémový prostředek**.</span><span class="sxs-lookup"><span data-stu-id="183f4-151">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="183f4-152">V seznamu **název atributu** vyberte možnost **název**.</span><span class="sxs-lookup"><span data-stu-id="183f4-152">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="183f4-153">Do pole **hodnota** zadejte `%`a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-153">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="183f4-154">Na stránce **vybrat prostředky** zaškrtněte políčko u každého počítače, do kterého chcete nasadit .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="183f4-154">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="183f4-155">Klikněte na tlačítko **Další**a dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="183f4-155">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="183f4-156">Na stránce **pravidla členství** v **Průvodci vytvořením kolekce zařízení**klikněte na tlačítko **Další**a dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="183f4-156">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="183f4-157">Vytvoření balíčku a programu pro distribuovatelný balíček rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="183f4-157">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="183f4-158">Podle následujících kroků můžete ručně vytvořit distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="183f4-158">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="183f4-159">Balíček obsahuje konkrétní parametry pro instalaci rozhraní .NET Framework a umístění, ze kterých bude balíček distribuován cílovým počítačům.</span><span class="sxs-lookup"><span data-stu-id="183f4-159">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="183f4-160">Postup vytvoření balíčku:</span><span class="sxs-lookup"><span data-stu-id="183f4-160">To create a package:</span></span>

1. <span data-ttu-id="183f4-161">V konzole Configuration Manager vyberte možnost **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="183f4-161">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="183f4-162">V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="183f4-162">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="183f4-163">Na kartě **Domů** ve skupině **vytvořit** klikněte na možnost **vytvořit balíček**.</span><span class="sxs-lookup"><span data-stu-id="183f4-163">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="183f4-164">Na stránce **balíček** v **Průvodci vytvořením balíčku a programu**zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="183f4-164">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="183f4-165">Název: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="183f4-165">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="183f4-166">Výrobce: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="183f4-166">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="183f4-167">Jazyk.</span><span class="sxs-lookup"><span data-stu-id="183f4-167">Language.</span></span> `English (US)`

5. <span data-ttu-id="183f4-168">Zvolte **Tento balíček obsahuje zdrojové soubory**a pak zvolte **Procházet** a vyberte místní nebo síťovou složku, která obsahuje instalační soubory .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="183f4-168">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="183f4-169">Po výběru složky klikněte na **tlačítko OK**a potom na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-169">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="183f4-170">Na stránce **typ programu** v průvodci zvolte možnost **standardní program**a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-170">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="183f4-171">Na stránce **program** v **Průvodci vytvořením balíčku a programu**zadejte následující informace:</span><span class="sxs-lookup"><span data-stu-id="183f4-171">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="183f4-172">**Název:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="183f4-172">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="183f4-173">**Příkazový řádek:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (parametry příkazového řádku jsou popsány v tabulce po těchto krocích)</span><span class="sxs-lookup"><span data-stu-id="183f4-173">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="183f4-174">**Spusťte:** Vyberte **skrytý**.</span><span class="sxs-lookup"><span data-stu-id="183f4-174">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="183f4-175">**Program lze spustit:** Vyberte možnost, která určuje, zda může program běžet bez ohledu na to, zda je uživatel přihlášen.</span><span class="sxs-lookup"><span data-stu-id="183f4-175">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="183f4-176">Na stránce **požadavky** kliknutím na tlačítko **Další** přijměte výchozí hodnoty a pak dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="183f4-176">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="183f4-177">Následující tabulka popisuje možnosti příkazového řádku zadané v kroku 7.</span><span class="sxs-lookup"><span data-stu-id="183f4-177">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="183f4-178">Možnost</span><span class="sxs-lookup"><span data-stu-id="183f4-178">Option</span></span>|<span data-ttu-id="183f4-179">Popis</span><span class="sxs-lookup"><span data-stu-id="183f4-179">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="183f4-180">**/q**</span><span class="sxs-lookup"><span data-stu-id="183f4-180">**/q**</span></span>|<span data-ttu-id="183f4-181">Nastaví tichý režim.</span><span class="sxs-lookup"><span data-stu-id="183f4-181">Sets quiet mode.</span></span> <span data-ttu-id="183f4-182">Není vyžadován žádný vstup uživatele a nebude zobrazen žádný výstup.</span><span class="sxs-lookup"><span data-stu-id="183f4-182">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="183f4-183">**/ norestart /**</span><span class="sxs-lookup"><span data-stu-id="183f4-183">**/norestart**</span></span>|<span data-ttu-id="183f4-184">Zabrání instalačnímu programu v automatickém restartování.</span><span class="sxs-lookup"><span data-stu-id="183f4-184">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="183f4-185">Pokud použijete tuto možnost, musí restartování počítače zpracovat nástroj Správce konfigurace.</span><span class="sxs-lookup"><span data-stu-id="183f4-185">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="183f4-186">**/chainingpackage** – *balíček*</span><span class="sxs-lookup"><span data-stu-id="183f4-186">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="183f4-187">Určuje název balíčku, který provádí řetězení.</span><span class="sxs-lookup"><span data-stu-id="183f4-187">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="183f4-188">Tyto informace jsou hlášeny s dalšími informacemi o Instalační relaci pro ty, kteří se zaregistrovali v programu Microsoft program Zlepšování softwaru a služeb na základě zkušeností uživatelů (CEIP).</span><span class="sxs-lookup"><span data-stu-id="183f4-188">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="183f4-189">Pokud název balíčku obsahuje mezery, použijte dvojité uvozovky jako oddělovače. Příklad: **/chainingpackage "řetězení produktu"** .</span><span class="sxs-lookup"><span data-stu-id="183f4-189">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="183f4-190">Podle těchto kroků vytvoříte balíček s názvem .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="183f4-190">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="183f4-191">Program provede nasazení tiché instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="183f4-191">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="183f4-192">V tiché instalaci uživatelé nepracují s procesem instalace a zřetězená aplikace musí zachytit návratový kód a zpracovat restartování. viz [získání informací o průběhu z instalačního balíčku](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="183f4-192">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="183f4-193">Výběr distribučního bodu</span><span class="sxs-lookup"><span data-stu-id="183f4-193">Select a distribution point</span></span>

<span data-ttu-id="183f4-194">Chcete-li distribuovat balíček a program do klientských počítačů ze serveru, musíte nejdříve určit systém lokality jako distribuční bod a poté distribuovat balíček do distribučního bodu.</span><span class="sxs-lookup"><span data-stu-id="183f4-194">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="183f4-195">Pomocí následujícího postupu vyberte distribuční bod pro balíček .NET Framework 4.5, který jste vytvořili v předchozím oddílu:</span><span class="sxs-lookup"><span data-stu-id="183f4-195">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="183f4-196">V konzole Configuration Manager vyberte možnost **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="183f4-196">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="183f4-197">V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="183f4-197">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="183f4-198">V seznamu balíčků vyberte balíček **.NET Framework 4,5** , který jste vytvořili v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="183f4-198">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="183f4-199">Na kartě **Domů** ve skupině **nasazení** klikněte na možnost **distribuovat obsah**.</span><span class="sxs-lookup"><span data-stu-id="183f4-199">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="183f4-200">Na kartě **Obecné** v **Průvodci distribucí obsahu**klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-200">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="183f4-201">Na stránce **cíl obsahu** průvodce zvolte možnost **Přidat**a pak zvolte možnost **distribuční bod**.</span><span class="sxs-lookup"><span data-stu-id="183f4-201">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="183f4-202">V dialogovém okně **Přidat distribuční body** vyberte distribuční body, které budou hostovat balíček a program a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="183f4-202">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="183f4-203">Dokončete průvodce</span><span class="sxs-lookup"><span data-stu-id="183f4-203">Complete the wizard.</span></span>

<span data-ttu-id="183f4-204">Balíček nyní obsahuje všechny informace, které potřebujete pro tiché nasazení rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="183f4-204">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="183f4-205">Před nasazením balíčku a programu ověřte, zda byl nainstalován v distribučním bodě. v části monitorování stavu obsahu v tématu monitorování [obsahu, který distribuujete pomocí Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) v knihovně dokumentace Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="183f4-205">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="183f4-206">Nasazení balíčku</span><span class="sxs-lookup"><span data-stu-id="183f4-206">Deploy the package</span></span>

<span data-ttu-id="183f4-207">Postup nasazení balíčku a programu .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="183f4-207">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="183f4-208">V konzole Configuration Manager vyberte možnost **softwarová knihovna**.</span><span class="sxs-lookup"><span data-stu-id="183f4-208">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="183f4-209">V pracovním prostoru **softwarová knihovna** rozbalte položku **Správa aplikací**a pak zvolte možnost **balíčky**.</span><span class="sxs-lookup"><span data-stu-id="183f4-209">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="183f4-210">V seznamu balíčků vyberte balíček, který jste vytvořili s názvem **.NET Framework 4,5**.</span><span class="sxs-lookup"><span data-stu-id="183f4-210">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="183f4-211">Na kartě **Domů** ve skupině **nasazení** klikněte na možnost **nasadit**.</span><span class="sxs-lookup"><span data-stu-id="183f4-211">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="183f4-212">Na stránce **Obecné** v **Průvodci nasazením softwaru**klikněte na tlačítko **Procházet**a poté vyberte kolekci, kterou jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="183f4-212">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="183f4-213">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-213">Choose **Next**.</span></span>

6. <span data-ttu-id="183f4-214">Na stránce **obsah** v průvodci ověřte, zda je zobrazen bod, ze kterého chcete distribuovat software, a pak zvolte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-214">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="183f4-215">Na stránce **nastavení nasazení** v průvodci potvrďte, že **Akce** je nastavená na **instalovat**a **účel** je nastavený na **požadováno**.</span><span class="sxs-lookup"><span data-stu-id="183f4-215">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="183f4-216">Díky tomuto nastavení bude softwarový balíček nastaven jako povinná instalace na cílových počítačích.</span><span class="sxs-lookup"><span data-stu-id="183f4-216">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="183f4-217">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-217">Choose **Next**.</span></span>

8. <span data-ttu-id="183f4-218">Na stránce **plánování** v průvodci určete, kdy chcete .NET Framework nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="183f4-218">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="183f4-219">Můžete zvolit možnost **nové** a přiřadit čas instalace nebo dát pokyn k instalaci softwaru, když se uživatel přihlásí nebo vypíná nebo co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="183f4-219">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="183f4-220">Zvolte **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-220">Choose **Next**.</span></span>

9. <span data-ttu-id="183f4-221">Na stránce **činnost koncového uživatele** v průvodci použijte výchozí hodnoty a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-221">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="183f4-222">Na vaše provozní prostředí se mohou vztahovat zásady, které vyžadují jiná nastavení plánu nasazení.</span><span class="sxs-lookup"><span data-stu-id="183f4-222">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="183f4-223">Informace o těchto možnostech naleznete v tématu [Vlastnosti názvu inzerce: karta plán](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="183f4-223">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="183f4-224">Na stránce **distribuční body** v průvodci použijte výchozí hodnoty a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="183f4-224">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="183f4-225">Dokončete průvodce</span><span class="sxs-lookup"><span data-stu-id="183f4-225">Complete the wizard.</span></span> <span data-ttu-id="183f4-226">Průběh nasazení můžete sledovat v uzlu **nasazení** v pracovním prostoru **monitorování** .</span><span class="sxs-lookup"><span data-stu-id="183f4-226">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="183f4-227">Balíček bude nyní nasazen na cílenou kolekci a bude spuštěna tichá instalace rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="183f4-227">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="183f4-228">Informace o kódech chyb instalace .NET Framework 4,5 naleznete v části [návratové kódy](#return_codes) dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="183f4-228">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="183f4-229">Prostředky</span><span class="sxs-lookup"><span data-stu-id="183f4-229">Resources</span></span>

<span data-ttu-id="183f4-230">Další informace o infrastruktuře pro testování nasazení .NET Framework 4,5 Distribuovatelný balíček najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="183f4-230">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="183f4-231">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="183f4-231">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="183f4-232">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="183f4-232">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="183f4-233">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="183f4-233">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="183f4-234">Protokol DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="183f4-234">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="183f4-235">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="183f4-235">**SQL Server 2008:**</span></span>

- <span data-ttu-id="183f4-236">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="183f4-236">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="183f4-237">Přehled zabezpečení SQL Server 2008 pro správce databáze</span><span class="sxs-lookup"><span data-stu-id="183f4-237">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="183f4-238">**System Center 2012 Configuration Manager (bod správy, distribuční bod):**</span><span class="sxs-lookup"><span data-stu-id="183f4-238">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="183f4-239">Správa lokality pro nástroj System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="183f4-239">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="183f4-240">Configuration Manager plánování a nasazení v jednom webu</span><span class="sxs-lookup"><span data-stu-id="183f4-240">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="183f4-241">**Klient System Center 2012 Configuration Manager klienta pro počítače se systémem Windows:**</span><span class="sxs-lookup"><span data-stu-id="183f4-241">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="183f4-242">Nasazení klientů pro nástroj System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="183f4-242">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="183f4-243">Odstraňování problémů</span><span class="sxs-lookup"><span data-stu-id="183f4-243">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="183f4-244">Umístění souborů protokolu</span><span class="sxs-lookup"><span data-stu-id="183f4-244">Log file locations</span></span>

<span data-ttu-id="183f4-245">Během .NET Frameworkho nastavení se generují následující soubory protokolu:</span><span class="sxs-lookup"><span data-stu-id="183f4-245">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="183f4-246">%temp%\Microsoft .NET Framework *verze*\*. txt</span><span class="sxs-lookup"><span data-stu-id="183f4-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="183f4-247">%temp%\Microsoft .NET Framework *verze*\*. html</span><span class="sxs-lookup"><span data-stu-id="183f4-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="183f4-248">kde *verze* je verze .NET Framework, kterou instalujete, například 4,5 nebo 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="183f4-248">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="183f4-249">Můžete také zadat adresář, do kterého se budou zapisovat soubory protokolu, pomocí možnosti příkazového řádku `/log` v instalačním příkazu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="183f4-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="183f4-250">Další informace najdete v tématu [Průvodce nasazením .NET Framework pro vývojáře](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="183f4-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="183f4-251">[Nástroj pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) můžete použít ke shromáždění souborů protokolu .NET Framework a k vytvoření komprimovaného souboru CAB (. cab), který zmenší velikost souborů.</span><span class="sxs-lookup"><span data-stu-id="183f4-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="183f4-252">Návratové kódy</span><span class="sxs-lookup"><span data-stu-id="183f4-252">Return codes</span></span>

<span data-ttu-id="183f4-253">Následující tabulka uvádí nejběžnější návratové kódy z instalačního programu .NET Framework 4,5 Redistributable.</span><span class="sxs-lookup"><span data-stu-id="183f4-253">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="183f4-254">Návratové kódy jsou stejné pro všechny verze instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="183f4-254">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="183f4-255">Odkazy na podrobné informace naleznete v další části, [stažení kódů chyb](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="183f4-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="183f4-256">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="183f4-256">Return code</span></span>|<span data-ttu-id="183f4-257">Popis</span><span class="sxs-lookup"><span data-stu-id="183f4-257">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="183f4-258">0</span><span class="sxs-lookup"><span data-stu-id="183f4-258">0</span></span>|<span data-ttu-id="183f4-259">Instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="183f4-259">Installation completed successfully.</span></span>|
|<span data-ttu-id="183f4-260">1602</span><span class="sxs-lookup"><span data-stu-id="183f4-260">1602</span></span>|<span data-ttu-id="183f4-261">Instalace byla zrušena uživatelem.</span><span class="sxs-lookup"><span data-stu-id="183f4-261">The user canceled installation.</span></span>|
|<span data-ttu-id="183f4-262">1603</span><span class="sxs-lookup"><span data-stu-id="183f4-262">1603</span></span>|<span data-ttu-id="183f4-263">Při instalaci došlo k závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="183f4-263">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="183f4-264">1641</span><span class="sxs-lookup"><span data-stu-id="183f4-264">1641</span></span>|<span data-ttu-id="183f4-265">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="183f4-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="183f4-266">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="183f4-266">This message indicates success.</span></span>|
|<span data-ttu-id="183f4-267">3010</span><span class="sxs-lookup"><span data-stu-id="183f4-267">3010</span></span>|<span data-ttu-id="183f4-268">K dokončení instalace je nutné provést restart.</span><span class="sxs-lookup"><span data-stu-id="183f4-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="183f4-269">Tato zpráva znamená úspěch.</span><span class="sxs-lookup"><span data-stu-id="183f4-269">This message indicates success.</span></span>|
|<span data-ttu-id="183f4-270">5100</span><span class="sxs-lookup"><span data-stu-id="183f4-270">5100</span></span>|<span data-ttu-id="183f4-271">Počítač uživatele nesplňuje požadavky systému.</span><span class="sxs-lookup"><span data-stu-id="183f4-271">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="183f4-272">Kódy chyb stahování</span><span class="sxs-lookup"><span data-stu-id="183f4-272">Download error codes</span></span>

- [<span data-ttu-id="183f4-273">Kódy chyb Background Intelligent Transfer Service (BITS)</span><span class="sxs-lookup"><span data-stu-id="183f4-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="183f4-274">Kódy chyb monikeru URL</span><span class="sxs-lookup"><span data-stu-id="183f4-274">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="183f4-275">Kódy chyb služby WinHttp</span><span class="sxs-lookup"><span data-stu-id="183f4-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="183f4-276">Další kódy chyb:</span><span class="sxs-lookup"><span data-stu-id="183f4-276">Other error codes:</span></span>

- [<span data-ttu-id="183f4-277">Kódy chyb Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="183f4-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="183f4-278">[web Windows Update kódy výsledků agenta](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="183f4-278">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="183f4-279">Viz také:</span><span class="sxs-lookup"><span data-stu-id="183f4-279">See also</span></span>

- [<span data-ttu-id="183f4-280">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="183f4-280">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="183f4-281">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="183f4-281">System Requirements</span></span>](../get-started/system-requirements.md)
