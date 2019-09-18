---
title: Konfigurace přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e2add2756106234227c7b2dd62ae107adc58854
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052183"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="5dece-102">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="5dece-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="5dece-103">Ve výchozím nastavení používají aplikace sadu .NET Framework sestavení, která byla dodávána s verzí modulu runtime použitou ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5dece-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="5dece-104">Můžete použít **appliesTo** atribut na [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) prvku v konfiguračním souboru aplikace přesměrovat odkazy vazby sestavení na konkrétní verzi rozhraní .NET Sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5dece-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="5dece-105">Tento nepovinný atribut používá .NET Framework číslo verze k označení, na kterou verzi se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="5dece-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="5dece-106">Pokud ne **appliesTo** atribut zadán, **\<assemblyBinding>** element platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dece-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5dece-107">Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="5dece-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="5dece-108">To znamená, že všechny **\<assemblyBinding>** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.</span><span class="sxs-lookup"><span data-stu-id="5dece-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dece-109">Použijte atribut **AppliesTo** k omezení přesměrování vazby sestavení na konkrétní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5dece-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="5dece-110">Chcete-li například přesměrovat vazbu sestavení pro sestavení .NET Framework verze 1,0, měli byste do konfiguračního souboru aplikace zahrnout následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="5dece-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="5dece-111">**\<AssemblyBinding>** prvky jsou citlivé na pořadí.</span><span class="sxs-lookup"><span data-stu-id="5dece-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="5dece-112">Nejdříve je třeba zadat informace o přesměrování vazby sestavení pro všechna .NET Framework sestavení verze 1,0 a následně informace o přesměrování vazby sestavení pro všechna sestavení .NET Framework verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="5dece-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="5dece-113">Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení .NET Framework, které nepoužívá atribut **AppliesTo** , a proto platí pro všechny verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dece-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="5dece-114">V případě konfliktu v přesměrování se použije první shodný příkaz přesměrování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5dece-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="5dece-115">Chcete-li například přesměrovat jeden odkaz na sestavení verze 1,0 .NET Framework a jiný odkaz na sestavení .NET Framework verze 1,1, použijte vzor uvedený v následujícím pseudokódu.</span><span class="sxs-lookup"><span data-stu-id="5dece-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="5dece-116">Ladění chyb konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5dece-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="5dece-117">Modul runtime analyzuje konfigurační soubory jednou při vytvoření domény aplikace a načítá kód do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5dece-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="5dece-118">Modul CLR (Common Language Runtime) zpracovává chyby v konfiguračním souboru tak, že položku ignoruje.</span><span class="sxs-lookup"><span data-stu-id="5dece-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="5dece-119">Modul runtime ignoruje celý konfigurační soubor, pokud obsahuje chybně vytvořený kód XML.</span><span class="sxs-lookup"><span data-stu-id="5dece-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="5dece-120">Pro neplatný kód XML jsou ignorovány pouze neplatné oddíly.</span><span class="sxs-lookup"><span data-stu-id="5dece-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="5dece-121">Můžete určit, zda se konfigurační soubor používá, určením, zda dochází ke přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="5dece-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="5dece-122">Použijte [Prohlížeč protokolů vazby sestavení (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) , chcete-li zjistit, která sestavení jsou načítána.</span><span class="sxs-lookup"><span data-stu-id="5dece-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="5dece-123">Chcete-li zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.</span><span class="sxs-lookup"><span data-stu-id="5dece-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dece-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5dece-124">See also</span></span>

- [<span data-ttu-id="5dece-125">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="5dece-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
