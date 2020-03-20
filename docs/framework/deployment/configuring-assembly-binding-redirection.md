---
title: Konfigurace přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181686"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="2c468-102">Konfigurace přesměrování vazby sestavení</span><span class="sxs-lookup"><span data-stu-id="2c468-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="2c468-103">Ve výchozím nastavení používají aplikace sadu sestavení rozhraní .NET Framework, která byla dodána s runtime verzí používanou ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c468-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="2c468-104">Atribut **appliesTo** na elementu [ \<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) v konfiguračním souboru aplikace můžete použít k přesměrování odkazů na vazbu sestavení na konkrétní verzi sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c468-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="2c468-105">Tento volitelný atribut používá číslo verze rozhraní .NET Framework k označení, na kterou verzi se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="2c468-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="2c468-106">Pokud není zadán žádný atribut **appliesTo,** element \*\* \<assemblyBinding>\*\* se vztahuje na všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c468-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2c468-107">Atribut **appliesTo** byl zaveden v rozhraní .NET Framework verze 1.1; rozhraní .NET Framework verze 1.0 jej ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2c468-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="2c468-108">To znamená, že všechny \*\* \<elementy assemblyBinding>\*\* jsou použity při použití rozhraní .NET Framework verze 1.0, i když je zadán atribut **appliesTo.**</span><span class="sxs-lookup"><span data-stu-id="2c468-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c468-109">Pomocí atributu **appliesTo** omezte přesměrování vazeb sestavení na určitou verzi běhu.</span><span class="sxs-lookup"><span data-stu-id="2c468-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="2c468-110">Chcete-li například přesměrovat vazbu sestavení pro sestavení rozhraní .NET Framework verze 1.0, zahrnete do konfiguračního souboru aplikace následující kód XML.</span><span class="sxs-lookup"><span data-stu-id="2c468-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="2c468-111">\*\* \<AssemblyBinding>\*\* prvky jsou citlivé na pořadí.</span><span class="sxs-lookup"><span data-stu-id="2c468-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="2c468-112">Nejprve byste měli zadat informace o přesměrování vazeb sestavení pro všechna sestavení rozhraní .NET Framework verze 1.0 následované informacemi o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="2c468-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="2c468-113">Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení rozhraní .NET Framework, které nepoužívá atribut **appliesTo** a proto se vztahuje na všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c468-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="2c468-114">V případě konfliktu v přesměrování se použije první odpovídající příkaz přesměrování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2c468-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="2c468-115">Chcete-li například přesměrovat jeden odkaz na sestavení rozhraní .NET Framework verze 1.0 a jiný odkaz na sestavení rozhraní .NET Framework verze 1.1, použijte vzorek zobrazený v následujícím pseudokódu.</span><span class="sxs-lookup"><span data-stu-id="2c468-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="2c468-116">Ladění chyb konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2c468-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="2c468-117">Runtime analyzuje konfigurační soubory jednou při vytvoření domény aplikace a načte kód do této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c468-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="2c468-118">Běžný jazyk runtime zpracovává chyby v konfiguračním souboru ignorováním položky.</span><span class="sxs-lookup"><span data-stu-id="2c468-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="2c468-119">Runtime ignoruje celý konfigurační soubor, pokud obsahuje poškozený xml.</span><span class="sxs-lookup"><span data-stu-id="2c468-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="2c468-120">V případě neplatného jazyka XML jsou ignorovány pouze neplatné oddíly.</span><span class="sxs-lookup"><span data-stu-id="2c468-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="2c468-121">Můžete určit, zda konfigurační soubor se používá určením, zda dojde k přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c468-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="2c468-122">Pomocí [prohlížeče protokolů vazby sestavení (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte, která sestavení jsou načítána.</span><span class="sxs-lookup"><span data-stu-id="2c468-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="2c468-123">Chcete-li zobrazit všechna vazby sestavení, musíte nastavit položku pro **ForceLog** v registru.</span><span class="sxs-lookup"><span data-stu-id="2c468-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c468-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c468-124">See also</span></span>

- [<span data-ttu-id="2c468-125">Postupy: Povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="2c468-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
