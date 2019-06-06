---
title: Obecné typy v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 6ca7986513d1a6cbe160ca1a0af6699c323aac7e
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690652"
---
# <a name="generics-in-xaml"></a>Obecné typy v jazyku XAML
Rozhraní .NET Framework XAML Services jak je implementován v oboru názvů System.Xaml poskytuje podporu pro používání obecných typů CLR. Tato podpora zahrnuje určení omezení obecných typů jako argument typu a vynucování omezení voláním příslušné `Add` metodu pro případy, obecné kolekce. Toto téma popisuje aspekty pomocí a odkazování na obecné typy v XAML.  
  
## <a name="xtypearguments"></a>x:TypeArguments  
 `x:TypeArguments` definoval direktivy jazyka XAML. Když se používá jako člen typu XAML, který se zálohuje pomocí obecného typu, `x:TypeArguments` předá omezení zadejte argumenty obecného konstruktoru zálohování. Odkaz syntaxe, které se vztahují na rozhraní .NET Framework XAML Services využívání `x:TypeArguments`, což zahrnuje příklady syntaxe, naleznete v tématu [x: TypeArguments – direktiva](x-typearguments-directive.md).  
  
 Protože `x:TypeArguments` přijímá řetězec a má typ převaděče zálohování, je obvykle deklarované v použití atributu XAML.  
  
 V datovém proudu uzlu XAML informace deklaroval `x:TypeArguments` můžete získat <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> na `StartObject` pozici v datovém proudu uzlu. Návratová hodnota <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> je seznam <xref:System.Xaml.XamlType> hodnoty. Určení, zda typ XAML představuje obecný typ nelze realizovat voláním <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Pravidla a pravidla týkající se syntaxe pro obecné typy v XAML  
 V XAML musí být vždy reprezentována obecného typu jako omezené obecný; bez omezení obecné není nikdy k dispozici v typu systému XAML nebo datový proud uzlu XAML, nemůže být vyjádřena v kódu XAML. Obecný může být odkazováno v syntaxi atributu XAML pro případy, kdy je omezení vnořený typ obecný, se na ně odkazovat `x:TypeArguments`, nebo pro případy, kde `x:Type` poskytuje odkaz na typ CLR pro obecného typu. To je podporováno prostřednictvím <xref:System.Xaml.Schema.XamlTypeTypeConverter> třídy definované v rozhraní .NET Framework XAML Services.  
  
 XAML atributu forma syntaxe umožněné <xref:System.Xaml.Schema.XamlTypeTypeConverter> mění typické MSIL / CLR syntaxe vytváření názvů, které používá ostré závorky pro typy a omezení obecných typů a místo toho nahradí závorky pro container omezení. Příklad najdete v tématu [x: TypeArguments – direktiva](x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Obecné typy a funkce XAML 2009  
 Pokud používáte XAML 2009 místo mapování CLR základní typy získat primitiv jazyka XAML typy, můžete použít [předdefinovaných typů XAML 2009](built-in-types-for-common-xaml-language-primitives.md) jako informačních položek v `x:TypeArguments`. Například můžete deklarovat následující (předpona mapování nezobrazují, ale `x` je obor názvů jazyka XAML XAML pro XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Podpora obecných typů v projektech WPF a další architektury v3.5  
 XAML 2006 využití při specificky cílené na WPF [x: Class](x-class-directive.md) musí se poskytnout i na stejný prvek jako `x:TypeArguments`, a tento element musí být kořenový element v dokumentu XAML. Kořenový element musí být namapovaný na obecný typ s alespoň jeden argument typu. Příklad: <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Možná řešení pro podporu obecných použití patří definování rozšíření vlastního kódu, která vrací obecných typů, nebo které uvádějí zabalení třídy definice, která je odvozena od obecného typu, ale sloučí obecná omezení v definici třídy.  
  
 V WPF a cílí na rozhraní .NET Framework 4, můžete použít funkce XAML 2009 spolu s `x:TypeArguments`, ale pouze pro volný XAML (XAML, který není kompilována značka). Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.  
  
 Vlastní pracovní postupy v modelu Windows Workflow Foundation pro .NET Framework 3.5 nepodporují použití obecných XAML.  
  
## <a name="see-also"></a>Viz také:

- [x:TypeArguments – direktiva](x-typearguments-directive.md)
- [x:Class – direktiva](x-class-directive.md)
- [Předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md)
