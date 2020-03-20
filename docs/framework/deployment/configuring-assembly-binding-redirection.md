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
# <a name="configuring-assembly-binding-redirection"></a>Konfigurace přesměrování vazby sestavení
Ve výchozím nastavení používají aplikace sadu sestavení rozhraní .NET Framework, která byla dodána s runtime verzí používanou ke kompilaci aplikace. Atribut **appliesTo** na elementu [ \<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) v konfiguračním souboru aplikace můžete použít k přesměrování odkazů na vazbu sestavení na konkrétní verzi sestavení rozhraní .NET Framework. Tento volitelný atribut používá číslo verze rozhraní .NET Framework k označení, na kterou verzi se vztahuje. Pokud není zadán žádný atribut **appliesTo,** element ** \<assemblyBinding>** se vztahuje na všechny verze rozhraní .NET Framework.  
  
 Atribut **appliesTo** byl zaveden v rozhraní .NET Framework verze 1.1; rozhraní .NET Framework verze 1.0 jej ignoruje. To znamená, že všechny ** \<elementy assemblyBinding>** jsou použity při použití rozhraní .NET Framework verze 1.0, i když je zadán atribut **appliesTo.**  
  
> [!NOTE]
> Pomocí atributu **appliesTo** omezte přesměrování vazeb sestavení na určitou verzi běhu.  
  
 Chcete-li například přesměrovat vazbu sestavení pro sestavení rozhraní .NET Framework verze 1.0, zahrnete do konfiguračního souboru aplikace následující kód XML.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 ** \<AssemblyBinding>** prvky jsou citlivé na pořadí. Nejprve byste měli zadat informace o přesměrování vazeb sestavení pro všechna sestavení rozhraní .NET Framework verze 1.0 následované informacemi o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.1. Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení rozhraní .NET Framework, které nepoužívá atribut **appliesTo** a proto se vztahuje na všechny verze rozhraní .NET Framework. V případě konfliktu v přesměrování se použije první odpovídající příkaz přesměrování v konfiguračním souboru.  
  
 Chcete-li například přesměrovat jeden odkaz na sestavení rozhraní .NET Framework verze 1.0 a jiný odkaz na sestavení rozhraní .NET Framework verze 1.1, použijte vzorek zobrazený v následujícím pseudokódu.  
  
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
  
## <a name="debugging-configuration-file-errors"></a>Ladění chyb konfiguračního souboru  
 Runtime analyzuje konfigurační soubory jednou při vytvoření domény aplikace a načte kód do této domény aplikace. Běžný jazyk runtime zpracovává chyby v konfiguračním souboru ignorováním položky. Runtime ignoruje celý konfigurační soubor, pokud obsahuje poškozený xml. V případě neplatného jazyka XML jsou ignorovány pouze neplatné oddíly.  
  
 Můžete určit, zda konfigurační soubor se používá určením, zda dojde k přesměrování vazby sestavení. Pomocí [prohlížeče protokolů vazby sestavení (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte, která sestavení jsou načítána. Chcete-li zobrazit všechna vazby sestavení, musíte nastavit položku pro **ForceLog** v registru.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
