---
title: "x:Static – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d006c8d0937a454dcbe092dcc3e35c4644088e59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xstatic-markup-extension"></a>x:Static – rozšíření značek
Každá entita kód statické podle hodnoty, která je definována v odkazuje [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– kompatibilní způsob. Statické vlastnosti, která se odkazuje slouží k poskytování hodnotou vlastnosti v jazyce XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`prefix`|Volitelné. Předponu, která odkazuje na namapované, jiné než výchozí obor názvů jazyka XAML. `prefix`ukazuje explicitně využití zřídka odkazovat statické vlastnosti, které pocházejí z oboru názvů jazyka XAML výchozí. V části poznámky.|  
|`typeName`|Požadováno. Název typu, který definuje požadované statický člen.|  
|`staticMemberName`|Požadováno. Název člena požadovanou statickou hodnotu (konstanta, pomocí statické vlastnosti, pole nebo hodnotou výčtu).|  
  
## <a name="remarks"></a>Poznámky  
 Entity kód, který se odkazuje musí mít jednu z následujících akcí:  
  
-   Konstanta  
  
-   Statické vlastnosti  
  
-   Pole  
  
-   Hodnota výčtu  
  
 Chyba kompilace zadání dalších kód entitu, jako je například nestatické vlastnost, dojde, pokud je XAML kompilaci kódu, nebo k výjimce při načtení analýzy XAML.  
  
 Můžete provést `x:Static` odkazy na statických polí nebo vlastnosti, které nejsou ve výchozí obor názvů jazyka XAML pro aktuální dokument XAML; to však vyžaduje mapování předpony. Obory názvů jazyka XAML jsou téměř vždy definována v kořenovém elementu dokumentu XAML.  
  
 Operace vyhledávání pro statické vlastnosti můžete provést pomocí rozhraní .NET Framework XAML Services a jeho XAML čtení a zápis XAML, pokud jsou spuštěny s výchozí kontext schématu XAML. Tento kontext schématu XAML zajistit potřebné statické hodnoty pro vytváření objektů grafu použít reflexe CLR. `typeName` Zadejte je ve skutečnosti XAML název typu, nikoli název typu CLR, i když tyto jsou v podstatě stejný název, když používáte výchozí kontext schématu XAML nebo při použití architektury všechny existující implementace XAML na základě CLR.  
  
 Buďte opatrní při provádění `x:Static` odkazy, které nejsou přímo typ vlastnosti na hodnotu. V XAML zpracování pořadí, zadat hodnoty z rozšíření značek Nevolejte převod další hodnoty. To platí i v případě vaší `x:Static` odkaz vytvoří textový řetězec a převod hodnoty pro hodnoty atributů, které jsou založené na textový řetězec obvykle dochází pro konkrétní člena nebo všechny hodnoty členů návratového typu.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `x:Static` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.StaticExtension.Member%2A> hodnotu základní <xref:System.Windows.Markup.StaticExtension> rozšíření třídy.  
  
 Existují dva další XAML použití, které jsou technicky možné. Tyto použití jsou však méně častých, protože je zbytečně podrobné:  
  
 **Objekt elementu syntaxe:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`  
  
 **Atribut syntaxi společně s explicitní vlastnost člena pro inicializačního řetězce:** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`  
  
 Implementace rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.StaticExtension> třídy.  
  
 `x:Static`je rozšíření značek. Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musíte zadat hodnotu. Další informace o rozšíření značek najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Výchozí obor názvů jazyka XAML použijete pro programování WPF neobsahuje mnoho užitečné statické vlastnosti a většina užitečné statické vlastnosti má podpory, jako je například převaděče typů, které usnadňují použití bez nutnosti `{x:Static}` . Statické vlastnosti je nutné mapovat předponu pro obor názvů jazyka XAML, pokud platí jedna z následujících akcí:  
  
-   Je odkazováno na typ, který existuje v grafickém subsystému WPF, ale není součástí výchozí obor názvů jazyka XAML pro grafický subsystém WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Toto je celkem běžné scénáře použití `x:Static`. Například můžete použít `x:Static` odkaz s mapování oboru názvů jazyka XAML do <xref:System> sestavení CLR obor názvů a mscorlib – Chcete-li odkazovat na statické vlastnosti <xref:System.Environment> třídy.  
  
-   Typ odkazují z vlastního sestavení.  
  
-   Je odkazováno na typ, který existuje v sestavení WPF, ale tento typ je v rámci oboru názvů CLR, který nebyl namapovaný jako součást WPF výchozí obor názvů jazyka XAML. Mapování obory názvů CLR do výchozí obor názvů jazyka XAML pro grafický subsystém WPF provádí definice v různých sestavení grafického subsystému WPF (Další informace o tento koncept najdete v tématu [obory názvů jazyka XAML a mapování Namespace pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Mapované bez obory názvů CLR může existovat, pokud tento obor názvů CLR tvoří většinou definice tříd, které nejsou určeny obvykle pro jazyk XAML, jako například <xref:System.Windows.Threading>.  
  
 Další informace o tom, jak používat předpony a obory názvů jazyka XAML pro grafický subsystém WPF najdete v tématu [obory názvů jazyka XAML a Namespace mapování pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [x: Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Typy migrované z grafického subsystému WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
