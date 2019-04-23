---
title: Obecné typy v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9263edf18872f510f5f2f4e3e9cb793e45c5d0b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221597"
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
  
 V WPF a cílení [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je možné použít funkce XAML 2009 spolu s `x:TypeArguments`, ale pouze pro volný XAML (XAML, který není kompilována značka). Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.  
  
 Vlastní pracovní postupy v modelu Windows Workflow Foundation pro [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] nepodporují použití obecných XAML.  
  
## <a name="see-also"></a>Viz také:

- [x:TypeArguments – direktiva](x-typearguments-directive.md)
- [x:Class – direktiva](x-class-directive.md)
- [Předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md)
