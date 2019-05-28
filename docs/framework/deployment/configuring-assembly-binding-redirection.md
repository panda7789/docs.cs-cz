---
title: Konfigurace přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5df468b87c62f454f6a42fa7a80d92e5ec199fd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873727"
---
# <a name="configuring-assembly-binding-redirection"></a>Konfigurace přesměrování vazby sestavení
Ve výchozím nastavení aplikace použijte sadu sestavení rozhraní .NET Framework, která jsou součástí modulu runtime verze použitá pro kompilaci aplikace. Můžete použít **appliesTo** atribut na [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) prvku v konfiguračním souboru aplikace přesměrovat odkazy vazby sestavení na konkrétní verzi rozhraní .NET Sestavení rozhraní. Tento volitelný atribut používá k označení, která verze se vztahuje na číslo verze rozhraní .NET Framework. Pokud ne **appliesTo** atribut zadán, **\<assemblyBinding>** element platí pro všechny verze rozhraní .NET Framework.  
  
 **AppliesTo** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0. To znamená, že všechny **\<assemblyBinding>** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.  
  
> [!NOTE]
>  Použití **appliesTo** atribut omezit přesměrování vazeb sestavení na konkrétní verzi modulu runtime.  
  
 Například pro přesměrování vazby pro sestavení rozhraní .NET Framework verze 1.0 sestavení, bude zahrnovat následující kód XML v konfiguračním souboru aplikace.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding>** prvky jsou citlivé na pořadí. Měli byste zadat informace o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.0 nejprve, za nímž následuje informace o přesměrování vazby sestavení pro všechna sestavení rozhraní .NET Framework verze 1.1. Nakonec je třeba zadat informace o přesměrování vazby sestavení pro všechny přesměrování sestavení rozhraní .NET Framework, která nepoužívá **appliesTo** atribut a tedy platí pro všechny verze rozhraní .NET Framework. V případě konfliktu při přesměrování je použit první odpovídající příkaz přesměrování konfiguračního souboru.  
  
 Například pro přesměrování jednoho odkazu na sestavení rozhraní .NET Framework verze 1.0 a jiného odkazu na sestavení rozhraní .NET Framework verze 1.1, by použít vzor, uvedený v následujícím pseudokódu.  
  
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
 Modul runtime analyzuje konfigurační soubory jednou při domény aplikace se vytvoří a načte kódu do této domény aplikace. Modul common language runtime zpracovává chyby v konfiguračním souboru pomocí položka je ignorována. Modul runtime ignorovat celý konfigurační soubor, pokud obsahuje nesprávně vytvořeným kódem XML. Pro neplatný kód XML pouze části neplatný se ignorují.  
  
 Můžete určit, zda konfigurační soubor se používá tak, že určíte, zda dochází k přesměrování vazby sestavení. Použití [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) zobrazíte, která sestavení jsou načítány. Pokud chcete zobrazit všechny vazby sestavení, je nutné nastavit položku pro **ForceLog** v registru.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
