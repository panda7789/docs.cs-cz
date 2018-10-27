---
title: Konfigurace přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3abf42790757708b235b3eab82ea9a11ff545215
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182863"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="4d646-102">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="4d646-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="4d646-103">Ve výchozím nastavení aplikace použijte sadu sestavení rozhraní .NET Framework, která jsou součástí modulu runtime verze použitá pro kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d646-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="4d646-104">Můžete použít **appliesTo** atribut na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) prvku v konfiguračním souboru aplikace přesměrovat odkazy vazby sestavení na konkrétní verzi rozhraní .NET Sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d646-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="4d646-105">Tento volitelný atribut používá k označení, která verze se vztahuje na číslo verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d646-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="4d646-106">Pokud ne **appliesTo** atribut zadán,  **\<assemblyBinding >** element platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d646-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4d646-107">**AppliesTo** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="4d646-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="4d646-108">To znamená, že všechny  **\<assemblyBinding >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.</span><span class="sxs-lookup"><span data-stu-id="4d646-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d646-109">Použití **appliesTo** atribut omezit přesměrování vazeb sestavení na konkrétní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4d646-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="4d646-110">Například pro přesměrování vazby pro sestavení rozhraní .NET Framework verze 1.0 sestavení, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d646-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="4d646-111">**\<AssemblyBinding >** prvky jsou citlivé na pořadí.</span><span class="sxs-lookup"><span data-stu-id="4d646-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="4d646-112">Měli byste zadat informace o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.0 nejprve, za nímž následuje informace o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="4d646-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="4d646-113">Nakonec je třeba zadat informace o přesměrování vazby sestavení pro všechny přesměrování sestavení rozhraní .NET Framework, která nepoužívá **appliesTo** atribut a tedy platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d646-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="4d646-114">V případě konfliktu při přesměrování je použit první odpovídající příkaz přesměrování konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4d646-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="4d646-115">Například pro přesměrování jednoho odkazu na sestavení rozhraní .NET Framework verze 1.0 a jiného odkazu na sestavení rozhraní .NET Framework verze 1.1, by použít vzor, uvedený v následujícím pseudokódu.</span><span class="sxs-lookup"><span data-stu-id="4d646-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="4d646-116">Ladění chyb konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4d646-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="4d646-117">Modul runtime analyzuje konfigurační soubory jednou při domény aplikace se vytvoří a načte kódu do této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d646-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="4d646-118">Modul common language runtime zpracovává chyby v konfiguračním souboru pomocí položka je ignorována.</span><span class="sxs-lookup"><span data-stu-id="4d646-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="4d646-119">Modul runtime ignorovat celý konfigurační soubor, pokud obsahuje nesprávně vytvořeným kódem XML.</span><span class="sxs-lookup"><span data-stu-id="4d646-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="4d646-120">Pro neplatný kód XML pouze části neplatný se ignorují.</span><span class="sxs-lookup"><span data-stu-id="4d646-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="4d646-121">Můžete určit, zda konfigurační soubor se používá tak, že určíte, zda dochází k přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d646-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="4d646-122">Použití [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte, která sestavení jsou načítány.</span><span class="sxs-lookup"><span data-stu-id="4d646-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="4d646-123">Pokud chcete zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.</span><span class="sxs-lookup"><span data-stu-id="4d646-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d646-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d646-124">See Also</span></span>  
- [<span data-ttu-id="4d646-125">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="4d646-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
