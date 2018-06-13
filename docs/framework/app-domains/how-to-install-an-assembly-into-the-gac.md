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
ms.openlocfilehash: ed6519cb6bb7006f62ef83cd6baf8f2e32a44d19
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744379"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="3f39a-102">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="3f39a-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="3f39a-103">Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="3f39a-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f39a-104">Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="3f39a-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="3f39a-105">Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="3f39a-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="3f39a-106">Pomocí [Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="3f39a-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="3f39a-107">V sadě Visual Studio 2012 a Visual Studio 2013 můžete tuto akci provést instalací projektu InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="3f39a-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="3f39a-108">Toto je doporučený a nejběžnější způsob přidávání sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f39a-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="3f39a-109">Instalační program poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.</span><span class="sxs-lookup"><span data-stu-id="3f39a-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="3f39a-110">Pomocí [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="3f39a-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="3f39a-111">Nástroj Gacutil.exe slouží k přidávání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f39a-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3f39a-112">Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f39a-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f39a-113">V dřívějších verzích rozhraní .NET Framework povolené rozšíření pro prostředí Shfusion.dll Windows nainstalovat sestavení tak, že je přetáhnete v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="3f39a-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="3f39a-114">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="3f39a-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="3f39a-115">Používání nástroje Global Assembly Cache (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="3f39a-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="3f39a-116">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="3f39a-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="3f39a-117">**Gacutil -i** \< *název sestavení*></span><span class="sxs-lookup"><span data-stu-id="3f39a-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="3f39a-118">V tomto příkazu *název sestavení* je název sestavení pro instalaci v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f39a-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="3f39a-119">Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f39a-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="3f39a-120">Další informace najdete v tématu [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="3f39a-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="3f39a-121">Používání projektu InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="3f39a-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="3f39a-122">Přidání balíčku instalace a nasazení do řešení otevřením místní nabídku pro vaše řešení, a pak vyberete **přidat**, **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="3f39a-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="3f39a-123">V **přidat nový projekt** dialogovém **nainstalovaná** složky, vyberte **jiné typy projektů**, **instalace a nasazení**, **InstallShield Limited Edition**a zadejte název projektu.</span><span class="sxs-lookup"><span data-stu-id="3f39a-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="3f39a-124">(Pokud se zobrazí výzva, stáhnout, nainstalovat a aktivovat InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="3f39a-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="3f39a-125">Provedení obecné konfigurace instalace a nasazení projektu, buď pomocí Pomocníka pro projekt v **Průzkumníku řešení**, nebo výběrem dílčích kroků číslované kroky **Průzkumníku řešení**. Konfigurace vašeho nastavení, jako při sestavení nebyly přidání do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="3f39a-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="3f39a-126">Chcete-li zahájit proces přidávání sestavení do mezipaměti GAC, zvolte **soubory**, který je v části **zadejte Data aplikací** krok v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="3f39a-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="3f39a-127">V **složek na cílovém počítači** podokně otevřete místní nabídku pro **cílový počítač**a potom zvolte **zobrazit předdefinované složku**, **[[ GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="3f39a-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="3f39a-128">V případě jednotlivých projektů v rámci řešení obsahující sestavení, které chcete nainstalovat do globální mezipaměti sestavení:</span><span class="sxs-lookup"><span data-stu-id="3f39a-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="3f39a-129">V **zdrojové složky počítače** podokně vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="3f39a-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="3f39a-130">V **složek na cílovém počítači** podokně vyberte **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="3f39a-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="3f39a-131">V **zdrojové soubory počítače** podokně vyberte **primární výstup z** *< název_projektu >*.</span><span class="sxs-lookup"><span data-stu-id="3f39a-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="3f39a-132">Přetáhněte soubor v kroku c **soubory v cílovém počítači** podokně (nebo použijte **kopie** a **vložení** příkazy z místní nabídky souboru).</span><span class="sxs-lookup"><span data-stu-id="3f39a-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f39a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f39a-133">See Also</span></span>  
 [<span data-ttu-id="3f39a-134">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="3f39a-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="3f39a-135">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="3f39a-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="3f39a-136">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="3f39a-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="3f39a-137">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="3f39a-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="3f39a-138">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="3f39a-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
