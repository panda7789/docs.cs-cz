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
ms.openlocfilehash: 707c71482196d789ed9a88db34af048ec57734fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130030"
---
# <a name="specifying-fully-qualified-type-names"></a>Určení plně kvalifikovaných názvů typů

Je nutné zadat názvy typů, aby měly platný vstup k různým operacím reflexe. Plně kvalifikovaný název typu se skládá ze specifikace názvu sestavení, specifikace oboru názvů a názvu typu. Specifikace názvu typu jsou používány metodami, jako jsou <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.

## <a name="grammar-for-type-names"></a>Gramatika pro názvy typů

 Gramatika definuje syntaxi formálních jazyků. V následující tabulce jsou uvedeny lexikální pravidla, která popisují, jak rozpoznat platný vstup. Terminály (tyto prvky, které nejsou další redukovatelné) jsou uvedeny velkými písmeny. Neterminály (tyto prvky, které jsou dále redukovatelné) jsou zobrazeny v kombinovaných nebo jednotlivě citovaných řetězcích, ale jednoduché uvozovky (') nejsou součástí samotné syntaxe. Znak kanálu (&#124;) označuje pravidla, která mají podpravidla.

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

## <a name="specifying-special-characters"></a>Určení speciálních znaků

V názvu typu je identifikátor libovolný platný název určený pravidly jazyka.

Použijte zpětné lomítko (\\) jako řídicí znak pro oddělení následujících tokenů při použití jako součást IDENTIFIKÁTORu.

|Klíčové|Význam|
|-----------|-------------|
|\\,|Oddělovač sestavení|
|\\+|Oddělovač vloženého typu|
|\\&|Odkazový typ|
|\\*|Typ ukazatele.|
|\\[|Oddělovač dimenze pole.|
|\\]|Oddělovač dimenze pole.|
|\\.|Použití zpětného lomítka před tečkou pouze v případě, že se období používá ve specifikaci pole. Období v NamespaceSpec neberou zpětné lomítko.|
|v případě potřeby \\\|zpětného lomítka jako řetězcový literál.|

Všimněte si, že ve všech součástech token TypeSpec s výjimkou AssemblyNameSpec jsou mezery relevantní. V AssemblyNameSpec mezery před oddělovačem ', ' jsou relevantní, ale mezery za oddělovačem ', ' budou ignorovány.

Třídy reflexe, jako je například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí název pozměněný tak, aby se vrácený název mohl použít při volání <xref:System.Type.GetType%2A>, jako v `MyType.GetType(myType.FullName)`.

Například plně kvalifikovaný název pro typ může být `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.

Pokud byl obor názvů `Ozzy.Out+Back`, před znaménkem znaménka musí být uvozen zpětným lomítkem. V opačném případě analyzátor by ho interpretoval jako oddělovač vnořování. Reflexe generuje tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.

## <a name="specifying-assembly-names"></a>Určení názvů sestavení

Minimální informace požadované ve specifikaci názvu sestavení jsou textový název (identifikátor) sestavení. Identifikátor můžete sledovat pomocí čárkami oddělený seznam párů vlastnost/hodnota, jak je popsáno v následující tabulce. Názvy IDENTIFIKÁTORů by měly splňovat pravidla pro pojmenovávání souborů. V IDENTIFIKÁTORu se nerozlišují malá a velká písmena.

|Název vlastnosti|Popis|Povolené hodnoty|
|-------------------|-----------------|----------------------|
|**Verze**|Číslo verze sestavení|*Hlavní_verze. podverze. sestavení. revize*, kde *hlavní*, *vedlejší*, *sestavení*a *Revize* jsou celá čísla mezi 0 a 65535 včetně.|
|**PublicKey**|Úplný veřejný klíč|Řetězcová hodnota úplného veřejného klíče v šestnáctkovém formátu Zadejte nulový odkaz (**Nothing** v Visual Basic) k explicitnímu označení soukromého sestavení.|
|**PublicKeyToken**|Token veřejného klíče (8bitové bajtové hodnoty hash úplného veřejného klíče)|Řetězcová hodnota tokenu veřejného klíče v šestnáctkovém formátu. Zadejte nulový odkaz (**Nothing** v Visual Basic) k explicitnímu označení soukromého sestavení.|
|**Jazykových**|Jazyková verze sestavení|Jazyková verze sestavení ve formátu RFC-1766 nebo neutrální pro sestavení nezávislá na jazyce (nesatelitní).|
|**Uživatelská**|Vlastní binární rozsáhlý objekt (BLOB). Tato operace je aktuálně používána pouze v sestaveních generovaných [generátorem nativních bitových kopií (NGen)](../tools/ngen-exe-native-image-generator.md).|Vlastní řetězec používaný nástrojem generátor nativních bitových kopií pro oznamování mezipaměti sestavení, že sestavení, které se instaluje, je nativní bitová kopie, a proto je nutné ji nainstalovat do mezipaměti nativní bitové kopie. Označuje se také jako řetězec zap.|

Následující příklad ukazuje rozhraní **AssemblyName** pro jednoduše pojmenované sestavení s výchozí jazykovou verzí.

```csharp
com.microsoft.crypto, Culture=""
```

Následující příklad ukazuje plně určený odkaz pro silně pojmenované sestavení s jazykovou verzí "en".

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

Následující příklady každý ukazují částečně určené pole **AssemblyName**, které může být splněno buď silným, nebo jednoduše pojmenovaným sestavením.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

Následující příklady každý znázorňují částečně určený **AssemblyName**, který musí být splněn jednoduše pojmenovaným sestavením.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

V následujících příkladech je každý z nich zobrazen částečně určený **AssemblyName**, který musí být splněn silně pojmenovaným sestavením.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a>Určení obecných typů

SimpleTypeSpec\`číslo představuje otevřený obecný typ s parametry od 1 do *n* parametrů obecného typu. Chcete-li například získat odkaz na otevřený seznam obecných typů\<T > nebo uzavřený seznam obecných typů\<> řetězce, použijte ``Type.GetType("System.Collections.Generic.List`1")`` k získání odkazu na slovník obecného typu\<TKey, TValue > , použijte ``Type.GetType("System.Collections.Generic.Dictionary`2")``.

## <a name="specifying-pointers"></a>Určení ukazatelů

SimpleTypeSpec * představuje nespravovaný ukazatel. Například chcete-li získat ukazatel na typ MyType, použijte `Type.GetType("MyType*")`. Chcete-li získat ukazatel na ukazatel na typ MyType, použijte `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Zadání odkazů

SimpleTypeSpec & představuje spravovaný ukazatel nebo odkaz. Například pro získání odkazu na typ MyType použijte `Type.GetType("MyType &")`. Všimněte si, že na rozdíl od ukazatelů jsou odkazy omezeny na jednu úroveň.

## <a name="specifying-arrays"></a>Určení polí

V BNF gramatice se ReflectionEmitDimension vztahuje pouze na neúplné definice typu načtené pomocí <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Neúplné definice typu jsou <xref:System.Reflection.Emit.TypeBuilder> objekty vytvořené pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>, ale na kterých <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nebyl volán. ReflectionDimension lze použít k načtení jakékoli definice typu, která byla dokončena, tedy typu, který byl načten.

Pole jsou k dispozici v reflexi zadáním pořadí pole:

- `Type.GetType("MyArray[]")` získá pole s jednou dimenzí s 0 s dolní hranicí.

- `Type.GetType("MyArray[*]")` získá pole s jednou dimenzí, které má neznámou dolní mez.
- `Type.GetType("MyArray[][]")` získá pole dvourozměrného pole.

- `Type.GetType("MyArray[*,*]")` a `Type.GetType("MyArray[,]")` získá obdélníkové dvourozměrné pole s neznámými dolními mezemi.

Všimněte si, že z běhového bodu zobrazení, `MyArray[] != MyArray[*]`, ale u multidimenzionálních polí jsou oba zápisy ekvivalentní. To znamená, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` se vyhodnotí jako **true**.

Pro **modul ModuleBuilder. GetType**`MyArray[0..5]` označuje pole s jednou dimenzí, které má velikost 6, dolní mez 0. `MyArray[4…]` označuje pole s jednou dimenzí s neznámou velikostí a dolní mez 4.

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](viewing-type-information.md)
