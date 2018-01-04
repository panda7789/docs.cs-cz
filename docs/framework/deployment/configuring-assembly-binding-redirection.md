---
title: "Konfigurace přesměrování vazby sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b53673d1ddb1de7fed087b4c5cb125e50f11b918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="5949c-102">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="5949c-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="5949c-103">Ve výchozím nastavení používají aplikace sadu sestavení rozhraní .NET Framework, která jsou součástí na verzi modulu runtime používá ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5949c-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="5949c-104">Můžete použít **AppliesTo –** atributu u [ \<assemblybinding – >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element v konfiguračním souboru aplikace pro přesměrování odkazy na sestavení vazbu na konkrétní verzi rozhraní .NET Sestavení architektury.</span><span class="sxs-lookup"><span data-stu-id="5949c-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="5949c-105">Tento volitelný atribut používá označíte, která verze se vztahuje na číslo verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5949c-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="5949c-106">Pokud žádné **AppliesTo –** atribut zadán,  **\<assemblybinding – >** element platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5949c-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5949c-107">**AppliesTo –** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="5949c-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="5949c-108">To znamená, že všechny  **\<assemblybinding – >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **AppliesTo –** zadán atribut.</span><span class="sxs-lookup"><span data-stu-id="5949c-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5949c-109">Použití **AppliesTo –** atribut omezit sestavení – přesměrování vazby na konkrétní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5949c-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="5949c-110">Například k přesměrování vazby sestavení rozhraní .NET Framework verze 1.0 sestavení, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5949c-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="5949c-111"> **\<Assemblybinding – >** prvky jsou pořadí-velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="5949c-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="5949c-112">Informace o všech sestavení rozhraní .NET Framework verze 1.0 přesměrování vazby sestavení by měl zadejte nejprve následuje informací o přesměrování vazby sestavení pro všechny sestavení rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="5949c-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="5949c-113">Nakonec zadejte informace o přesměrování vazby sestavení pro žádné přesměrování sestavení rozhraní .NET Framework, který nepoužívá **AppliesTo –** atribut a proto se vztahuje na všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5949c-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="5949c-114">V případě konfliktu v přesměrování se použije první odpovídající příkaz přesměrování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5949c-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="5949c-115">Například pokud chcete přesměrovat jeden odkaz na sestavení rozhraní .NET Framework verze 1.0 a další odkaz na sestavení rozhraní .NET Framework verze 1.1, použijte vzor uvedené v následující pseudokódu.</span><span class="sxs-lookup"><span data-stu-id="5949c-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="5949c-116">Ladění chyb konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5949c-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="5949c-117">Modul runtime analyzuje konfigurační soubory jednou, pokud domény aplikace se vytvoří a načte kód do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5949c-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="5949c-118">Modul common language runtime zpracovává chyby v konfiguračním souboru ignorováním položku.</span><span class="sxs-lookup"><span data-stu-id="5949c-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="5949c-119">Modul runtime ignoruje celý konfigurační soubor, pokud obsahuje poškozený obsah XML.</span><span class="sxs-lookup"><span data-stu-id="5949c-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="5949c-120">Pro neplatný kód XML se ignorují jenom neplatný oddíly.</span><span class="sxs-lookup"><span data-stu-id="5949c-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="5949c-121">Můžete určit, zda konfigurační soubor je používán podle určení, zda dochází k přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="5949c-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="5949c-122">Použití [sestavení vazby Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte sestavení, které jsou právě načítán.</span><span class="sxs-lookup"><span data-stu-id="5949c-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="5949c-123">Pokud chcete zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.</span><span class="sxs-lookup"><span data-stu-id="5949c-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5949c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5949c-124">See Also</span></span>  
 [<span data-ttu-id="5949c-125">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="5949c-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
