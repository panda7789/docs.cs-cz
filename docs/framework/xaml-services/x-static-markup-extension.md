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
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733356"
---
# <a name="xstatic-markup-extension"></a>x:Static – rozšíření značek
Odkazuje na libovolnou entitu kódu static podle hodnoty, která je definována v jazyce CLS (Common Language Specification). Odkazovaná statická vlastnost může být použita k poskytnutí hodnoty vlastnosti v jazyce XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
| | |  
|-|-|  
|`prefix`|Volitelné. Předpona, která odkazuje na namapovaný, nevýchozí obor názvů XAML. `prefix` se zobrazuje explicitně v použití, protože zřídka odkazujete na statické vlastnosti, které pocházejí z výchozího oboru názvů XAML. Viz poznámky.|  
|`typeName`|Požadováno. Název typu, který definuje požadovaného statického člena.|  
|`staticMemberName`|Požadováno. Název požadovaného člena statické hodnoty (konstanta, statická vlastnost, pole nebo hodnota výčtu).|  
  
## <a name="remarks"></a>Poznámky  

Odkazovaná entita kódu musí být jedna z následujících:  
  
- Konstanta  
- Statická vlastnost  
- Pole  
- Hodnota výčtu

Určení jakékoli jiné entity kódu, jako je například nestatická vlastnost, způsobí chybu při kompilaci, je-li kód XAML zkompilován, nebo výjimka při analýze při načítání jazyka XAML.  

Můžete nastavit `x:Static` odkazy na statická pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML. to však vyžaduje mapování předpony. Obory názvů XAML jsou téměř vždy definovány u kořenového prvku dokumentu XAML.  

Operace vyhledávání statických vlastností lze provádět pomocí .NET Framework služby XAML a jejich čteček XAML a zapisovače XAML, pokud jsou spuštěny s výchozím kontextem schématu XAML. Tento kontext schématu XAML může použít reflexi CLR k poskytnutí nezbytných statických hodnot pro vytváření grafů objektů. `typeName`, které zadáte, je jako název typu XAML, nikoli název typu CLR, i když jsou v podstatě stejný název při použití výchozího kontextu schématu XAML nebo při použití všech stávajících rozhraní implementací XAML založených na CLR.  

Při provádění `x:Static` odkazů, které nejsou přímo typu hodnoty vlastnosti, buďte opatrní. V sekvenci zpracování XAML poskytují hodnoty z rozšíření značek nevyvolávají další převod hodnoty. To platí i v případě, že `x:Static` odkaz vytvoří textový řetězec a převod hodnoty atributů na základě textového řetězce obvykle probíhá buď pro tento konkrétní člen, nebo pro jakékoli členské hodnoty návratového typu.  

Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `x:Static` identifikátoru je přiřazen jako hodnota <xref:System.Windows.Markup.StaticExtension.Member%2A> základní třídy rozšíření <xref:System.Windows.Markup.StaticExtension>.  

Existují dva další použití XAML, které jsou technicky možné. Tato použití jsou ale méně společná, protože jsou zbytečně podrobná:  

1. Syntaxe elementu objektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Syntaxe atributu s explicitní vlastností member pro inicializační řetězec

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

V implementaci .NET Framework XAML Services je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.Markup.StaticExtension>.  

`x:Static` je rozšíření značek. Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí poskytovat hodnotu. Další informace o rozšíření značek naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Výchozí obor názvů jazyka XAML, který použijete pro programování WPF, neobsahuje mnoho užitečných statických vlastností a většina užitečných statických vlastností podporuje například převaděče typu, které umožňují použití bez nutnosti `{x:Static}`. V případě statických vlastností je nutné namapovat předponu pro obor názvů XAML, pokud je splněna jedna z následujících hodnot:  
  
- Odkazujete na typ, který existuje v WPF, ale není součástí výchozího oboru názvů XAML pro WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`). Toto je poměrně běžný scénář pro použití `x:Static`. Například můžete použít `x:Static` odkaz s mapováním oboru názvů XAML na <xref:System> obor názvů CLR a sestavení mscorlib, aby odkazovaly na statické vlastnosti třídy <xref:System.Environment>.  
  
- Odkazujete na typ z vlastního sestavení.  
  
- Odkazujete na typ, který existuje v sestavení WPF, ale tento typ je v rámci oboru názvů CLR, který nebyl namapován, aby byl součástí výchozího oboru názvů jazyka XAML WPF. Mapování oborů názvů CLR na výchozí obor názvů XAML pro WPF je prováděno definicemi v různých sestaveních WPF (Další informace o tomto konceptu naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Nemapované obory názvů CLR mohou existovat, pokud je tento obor názvů CLR složen hlavně z definic třídy, které nejsou obvykle určeny pro jazyk XAML, například <xref:System.Windows.Threading>.  
  
 Další informace o tom, jak používat předpony a obory názvů XAML pro WPF, naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [x:Type – rozšíření značek](x-type-markup-extension.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
