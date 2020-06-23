---
title: 'Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH'
description: Otestujte správné fungování sdíleného sestavení s mnoha aplikacemi v rozhraní .NET pomocí konfiguračního souboru XML počítače a proměnné prostředí mechanismu DEVPATH.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105376"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="2378c-103">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="2378c-103">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="2378c-104">Vývojáři mohou chtít zajistit, aby sdílené sestavení, které sestavuje, fungovalo správně s více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="2378c-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="2378c-105">Namísto průběžného vkládání sestavení do globální mezipaměti sestavení (GAC) během cyklu vývoje může vývojář vytvořit proměnnou prostředí mechanismu DEVPATH, která odkazuje na výstupní adresář sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="2378c-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="2378c-106">Předpokládejme například, že vytváříte sdílené sestavení s názvem MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="2378c-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="2378c-107">C:\MySharedAssembly\Debug můžete umístit do proměnné mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2378c-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="2378c-108">Pak je nutné zadat [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) prvek v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="2378c-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="2378c-109">Tento prvek oznamuje modulu CLR (Common Language Runtime), aby mohl používat mechanismu DEVPATH k vyhledávání sestavení.</span><span class="sxs-lookup"><span data-stu-id="2378c-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="2378c-110">Sdílené sestavení musí být zjistitelné modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="2378c-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="2378c-111">Chcete-li určit privátní adresář pro překlad odkazů na sestavení, použijte [ \<codeBase> element](./file-schema/runtime/codebase-element.md) nebo [ \<probing> element](./file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v tématu [určení umístění sestavení](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="2378c-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="2378c-112">Můžete také vložit sestavení do podadresáře adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="2378c-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="2378c-113">Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2378c-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2378c-114">Jedná se o pokročilou funkci, která je určená jenom pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="2378c-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="2378c-115">Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2378c-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2378c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="2378c-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2378c-117">Toto nastavení má výchozí hodnotu NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="2378c-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2378c-118">Toto nastavení použijte pouze v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="2378c-118">Use this setting only at development time.</span></span> <span data-ttu-id="2378c-119">Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2378c-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="2378c-120">Jednoduše používá první nalezené sestavení.</span><span class="sxs-lookup"><span data-stu-id="2378c-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2378c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2378c-121">See also</span></span>

- [<span data-ttu-id="2378c-122">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="2378c-122">Configuring Apps by using Configuration Files</span></span>](index.md)
