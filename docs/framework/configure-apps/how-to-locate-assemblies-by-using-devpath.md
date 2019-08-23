---
title: 'Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912998"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="d2214-102">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="d2214-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="d2214-103">Vývojáři mohou chtít zajistit, aby sdílené sestavení, které sestavuje, fungovalo správně s více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="d2214-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="d2214-104">Namísto průběžného vkládání sestavení do globální mezipaměti sestavení (GAC) během cyklu vývoje může vývojář vytvořit proměnnou prostředí mechanismu DEVPATH, která odkazuje na výstupní adresář sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2214-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="d2214-105">Předpokládejme například, že vytváříte sdílené sestavení s názvem MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="d2214-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="d2214-106">C:\MySharedAssembly\Debug můžete umístit do proměnné mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d2214-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="d2214-107">Pak musíte zadat [ \<developmentMode >](./file-schema/runtime/developmentmode-element.md) element v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="d2214-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="d2214-108">Tento prvek oznamuje modulu CLR (Common Language Runtime), aby mohl používat mechanismu DEVPATH k vyhledávání sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2214-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="d2214-109">Sdílené sestavení musí být zjistitelné modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d2214-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="d2214-110">Chcete-li určit privátní adresář pro překlad odkazů na sestavení, použijte [ \<> element](./file-schema/runtime/codebase-element.md) nebo [ \<> elementu pro zjišťování](./file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v tématu [určení umístění sestavení](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="d2214-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="d2214-111">Můžete také vložit sestavení do podadresáře adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2214-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="d2214-112">Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d2214-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2214-113">Jedná se o pokročilou funkci, která je určená jenom pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="d2214-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="d2214-114">Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d2214-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2214-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2214-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d2214-116">Toto nastavení má výchozí hodnotu NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="d2214-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2214-117">Toto nastavení použijte pouze v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="d2214-117">Use this setting only at development time.</span></span> <span data-ttu-id="d2214-118">Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="d2214-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="d2214-119">Jednoduše používá první nalezené sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2214-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2214-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2214-120">See also</span></span>

- [<span data-ttu-id="d2214-121">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="d2214-121">Configuring Apps by using Configuration Files</span></span>](index.md)
