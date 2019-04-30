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
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775827"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="4e1f1-102">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="4e1f1-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="4e1f1-103">Vývojáři mohou chtít mít jistotu, sdílené sestavení, které navíc teď připravují funguje správně s několika aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="4e1f1-104">Namísto vložení sestavení do globální mezipaměti sestavení průběžně během cyklu vývoje, můžete vytvořit vývojář proměnné prostředí DEVPATH, který odkazuje na výstupního adresáře sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="4e1f1-105">Předpokládejme například, že vytváříte sdílené sestavení nazvané MySharedAssembly a výstupní adresář je C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="4e1f1-106">Můžete vložit C:\MySharedAssembly\Debug DEVPATH proměnné.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="4e1f1-107">Musíte zadat [ \<developmentmode – >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) prvku v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="4e1f1-108">Tento prvek říká vyhledání sestavení pomocí mechanismu DEVPATH common language runtime.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="4e1f1-109">Sdílená sestavení musí být zjistitelné modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="4e1f1-110">K určení privátní adresář pro řešení pomocí odkazů na sestavení [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) nebo [ \<zjišťování > Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) v konfiguračním souboru, jak je popsáno v [Určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="4e1f1-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="4e1f1-111">Můžete také vložit sestavení v podadresáři adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="4e1f1-112">Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4e1f1-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e1f1-113">Jde o pokročilou funkci určené pouze pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="4e1f1-114">Následující příklad ukazuje, jak mají hledat sestavení v adresářích určených proměnnou prostředí DEVPATH pomocí běhového modulu.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e1f1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e1f1-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4e1f1-116">Toto nastavení výchozí hodnota je false.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e1f1-117">Toto nastavení použijte jenom v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-117">Use this setting only at development time.</span></span> <span data-ttu-id="4e1f1-118">Modul runtime verze sestavení se silným názvem součástí mechanismu DEVPATH nekontroluje.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="4e1f1-119">Jednoduše použije první sestavení, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="4e1f1-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1f1-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e1f1-120">See also</span></span>

- [<span data-ttu-id="4e1f1-121">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="4e1f1-121">Configuring Apps by using Configuration Files</span></span>](index.md)
