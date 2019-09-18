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
# <a name="configuring-assembly-binding-redirection"></a>Konfigurace přesměrování vazby sestavení
Ve výchozím nastavení používají aplikace sadu .NET Framework sestavení, která byla dodávána s verzí modulu runtime použitou ke kompilaci aplikace. Můžete použít **appliesTo** atribut na [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) prvku v konfiguračním souboru aplikace přesměrovat odkazy vazby sestavení na konkrétní verzi rozhraní .NET Sestavení rozhraní. Tento nepovinný atribut používá .NET Framework číslo verze k označení, na kterou verzi se vztahuje. Pokud ne **appliesTo** atribut zadán, **\<assemblyBinding>** element platí pro všechny verze rozhraní .NET Framework.  
  
 Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0. To znamená, že všechny **\<assemblyBinding>** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.  
  
> [!NOTE]
> Použijte atribut **AppliesTo** k omezení přesměrování vazby sestavení na konkrétní verzi modulu runtime.  
  
 Chcete-li například přesměrovat vazbu sestavení pro sestavení .NET Framework verze 1,0, měli byste do konfiguračního souboru aplikace zahrnout následující kód XML.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding>** prvky jsou citlivé na pořadí. Nejdříve je třeba zadat informace o přesměrování vazby sestavení pro všechna .NET Framework sestavení verze 1,0 a následně informace o přesměrování vazby sestavení pro všechna sestavení .NET Framework verze 1,1. Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení .NET Framework, které nepoužívá atribut **AppliesTo** , a proto platí pro všechny verze .NET Framework. V případě konfliktu v přesměrování se použije první shodný příkaz přesměrování v konfiguračním souboru.  
  
 Chcete-li například přesměrovat jeden odkaz na sestavení verze 1,0 .NET Framework a jiný odkaz na sestavení .NET Framework verze 1,1, použijte vzor uvedený v následujícím pseudokódu.  
  
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
 Modul runtime analyzuje konfigurační soubory jednou při vytvoření domény aplikace a načítá kód do domény aplikace. Modul CLR (Common Language Runtime) zpracovává chyby v konfiguračním souboru tak, že položku ignoruje. Modul runtime ignoruje celý konfigurační soubor, pokud obsahuje chybně vytvořený kód XML. Pro neplatný kód XML jsou ignorovány pouze neplatné oddíly.  
  
 Můžete určit, zda se konfigurační soubor používá, určením, zda dochází ke přesměrování vazby sestavení. Použijte [Prohlížeč protokolů vazby sestavení (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) , chcete-li zjistit, která sestavení jsou načítána. Chcete-li zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
