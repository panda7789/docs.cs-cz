---
title: x:Static – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 8a14b00fe762d325028072cd0ea3eecf9b9206e3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083475"
---
# <a name="xstatic-markup-extension"></a>x:Static – rozšíření značek
Odkazuje na entitu kód statickou hodnotou, která je definována v [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– kompatibilní způsobem. Statická vlastnost, která je popsána slouží k poskytnutí hodnoty vlastností v XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
| | |  
|-|-|  
|`prefix`|Volitelné. Předpona, která odkazuje na mapovanou, jiné než výchozí obor názvů XAML. `prefix` je zobrazena explicitně ve využití vzhledem k tomu, že odkazujete zřídka statické vlastnosti, které pocházejí z výchozí obor názvů XAML. Viz poznámky.|  
|`typeName`|Požadováno. Název typu, který definuje požadovaný statický člen.|  
|`staticMemberName`|Požadováno. Jméno člena požadovanou statickou hodnotu (konstantu, statické vlastnosti, pole nebo hodnoty výčtu).|  
  
## <a name="remarks"></a>Poznámky  

Kód entita, na který odkazuje musí být jeden z následujících akcí:  
  
-   Konstanta  
-   Statická vlastnost  
-   Pole  
-   Hodnota výčtu

Určení jiné kód entitě, jako je například nestatické vlastnosti způsobí chybu kompilace při kompilaci kódu nebo výjimku během načítání analýzy XAML XAML.  

Můžete provést `x:Static` odkazy na statické pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML; to však vyžaduje mapování předpony. Obory názvů XAML jsou téměř vždy definována na kořenový element dokumentu XAML.  

Operace vyhledávání pro statické vlastnosti lze provést pomocí rozhraní .NET Framework XAML Services a jeho XAML čtečky a zapisovače XAML, když jsou spuštěné s výchozí kontext schématu XAML. Tento kontext schématu XAML můžete CLR reflexe uvést nezbytné statické hodnoty pro vytváření grafu objektu. `typeName` Zadejte je ve skutečnosti XAML název typu, nikoli název typu CLR, i když tyto jsou v podstatě stejný název, při použití výchozí kontext schématu XAML nebo při použití všech stávajících architektur implementace XAML založené na modulu CLR.  

Buďte opatrní při provedení `x:Static` odkazů, které nejsou přímo typ hodnoty vlastnosti. V XAML zpracování pořadí, zadané hodnoty z rozšíření značek není vyvolat převod další hodnoty. To platí i v případě vaší `x:Static` vytvoří odkaz na textový řetězec a převod hodnoty pro atribut hodnoty založené na textový řetězec obvykle dochází u tohoto konkrétního člena nebo pro všechny hodnoty členů návratového typu.  

Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `x:Static` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.StaticExtension.Member%2A> hodnoty základního <xref:System.Windows.Markup.StaticExtension> rozšíření třídy.  

Existují dva další použití XAML, které je technicky možný. Tato použití jsou však méně častý, protože je zbytečně podrobný:  

1.  Syntaxe elementu objektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2.  Atribut syntaxi pomocí explicitní vlastnost člena pro inicializačního řetězce.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

V implementaci rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.StaticExtension> třídy.  

`x:Static` je rozšíření značek. Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého procesoru XAML rozpozná, že rozšíření značek musí poskytovat hodnotu. Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek XAML přehled](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Výchozí obor názvů XAML můžete použít pro programování WPF obsahuje mnoho užitečných statické vlastnosti, a většina užitečné statické vlastnosti mají podporu například převaděče typů, které usnadňují použití bez nutnosti `{x:Static}` . Pro statické vlastnosti je nutné mapovat předponu pro obor názvů XAML, pokud platí jedna z následujících akcí:  
  
-   Odkazujete na typ, který existuje ve WPF, ale není součástí výchozí obor názvů XAML pro WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Toto je celkem běžné scénáře použití `x:Static`. Například můžete použít `x:Static` odkaz s XAML mapování oboru názvů <xref:System> CLR obor názvů a mscorlib sestavení, aby bylo možné odkazovat statické vlastnosti <xref:System.Environment> třídy.  
  
-   Typ se odkazuje z vlastního sestavení.  
  
-   Typ, který existuje v sestavení WPF, se odkazuje, ale tento typ je v oboru názvů CLR, který nebyl namapován jako součást výchozí WPF XAML obor názvů. Mapování oborů názvů CLR do výchozí obor názvů XAML pro WPF se provádí pomocí definice v různých sestaveních WPF (Další informace o tento koncept najdete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Mapované na jiných oborů názvů CLR může existovat, pokud se tento obor názvů CLR skládá převážně z definice tříd, které nejsou určeny obvykle pro XAML, jako například <xref:System.Windows.Threading>.  
  
 Další informace o tom, jak používat předpony a obory názvů XAML pro WPF naleznete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [x:Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
