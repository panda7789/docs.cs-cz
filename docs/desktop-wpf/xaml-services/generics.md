---
title: Obecné typy v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071736"
---
# <a name="generics-in-xaml"></a>Obecné typy v jazyku XAML

Služby .NET XAML, jak jsou implementovány v rámci <xref:System.Xaml?displayProperty=fullName> poskytuje podporu pro použití obecných typů CLR. Tato podpora zahrnuje určení omezení obecných typů jako argument typu a vynucení omezení voláním příslušné `Add` metody pro případy obecné kolekce. Toto téma popisuje aspekty použití a odkazování na obecné typy v XAML.

## <a name="xtypearguments"></a>x:Argumenty typu

`x:TypeArguments`je směrnice definovaná jazykem XAML. Pokud se používá jako člen typu XAML, který je zálohován obecným typem, `x:TypeArguments` předá argumenty typu omezující typu obecného záložnímu konstruktoru. Pro referenční syntaxi, která se týká použití služby `x:TypeArguments`.NET XAML Services , která obsahuje příklady syntaxe, viz [x:TypeArguments Directive](xtypearguments-directive.md).

Protože `x:TypeArguments` trvá řetězec a má podporu převaděče typu, je obvykle deklarován v xaml použití jako atribut.

V datovém proudu uzlu XAML `x:TypeArguments` informace deklarované lze získat z <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> na `StartObject` pozici v datovém proudu uzlu. Vrácená hodnota <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> je seznam <xref:System.Xaml.XamlType> hodnot. Určení, zda typ XAML představuje obecný typ <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>lze provést voláním .

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Pravidla a syntaktické konvence pro obecné typy v XAML

V XAML obecný typ musí být vždy reprezentován jako omezený obecný. Obecný bez omezení není nikdy přítomen v systému typu XAML nebo datového proudu uzlu XAML a nemůže být reprezentován v značkách XAML. Obecný lze odkazovat v rámci syntaxe atributu XAML pro případy, kdy se `x:TypeArguments`jedná o `x:Type` vnořené omezení typu obecného, na které odkazuje , nebo v případech, kdy poskytuje odkaz na typ CLR pro obecný typ. Odkazování na obecné typy <xref:System.Xaml.Schema.XamlTypeTypeConverter> je podporováno prostřednictvím třídy definované službou .NET XAML Services.

Formulář syntaxe atributu XAML povolený změnou <xref:System.Xaml.Schema.XamlTypeTypeConverter> typické konvence syntaxe MSIL / CLR, která používá úhlové závorky pro typy a omezení obecných typů, a místo toho nahrazuje závorky pro kontejner omezení. Příklad viz [x:TypeArguments Directive](xtypearguments-directive.md).

## <a name="generics-and-xaml-2009-features"></a>Obecné typy a funkce XAML 2009

Pokud používáte XAML 2009 namísto mapování clr základní typy získat XAML typy pro základní jazyk běžné jazykové primitivy, můžete použít [XAML 2009 předdefinované typy](types-for-primitives.md) jako informační položky v `x:TypeArguments`. Můžete například deklarovat následující (mapování předpony `x` nejsou zobrazena, ale je xaml jazyk XAML obor názvů pro XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>Podpora obecných typů v wpf

Pro použití XAML 2006 při konkrétně cílení WPF, [x:Class](xclass-directive.md) musí `x:TypeArguments`být také k dispozici na stejný prvek jako , a tento prvek musí být kořenový prvek v dokumentu XAML. Kořenový prvek musí být mapován na obecný typ s alespoň jedním argumentem typu. Příklad: <xref:System.Windows.Navigation.PageFunction%601>.

Mezi možná zástupná řešení pro podporu obecných použití patří definování vlastního rozšíření značek, které může vrátit obecné typy, nebo poskytnutí definice třídy obtékání, která je odvozena od obecného typu, ale sloučí obecné omezení v definici vlastní třídy.

Ve WPF můžete používat funkce XAML 2009 společně s `x:TypeArguments`, ale pouze pro volné XAML (XAML, který není zkompilován značky). XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.

Vlastní pracovní postupy v systému Windows Workflow Foundation pro rozhraní .NET Framework 3.5 nepodporují obecné použití XAML.

## <a name="see-also"></a>Viz také

- [x:TypeArguments – direktiva](xtypearguments-directive.md)
- [x:Class – direktiva](xclass-directive.md)
- [Předdefinované typy obecných primitiv jazyka XAML](types-for-primitives.md)
