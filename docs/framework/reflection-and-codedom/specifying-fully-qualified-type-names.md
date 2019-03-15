---
title: Určení úplných názvů typů
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32b68078306c2cf7ffe07870de9c4e3150adafe9
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843186"
---
# <a name="specifying-fully-qualified-type-names"></a>Určení úplných názvů typů

Je nutné zadat názvy typů mít platné zadání do různých operací reflexe. Plně kvalifikovaného názvu typu se skládá z specifikaci název sestavení, oboru názvů a název typu. Specifikace názvu typu jsou používány metody jako například <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.

## <a name="grammar-for-type-names"></a>Gramatika pro názvy typů

 Gramatika definuje syntaxe formální jazyků. V následující tabulce jsou uvedeny lexikální pravidla, která popisují, jak rozpoznat platný vstup. Terminály (prvky, které nejsou další redukovatelné) jsou uvedeny v všechna velká písmena. Neterminály (prvky, které jsou dále redukovatelné) jsou uvedeny v řetězcích písmeny nebo jednotlivě v uvozovkách, ale jednoduché uvozovky (') není součástí syntaxe samotný. Znakem svislé čáry (&#124;) označuje pravidla, která mají dílčí pravidla.

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a>Zadávání speciálních znaků

V názvu typu je IDENTIFIKÁTOR libovolný platný název určuje podle pravidel objektů jazyka.

Použít zpětné lomítko (\\) jako řídicí znak pro oddělení následující klíčová slova, když se použije jako součást IDENTIFIKÁTORU.

|Podpisový|Význam|
|-----------|-------------|
|\\,|Oddělovač sestavení.|
|\\+|Vnořený typ oddělovače.|
|\\&|Typ odkazu.|
|\\*|Typ ukazatele.|
|\\[|Oddělovač rozměru pole.|
|\\]|Oddělovač rozměru pole.|
|\\.|Použijte zpětné lomítko před tečku pouze v případě, že období se používá ve specifikaci pole. Období NamespaceSpec nepřebírají zpětné lomítko.|
|\\\|Zpětné lomítko, v případě potřeby jako řetězcový literál.|

Všimněte si, že v všechny součásti token TypeSpec s výjimkou AssemblyNameSpec prostory relevantní. V AssemblyNameSpec souvisí mezery před oddělovačem ',', ale mezery za oddělovačem ',' jsou ignorovány.

Reflexe třídy, jako například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí pozměněný název tak, aby vrácený název lze použít ve volání <xref:System.Type.GetType%2A>, například `MyType.GetType(myType.FullName)`.

Například plně kvalifikovaný název pro typ může být `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.

Pokud byly oboru názvů `Ozzy.Out+Back`, klepněte na znaménko plus musí být předcházen zpětným lomítkem. V opačném případě by analyzátor toto jako oddělovač vnoření. Reflexe generuje tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.

## <a name="specifying-assembly-names"></a>Zadání názvu sestavení

Minimum informací potřebných v specifikaci název sestavení je textový název sestavení (IDENTIFIKÁTOR). Následují tento IDENTIFIKÁTOR čárkou oddělený seznam dvojic vlastnost hodnota, jak je popsáno v následující tabulce. Názvy identifikátorů by měla dodržovat pravidla pro pojmenovávání souborů. IDENTIFIKÁTOR je velká a malá písmena.

|Název vlastnosti|Popis|Povolené hodnoty|
|-------------------|-----------------|----------------------|
|**Verze**|Číslo verze sestavení|*Major.Minor.Build.Revision*, kde *hlavní*, *menší*, *sestavení*, a *revize* jsou celá čísla mezi 0 a 65535 (včetně).|
|**PublicKey**|Plně veřejný klíč|Hodnota úplného veřejný klíč v šestnáctkovém formátu řetězce. Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně určit soukromé sestavení.|
|**PublicKeyToken**|Token veřejného klíče (8 bajtů hash veřejného klíče)|Hodnota tokenu veřejného klíče v šestnáctkovém formátu řetězce. Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně určit soukromé sestavení.|
|**Jazyková verze**|Jazyková verze sestavení|Jazyková verze sestavení ve formátu RFC 1766, nebo "neutrální" pro sestavení nezávislým na jazyku (nonsatellite).|
|**Vlastní**|Vlastní binární velkých objektů (BLOB). Tím se aktuálně používá pouze v sestaveních generovaných [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Vlastní řetězec použitý nástrojem Native Image Generator sestavení mezipaměti upozornit, že je nativní bitové kopie sestavení probíhá instalace a proto má být nainstalován v mezipaměti nativních bitových kopií. Nazývá se také řetězec zap.|

Následující příklad ukazuje **AssemblyName** pro sestavení s jednoduchým názvem s výchozí jazykovou verzi.

```csharp
com.microsoft.crypto, Culture=""
```

Následující příklad ukazuje plně zadaný odkaz pro sestavení se silným názvem pomocí jazykové verze "en".

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

Následující příklady ukazují, částečně určeného **AssemblyName**, které je možné splnit silné nebo sestavení s jednoduchým názvem.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

Následující příklady ukazují, částečně určeného **AssemblyName**, které musí být splněno sestavení s jednoduchým názvem.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

Následující příklady ukazují, částečně určeného **AssemblyName**, které musí být splněno sestavení se silným názvem.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```
## <a name="specifying-generic-types"></a>Zadání obecných typů

SimpleTypeSpec\`číslo představuje otevřený obecný typ. se od 1 do *n* parametry obecného typu. Například chcete získat odkaz na otevřený obecný typ. seznamu\<T > nebo uzavřený obecný typ seznamu\<řetězec >, použijte ``Type.GetType("System.Collections.Generic.List`1")`` získáte odkaz na obecný typ slovníku\<TKey, TValue >, použijte ``Type.GetType("System.Collections.Generic.Dictionary`2")``.

## <a name="specifying-pointers"></a>Určení ukazatele

SimpleTypeSpec * představuje nespravovaný ukazatel. Například ukazatele na typ MyType získáte pomocí `Type.GetType("MyType*")`. Chcete-li získat ukazatel na ukazatel na typ MyType, použijte `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Určení odkazy

SimpleTypeSpec & představuje spravovaného ukazatele nebo odkazu. Například pokud chcete získat odkaz na typ MyType, použít `Type.GetType("MyType &")`. Všimněte si, že na rozdíl od ukazatelů, odkazů jsou omezené na jedné úrovni.

## <a name="specifying-arrays"></a>Určení polí

V BNF – gramatika ReflectionEmitDimension platí jenom pro definice nekompletní typ načten pomocí možnosti <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Definice neúplného typu jsou <xref:System.Reflection.Emit.TypeBuilder> objekty, které jsou vytvářeny pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> ale na které <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> se nevolala. ReflectionDimension slouží k načtení žádné definice typu, která byla dokončena, to znamená typ, který se načetl.

Pole jsou přístupné v reflexi tak, že určíte počet rozměrů pole:

- `Type.GetType("MyArray[]")` Získá pole s jednou dimenzí s dolní mez 0.

- `Type.GetType("MyArray[*]")` Získá pole s jednou dimenzí s neznámým rozsahem. nižší.
- `Type.GetType("MyArray[][]")` Získá pole dvourozměrné pole.

- `Type.GetType("MyArray[*,*]")` a `Type.GetType("MyArray[,]")` získá obdélníkové dvojrozměrné pole s Neznámý dolní meze.

Všimněte si, že z modulu runtime pohledu `MyArray[] != MyArray[*]`, ale pro vícerozměrná pole jsou ekvivalentní zápisy dva. To znamená `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` vyhodnotí jako **true**.

Pro **ModuleBuilder.GetType**, `MyArray[0..5]` určuje pole s jednou dimenzí s velikostí 6, dolní meze 0. `MyArray[4…]` označuje jednou dimenzí pole neznámé velikosti a dolní mez 4.

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
