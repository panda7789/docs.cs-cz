---
title: "Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0944f2798c45a039149baaa6e46ce2b56eb5c5df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="ee242-102">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="ee242-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="ee242-103">Vývojáři mohou chtít Ujistěte se, že se sdílené sestavení, na které se sestavení s více aplikacemi funguje správně.</span><span class="sxs-lookup"><span data-stu-id="ee242-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="ee242-104">Místo průběžně uvedení sestavení v globální mezipaměti sestavení během cyklu vývoje, můžete vytvořit vývojář mechanismu DEVPATH proměnné prostředí, která odkazuje na výstupního adresáře sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ee242-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="ee242-105">Předpokládejme například, že vytváříte sdílené sestavení nazvané MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="ee242-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="ee242-106">Můžete vložit C:\MySharedAssembly\Debug mechanismu DEVPATH proměnné.</span><span class="sxs-lookup"><span data-stu-id="ee242-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="ee242-107">Pak musíte zadat [ \<developmentmode – >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="ee242-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="ee242-108">Tento element informuje modul common language runtime vyhledávat sestavení pomocí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ee242-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="ee242-109">Sdílené sestavení musí být zjistitelný modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="ee242-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="ee242-110">K určení privátní adresář pro použití odkazů na sestavení řešení [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) nebo [ \<zjišťování > Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v [Určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="ee242-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="ee242-111">Můžete taky umístit sestavení v podadresáři adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee242-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="ee242-112">Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ee242-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee242-113">Toto je pokročilá funkce, určena pouze pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="ee242-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="ee242-114">Následující příklad ukazuje, jak způsobí modulu runtime pro vyhledání sestavení v zadaném proměnnou prostředí DEVPATH adresáře.</span><span class="sxs-lookup"><span data-stu-id="ee242-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee242-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee242-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ee242-116">Toto nastavení výchozí nastavení na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="ee242-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee242-117">Toto nastavení používejte pouze v době vývoj.</span><span class="sxs-lookup"><span data-stu-id="ee242-117">Use this setting only at development time.</span></span> <span data-ttu-id="ee242-118">Modul runtime nekontroluje verze na sestavení se silným názvem v mechanismu DEVPATH nalezen.</span><span class="sxs-lookup"><span data-stu-id="ee242-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="ee242-119">Jednoduše použije první sestavení, které najde.</span><span class="sxs-lookup"><span data-stu-id="ee242-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee242-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee242-120">See Also</span></span>  
 [<span data-ttu-id="ee242-121">Konfigurace aplikací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee242-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
