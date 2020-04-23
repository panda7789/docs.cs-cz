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
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072023"
---
# <a name="xstatic-markup-extension"></a>x:Static – rozšíření značek

Odkazuje na libovolnou statickou entitu kódu podle hodnoty, která je definována způsobem kompatibilním se specifikací common language (CLS). Statickou vlastnost, na kterou se odkazuje, lze použít k poskytnutí hodnoty vlastnosti v xaml.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>Hodnoty XAML

| | |
|-|-|
|`prefix`|Nepovinný parametr. Předpona, která odkazuje na mapovaný, nevýchozí obor názvů XAML. `prefix`je v použití explicitně zobrazena, protože zřídka kdy odkazujete na statické vlastnosti, které pocházejí z výchozího oboru názvů XAML. Viz Poznámky.|
|`typeName`|Povinná hodnota. Název typu, který definuje požadovaný statický člen.|
|`staticMemberName`|Povinná hodnota. Název členu požadované statické hodnoty (konstanta, statická vlastnost, pole nebo hodnota výčtu).|

## <a name="remarks"></a>Poznámky

Entita kódu, na kterou se odkazuje, musí být jedna z následujících:

- Konstanta
- Statická vlastnost
- Pole
- Hodnota výčtu

Zadání jakékoli jiné entity kódu, jako je například nestatická vlastnost, způsobí chybu v době kompilace, pokud je zkompilován kód XAML nebo výjimka analýzy doby načítání XAML.

Můžete odkazovat `x:Static` na statická pole nebo vlastnosti, které nejsou ve výchozím oboru názvů XAML pro aktuální dokument XAML. to však vyžaduje mapování předpony. Obory názvů XAML jsou téměř vždy definovány v kořenovém prvku dokumentu XAML.

Vyhledávací operace pro statické vlastnosti mohou být prováděny službou .NET XAML Services a jejími čtečkami XAML a zapisovači XAML, pokud jsou spuštěny s výchozím kontextem schématu XAML. Tento kontext schématu XAML můžete použít odraz CLR poskytnout potřebné statické hodnoty pro konstrukci grafu objektu. Vámi `typeName` zadaný je ve skutečnosti název typu XAML, nikoli název typu CLR, i když se jedná v podstatě o stejný název při použití výchozího kontextu schématu XAML nebo při použití všech existujících rozhraní pro implementaci XAML založených na CLR.

Buďte opatrní při `x:Static` odkazech, které nejsou přímo typu hodnoty vlastnosti. V posloupnosti zpracování XAML zadaných hodnot z rozšíření značek nevyvolávají převod další hodnoty. To platí i `x:Static` v případě, že váš odkaz vytvoří textový řetězec a převod hodnoty pro hodnoty atributů na základě textového řetězce obvykle dochází buď pro konkrétního člena, nebo pro všechny členské hodnoty návratového typu.

Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `x:Static` po přidělení řetězce <xref:System.Windows.Markup.StaticExtension.Member%2A> identifikátoru jako <xref:System.Windows.Markup.StaticExtension> hodnota základní třídy rozšíření.

Existují dvě další použití XAML, které jsou technicky možné. Tato použití jsou však méně časté, protože jsou zbytečně podrobné:

01. Syntaxe prvku objektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Syntaxe atributu s explicitní vlastností Member pro inicializační řetězec.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

V implementaci služby .NET XAML Services je zpracování <xref:System.Windows.Markup.StaticExtension> pro toto rozšíření značek definováno třídou.

`x:Static`je rozšíření značky. Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí poskytnout hodnotu. Další informace o rozšířeních značek naleznete v [tématu Markup Extensions for XAML Overview](markup-extensions-overview.md).

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Výchozí obor názvů XAML, který používáte pro programování WPF, neobsahuje mnoho užitečných statických vlastností a většina `{x:Static}` užitečných statických vlastností má podporu, například převaděče typů, které usnadňují použití bez nutnosti . Pro statické vlastnosti je nutné mapovat předponu pro obor názvů XAML, pokud je splněna jedna z následujících podmínek:

- Odkazujete na typ, který existuje v WPF, ale není součástí výchozího oboru`http://schemas.microsoft.com/winfx/2006/xaml/presentation`názvů XAML pro WPF ( ). Toto je poměrně běžný `x:Static`scénář pro použití . Můžete například použít `x:Static` odkaz s mapováním oboru názvů <xref:System> XAML na obor názvů CLR a sestavení mscorlib, abyste mohli odkazovat na statické vlastnosti <xref:System.Environment> třídy.

- Odkazujete na typ z vlastního sestavení.

- Odkazujete na typ, který existuje v sestavení WPF, ale tento typ je v oboru názvů CLR, který nebyl namapován jako součást výchozího oboru názvů WPF XAML. Mapování oborů názvů CLR do výchozího oboru názvů XAML pro WPF se provádí podle definic v různých sestaveních WPF (další informace o tomto konceptu naleznete v [tématu XAML Namespaces a Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Nemapované obory názvů CLR mohou existovat, pokud se tento obor názvů CLR skládá převážně z <xref:System.Windows.Threading>definic tříd, které nejsou obvykle určeny pro XAML, například .

Další informace o použití předpon a oborů názvů XAML pro WPF naleznete v [tématu XAML Obory názvů a Mapování oboru názvů pro WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

## <a name="see-also"></a>Viz také

- [x:Type – rozšíření značek](xtype-markup-extension.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
