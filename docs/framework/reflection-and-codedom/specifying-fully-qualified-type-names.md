---
title: "Určení úplných názvů typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6759e7b62f4083f6d53663385398baf098f2676f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-fully-qualified-type-names"></a>Určení úplných názvů typů
Je nutné zadat názvy typů tak, aby měl platný vstup pro různé operace reflexe. Název plně kvalifikovaný typ se skládá z specifikace název sestavení, oboru názvů a název typu. Zadejte název specifikace jsou používány metody, jako <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, a <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.  
  
## <a name="backus-naur-form-grammar-for-type-names"></a>Backus-Naur – gramatika formuláře pro názvy typů  
 Backus-Naur formuláře (BNF) definuje syntaxe formální jazyky. Následující tabulka uvádí BNF lexikální pravidla, které popisují, jak rozpoznat platné zadání. Terminály (elementy, které nejsou další reducible) se zobrazí velkými písmeny. Terminálově nezávislých (elementy, které jsou dále reducible) jsou uvedeny v řetězcích rozlišením malých a samostatně uvozovkách, ale jednoduché uvozovky (') není součástí syntaxe sám sebe. Svislou čarou (&#124;) označuje pravidla, která mají dílčích pravidel.  
  
|BNF – gramatika z úplné názvy typů|  
|-----------------------------------------------|  
|Typ TypeSpec: = ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec: = SimpleTypeSpec 'a'|  
|SimpleTypeSpec: = PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec: = SimpleTypeSpec ' *'|  
|ArrayTypeSpec: = SimpleTypeSpec [ReflectionDimension]<br /><br /> &#124;     SimpleTypeSpec [ReflectionEmitDimension]|  
|ReflectionDimension: = ' *'<br /><br /> &#124;     ReflectionDimension ReflectionDimension ','<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension: = ' *'<br /><br /> &#124;     Číslo '..' Číslo<br /><br /> &#124;     Číslo '...<br /><br /> &#124;     ReflectionDimension ReflectionDimension ','<br /><br /> &#124;     NOTOKEN|  
|Číslo: = [0-9] +|  
|TypeName: = NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName AssemblyNameSpec ','|  
|NamespaceTypeName: = NestedTypeName<br /><br /> &#124;     NamespaceSpec '. " NestedTypeName|  
|NestedTypeName: = IDENTIFIKÁTOR<br /><br /> &#124;     NestedTypeName IDENTIFIKÁTOR '+'|  
|NamespaceSpec: = IDENTIFIKÁTOR<br /><br /> &#124;     NamespaceSpec '. " IDENTIFIKÁTOR|  
|AssemblyNameSpec: = IDENTIFIKÁTOR<br /><br /> &#124;     IDENTIFIKÁTOR AssemblyProperties ','|  
|AssemblyProperties: = AssemblyProperty<br /><br /> &#124;     AssemblyProperties AssemblyProperty ','|  
|AssemblyProperty: = AssemblyPropertyName '=' AssemblyPropertyValue|  
  
## <a name="specifying-special-characters"></a>Zadání speciální znaky  
 Název typu je IDENTIFIKÁTOR libovolný platný název určit pravidly jazyka.  
  
 Použít zpětné lomítko (\\) jako řídicí znak oddělit následující klíčová slova, pokud se používá jako součást IDENTIFIKÁTORU.  
  
|Token|Význam|  
|-----------|-------------|  
|\\,|Oddělovač sestavení.|  
|\\+|Vnořené typy oddělovače.|  
|\\&|Typ odkazu.|  
|\\*|Typ ukazatele.|  
|\\[|Pole dimenze oddělovač.|  
|\\]|Pole dimenze oddělovač.|  
|\\.|Použijte zpětné lomítko před dobou pouze v případě, že období se používá v specifikace pole. Tečky v NamespaceSpec nepřebírají zpětné lomítko.|  
|\\\|Zpětné lomítko, v případě potřeby jako řetězcový literál.|  
  
 Upozorňujeme, že v všechny součásti typ TypeSpec s výjimkou AssemblyNameSpec, jsou relevantní prostory. V AssemblyNameSpec jsou relevantní prostory před oddělovač ',', ale mezery po ',' oddělovač jsou ignorovány.  
  
 Reflexe třídy, jako například <xref:System.Type.FullName%2A?displayProperty=nameWithType>, vrátí pozměnění název tak, aby vrácený název lze použít v volání <xref:System.Type.GetType%2A>jako v `MyType.GetType(myType.FullName)`.  
  
 Například může být plně kvalifikovaný název typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.  
  
 Pokud byly oboru názvů `Ozzy.Out+Back`, pak na symbol plus musí předcházet zpětné lomítko. Jinak by analyzátor toto jako oddělovač vnoření. Reflexe vysílá tento řetězec jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.  
  
## <a name="specifying-assembly-names"></a>Určení názvy sestavení  
 Minimální informace požadované specifikací název sestavení je textový název sestavení (IDENTIFIER). IDENTIFIKÁTOR můžete provést pomocí seznam oddělený čárkami dvojic vlastnost/hodnota, jak je popsáno v následující tabulce. IDENTIFIKÁTOR pojmenování by mělo vycházet pravidla pro pojmenovávání souborů. IDENTIFIKÁTOR nerozlišuje velká a malá písmena.  
  
|Název vlastnosti|Popis|Povolené hodnoty|  
|-------------------|-----------------|----------------------|  
|**Verze**|Číslo verze sestavení|*Major.Minor.Build.Revision*, kde *hlavní*, *menší*, *sestavení*, a *revize* jsou celá čísla mezi 0 a 65535 (včetně).|  
|**PublicKey**|Úplné veřejný klíč|Řetězec hodnotu úplné veřejný klíč v šestnáctkovém formátu. Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.|  
|**PublicKeyToken**|Token veřejného klíče (8 bajtů hash veřejného klíče)|Hodnota tokenu veřejného klíče v šestnáctkovém formátu řetězec. Zadejte odkaz s hodnotou null (**nic** v jazyce Visual Basic) explicitně udávajících privátní sestavení.|  
|**Jazyková verze**|Jazyková verze sestavení|Jazyková verze sestavení ve formátu RFC 1766, nebo "neutrální" pro sestavení nezávislé na jazyku (nonsatellite).|  
|**Vlastní**|Vlastní binární rozsáhlý objekt (binární rozsáhlý OBJEKT). To se aktuálně používá jenom v sestavení, které jsou generované [generátor (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Vlastní řetězec nástroje Generátor pro mezipaměť sestavení upozornit, že je nativních bitových kopií sestavení instaluje a proto má být nainstalován v mezipaměť nativních bitových kopií. Také nazývá zap řetězec.|  
  
 Následující příklad ukazuje **AssemblyName** pro jednoduše pojmenované sestavení s výchozí jazykovou verzi.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 Následující příklad ukazuje plně zadaný odkaz pro silně pojmenované sestavení s jazykovou verzi "en".  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 Následující příklady ukazují, částečně zadané **AssemblyName**, který může obsloužit silné nebo jednoduše pojmenované sestavení.  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit jednoduše pojmenované sestavení.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 Následující příklady ukazují, částečně zadané **AssemblyName**, které musí splnit silně pojmenované sestavení.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a>Určení ukazatele  
 SimpleTypeSpec * představuje nespravovaný ukazatel. Například ukazatel na typ MyType získáte pomocí `Type.GetType("MyType*")`. Ukazatel na ukazatel na typ MyType získáte pomocí `Type.GetType("MyType**")`.  
  
## <a name="specifying-references"></a>Určení odkazy  
 SimpleTypeSpec & reprezentuje spravované ukazatel nebo odkaz. Například pokud chcete získat odkaz na typ MyType, použijte `Type.GetType("MyType &")`. Všimněte si, že na rozdíl od ukazatele, odkazy jsou omezeny na jedné úrovni.  
  
## <a name="specifying-arrays"></a>Určení pole  
 V BNF – gramatika, ReflectionEmitDimension platí pouze pro neúplné typ definice načten pomocí <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Jsou neúplné typ definice <xref:System.Reflection.Emit.TypeBuilder> objekty, které jsou vytvářeny pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na kterém <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nebyla volána. ReflectionDimension umožňuje načíst všechny definice typu, která byla dokončena, který je typ, který byl načten.  
  
 Pole jsou přístupné v reflexe určení pořadí pole:  
  
-   `Type.GetType("MyArray[]")`Získá pole jedním dimenze s 0 dolní mez.  
  
-   `Type.GetType("MyArray[*]")`Získá pole jedním dimenze s neznámou dolní mez.  
  
-   `Type.GetType("MyArray[][]")`Získá pole dvourozměrná pole.  
  
-   `Type.GetType("MyArray[*,*]")`a `Type.GetType("MyArray[,]")` získá obdélníková dvourozměrná pole s neznámou dolní meze.  
  
 Všimněte si, že se z modulu runtime hlediska, `MyArray[] != MyArray[*]`, ale pro vícerozměrná pole jsou ekvivalentní zápisy dva. To znamená `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` vyhodnotí jako **true**.  
  
 Pro **ModuleBuilder.GetType**, `MyArray[0..5]` označuje jeden dimenze pole s velikostí 6, nižší vázán 0. `MyArray[4…]`Určuje pole dimenze jeden neznámý velikost a dolní hranice 4.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
