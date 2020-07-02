---
title: Konfigurace přesměrování vazby sestavení
description: Viz jak nakonfigurovat přesměrování vazby sestavení v rozhraní .NET pomocí atributu appliesTo v elementu assemblyBinding konfiguračního souboru aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 8f3e2270d92e11ea467d6cefc2b19b4faff563b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621727"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="320a3-103">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="320a3-103">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="320a3-104">Ve výchozím nastavení používají aplikace sadu .NET Framework sestavení, která byla dodávána s verzí modulu runtime použitou ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="320a3-104">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="320a3-105">V konfiguračním souboru aplikace **appliesTo** můžete použít atribut AppliesTo [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) pro přesměrování odkazů na vazby sestavení na konkrétní verzi .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="320a3-105">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="320a3-106">Tento nepovinný atribut používá .NET Framework číslo verze k označení, na kterou verzi se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="320a3-106">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="320a3-107">Pokud není zadán žádný atribut **AppliesTo** , bude **\<assemblyBinding>** element platit pro všechny verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="320a3-107">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="320a3-108">Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="320a3-108">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="320a3-109">To znamená, že všechny **\<assemblyBinding>** prvky jsou aplikovány při použití .NET Framework verze 1,0, a to i v případě, že je zadán atribut **AppliesTo** .</span><span class="sxs-lookup"><span data-stu-id="320a3-109">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="320a3-110">Použijte atribut **AppliesTo** k omezení přesměrování vazby sestavení na konkrétní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="320a3-110">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="320a3-111">Chcete-li například přesměrovat vazbu sestavení pro sestavení .NET Framework verze 1,0, měli byste do konfiguračního souboru aplikace zahrnout následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="320a3-111">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="320a3-112">**\<assemblyBinding>** Prvky jsou závislé na pořadí.</span><span class="sxs-lookup"><span data-stu-id="320a3-112">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="320a3-113">Nejdříve je třeba zadat informace o přesměrování vazby sestavení pro všechna .NET Framework sestavení verze 1,0 a následně informace o přesměrování vazby sestavení pro všechna sestavení .NET Framework verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="320a3-113">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="320a3-114">Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení .NET Framework, které nepoužívá atribut **AppliesTo** , a proto platí pro všechny verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="320a3-114">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="320a3-115">V případě konfliktu v přesměrování se použije první shodný příkaz přesměrování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="320a3-115">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="320a3-116">Chcete-li například přesměrovat jeden odkaz na sestavení verze 1,0 .NET Framework a jiný odkaz na sestavení .NET Framework verze 1,1, použijte vzor uvedený v následujícím pseudokódu.</span><span class="sxs-lookup"><span data-stu-id="320a3-116">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="320a3-117">Ladění chyb konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="320a3-117">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="320a3-118">Modul runtime analyzuje konfigurační soubory jednou při vytvoření domény aplikace a načítá kód do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="320a3-118">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="320a3-119">Modul CLR (Common Language Runtime) zpracovává chyby v konfiguračním souboru tak, že položku ignoruje.</span><span class="sxs-lookup"><span data-stu-id="320a3-119">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="320a3-120">Modul runtime ignoruje celý konfigurační soubor, pokud obsahuje chybně vytvořený kód XML.</span><span class="sxs-lookup"><span data-stu-id="320a3-120">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="320a3-121">Pro neplatný kód XML jsou ignorovány pouze neplatné oddíly.</span><span class="sxs-lookup"><span data-stu-id="320a3-121">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="320a3-122">Můžete určit, zda se konfigurační soubor používá, určením, zda dochází ke přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="320a3-122">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="320a3-123">Použijte [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) k zobrazení sestavení, která jsou načítána.</span><span class="sxs-lookup"><span data-stu-id="320a3-123">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="320a3-124">Chcete-li zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.</span><span class="sxs-lookup"><span data-stu-id="320a3-124">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320a3-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="320a3-125">See also</span></span>

- [<span data-ttu-id="320a3-126">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="320a3-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
