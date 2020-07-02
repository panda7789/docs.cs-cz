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
# <a name="configuring-assembly-binding-redirection"></a>Konfigurace přesměrování vazby sestavení
Ve výchozím nastavení používají aplikace sadu .NET Framework sestavení, která byla dodávána s verzí modulu runtime použitou ke kompilaci aplikace. V konfiguračním souboru aplikace **appliesTo** můžete použít atribut AppliesTo [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) pro přesměrování odkazů na vazby sestavení na konkrétní verzi .NET Framework sestavení. Tento nepovinný atribut používá .NET Framework číslo verze k označení, na kterou verzi se vztahuje. Pokud není zadán žádný atribut **AppliesTo** , bude **\<assemblyBinding>** element platit pro všechny verze .NET Framework.  
  
 Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0. To znamená, že všechny **\<assemblyBinding>** prvky jsou aplikovány při použití .NET Framework verze 1,0, a to i v případě, že je zadán atribut **AppliesTo** .  
  
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
  
 **\<assemblyBinding>** Prvky jsou závislé na pořadí. Nejdříve je třeba zadat informace o přesměrování vazby sestavení pro všechna .NET Framework sestavení verze 1,0 a následně informace o přesměrování vazby sestavení pro všechna sestavení .NET Framework verze 1,1. Nakonec zadejte informace o přesměrování vazby sestavení pro jakékoli přesměrování sestavení .NET Framework, které nepoužívá atribut **AppliesTo** , a proto platí pro všechny verze .NET Framework. V případě konfliktu v přesměrování se použije první shodný příkaz přesměrování v konfiguračním souboru.  
  
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
  
 Můžete určit, zda se konfigurační soubor používá, určením, zda dochází ke přesměrování vazby sestavení. Použijte [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) k zobrazení sestavení, která jsou načítána. Chcete-li zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
