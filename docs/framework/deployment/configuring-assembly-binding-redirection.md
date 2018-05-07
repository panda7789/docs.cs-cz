---
title: Konfigurace přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04743dc7a0fc821f2e3b94929e2384eb25c69f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-assembly-binding-redirection"></a>Konfigurace přesměrování vazby sestavení
Ve výchozím nastavení používají aplikace sadu sestavení rozhraní .NET Framework, která jsou součástí na verzi modulu runtime používá ke kompilaci aplikace. Můžete použít **AppliesTo –** atributu u [ \<assemblybinding – >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element v konfiguračním souboru aplikace pro přesměrování odkazy na sestavení vazbu na konkrétní verzi rozhraní .NET Sestavení architektury. Tento volitelný atribut používá označíte, která verze se vztahuje na číslo verze rozhraní .NET Framework. Pokud žádné **AppliesTo –** atribut zadán,  **\<assemblybinding – >** element platí pro všechny verze rozhraní .NET Framework.  
  
 **AppliesTo –** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0. To znamená, že všechny  **\<assemblybinding – >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **AppliesTo –** zadán atribut.  
  
> [!NOTE]
>  Použití **AppliesTo –** atribut omezit sestavení – přesměrování vazby na konkrétní verzi modulu runtime.  
  
 Například k přesměrování vazby sestavení rozhraní .NET Framework verze 1.0 sestavení, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<Assemblybinding – >** prvky jsou pořadí-velká a malá písmena. Informace o všech sestavení rozhraní .NET Framework verze 1.0 přesměrování vazby sestavení by měl zadejte nejprve následuje informací o přesměrování vazby sestavení pro všechny sestavení rozhraní .NET Framework verze 1.1. Nakonec zadejte informace o přesměrování vazby sestavení pro žádné přesměrování sestavení rozhraní .NET Framework, který nepoužívá **AppliesTo –** atribut a proto se vztahuje na všechny verze rozhraní .NET Framework. V případě konfliktu v přesměrování se použije první odpovídající příkaz přesměrování v konfiguračním souboru.  
  
 Například pokud chcete přesměrovat jeden odkaz na sestavení rozhraní .NET Framework verze 1.0 a další odkaz na sestavení rozhraní .NET Framework verze 1.1, použijte vzor uvedené v následující pseudokódu.  
  
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
  
## <a name="debugging-configuration-file-errors"></a>Ladění chyb konfiguračního souboru  
 Modul runtime analyzuje konfigurační soubory jednou, pokud domény aplikace se vytvoří a načte kód do domény aplikace. Modul common language runtime zpracovává chyby v konfiguračním souboru ignorováním položku. Modul runtime ignoruje celý konfigurační soubor, pokud obsahuje poškozený obsah XML. Pro neplatný kód XML se ignorují jenom neplatný oddíly.  
  
 Můžete určit, zda konfigurační soubor je používán podle určení, zda dochází k přesměrování vazby sestavení. Použití [sestavení vazby Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte sestavení, které jsou právě načítán. Pokud chcete zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
