---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468995"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="215ca-102">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="215ca-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="215ca-103">Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="215ca-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="215ca-104">Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="215ca-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="215ca-105">Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="215ca-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="215ca-106">Pomocí [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="215ca-106">Using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span>  
  
     <span data-ttu-id="215ca-107">V sadě Visual Studio 2012 a Visual Studio 2013 můžete tuto akci provést instalací projektu InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="215ca-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="215ca-108">Toto je doporučený a nejběžnější způsob přidávání sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="215ca-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="215ca-109">Instalační program poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.</span><span class="sxs-lookup"><span data-stu-id="215ca-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="215ca-110">Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="215ca-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="215ca-111">Nástroj Gacutil.exe slouží k přidávání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="215ca-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="215ca-112">Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="215ca-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="215ca-113">V dřívějších verzích rozhraní .NET Framework rozšíření prostředí Shfusion.dll Windows povolit instalaci sestavení přetažením v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="215ca-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="215ca-114">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="215ca-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="215ca-115">Používání nástroje Global Assembly Cache (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="215ca-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="215ca-116">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="215ca-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="215ca-117">**Gacutil -i** \< *název sestavení*></span><span class="sxs-lookup"><span data-stu-id="215ca-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="215ca-118">V tomto příkazu *název sestavení* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="215ca-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="215ca-119">Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="215ca-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="215ca-120">Další informace najdete v tématu [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="215ca-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="215ca-121">Používání projektu InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="215ca-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="215ca-122">Přidat balíček instalace a nasazení do vašeho řešení tak, že otevřete místní nabídku pro vaše řešení a následným výběrem možnosti **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="215ca-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="215ca-123">V **přidat nový projekt** v dialogu **nainstalováno** složky, zvolte **ostatní typy projektů**, **instalace a nasazení**, **InstallShield Limited Edition**a pojmenujte svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="215ca-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="215ca-124">(Pokud se zobrazí výzva, stažení, instalaci a aktivaci programu InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="215ca-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="215ca-125">Obecná konfigurace projektu instalace a nasazení provést buď pomocí Pomocník projektu v **Průzkumníka řešení**, nebo zadáním dílčích kroků jednotlivých očíslovaných kroků v **Průzkumníka řešení**. Konfigurace nastavení, jako byste nebyly přidávání sestavení do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="215ca-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="215ca-126">Chcete-li zahájit proces přidávání sestavení do mezipaměti GAC, zvolte **soubory**, která se nachází v **zadat Data aplikace** vstoupit **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="215ca-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="215ca-127">V podokně  **Složky cílového počítače** otevřete místní nabídku pro položku  **Cílový počítač** a vyberte možnost **Zobrazit předdefinovanou složku** a mezipaměť **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="215ca-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="215ca-128">V případě jednotlivých projektů v rámci řešení obsahující sestavení, které chcete nainstalovat do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="215ca-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="215ca-129">V **zdrojové složky počítače** podokně, vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="215ca-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="215ca-130">V **složky cílového počítače** podokně zvolte **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="215ca-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="215ca-131">V **zdrojové soubory počítače** podokně zvolte **primární výstup z** *< project_name >*.</span><span class="sxs-lookup"><span data-stu-id="215ca-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="215ca-132">Přetáhněte soubor v kroku c do **soubory cílového počítače** podokna (nebo použijte **kopírování** a **vložit** příkazy z místní nabídky souboru).</span><span class="sxs-lookup"><span data-stu-id="215ca-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215ca-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="215ca-133">See Also</span></span>  
 [<span data-ttu-id="215ca-134">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="215ca-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="215ca-135">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="215ca-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="215ca-136">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="215ca-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="215ca-137">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="215ca-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="215ca-138">Nasazení Instalační služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="215ca-138">Windows Installer Deployment</span></span>](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
