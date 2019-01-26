---
title: '&lt;Hodnota providerOption&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: da3dc807d3d30b6b45e34ccf7d328344ca580327
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084169"
---
# <a name="ltprovideroptiongt-element"></a>&lt;Hodnota providerOption&gt; – Element
Určuje atributy verze kompilátoru poskytovatele jazyka.  
  
 \<Konfigurace Element >  
\<system.codedom Element>  
\<compilers Element>  
\<Kompilátor > – Element  
\<provideroption – > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadovaný atribut.<br /><br /> Určuje název možnosti; například "CompilerVersion".|  
|`value`|Požadovaný atribut.<br /><br /> Určuje hodnotu parametru; například "v3.5".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Konfigurace > – Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikacemi rozhraní .NET Framework.|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Určuje konfigurační nastavení kompilátoru pro zprostředkovatele dostupných poskytovatelů jazyka.|  
|[\<Kompilátory > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Kontejner pro kompilátor – elementy konfigurace; obsahuje nulu nebo více `<compiler>` elementy.|  
|[\<Kompilátor > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Určuje kompilátor – konfigurační atributy pro poskytovatele jazyka.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5, poskytovatelů kód Code Document Object Model (CodeDOM) může podporovat možnosti specifické pro zprostředkovatele s použitím `<providerOption>` elementu.  
  
 Rozhraní .NET Framework 3.5 zahrnuje aktualizované sestavení rozhraní .NET Framework 2.0 a poskytuje nové sestavení verze 3.5, které obsahují nové typy. Poskytovatelé kód Microsoft C# a Visual Basic jsou obsaženy v sestavení rozhraní .NET Framework 2.0, ale byla aktualizována o podporu kompilátory verze 3.5. Ve výchozím nastavení poskytovatelů aktualizovaný kód generování kódu pro verze 2.0 kompilátory. Můžete použít `<providerOption>` prvek, který chcete změnit cílovou verzi kompilátoru 3.5. Chcete-li to provést, zadejte "CompilerVersion" pro `name` atribut a "v3.5" pro `value` atribut. Musí předcházet číslo verze, s malá "v".  
  
 Specifikace verze můžete globální provést přidáním `<providerOption>` prvků rozhraní .NET Framework 2.0 Machine.config nebo kořenový soubor Web.config. Pokud aktualizujete verzi kompilátoru výchozí až 3.5 v souboru Machine.config, můžete změnit ji zpět do 2.0 na základě jednotlivých aplikací s použitím `<providerOption>` prvku v konfiguračním souboru aplikace.  
  
 Implementátoři poskytovatele codeDOM kód může zpracovávat vlastní možnosti tím, že poskytuje konstruktor s daným počtem `providerOptions` parametr typu <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat verzi 3.5 zprostředkovatele kódu C# má být použita.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<Kompilátory > – Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [Určení úplných názvů typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Kompilátor – Element pro kompilátory compilation (schéma nastavení technologie ASP.NET)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
