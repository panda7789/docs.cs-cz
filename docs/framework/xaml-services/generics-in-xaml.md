---
title: Obecné typy v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: faef74c57ac5ff9e3d4162accfc6552db55715bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generics-in-xaml"></a>Obecné typy v jazyku XAML
Rozhraní .NET Framework XAML Services jak jsou implementované ve System.Xaml poskytuje podporu pro použití obecných typů CLR. Tato podpora zahrnuje určení omezení obecných typů jako argument typu a vynucující omezení voláním odpovídající `Add` metoda pro obecnou kolekci případy. Toto téma popisuje aspekty pomocí a odkazování na obecné typy v jazyce XAML.  
  
## <a name="xtypearguments"></a>x: TypeArguments –  
 `x:TypeArguments` direktivu definované jazyk XAML. Pokud se používá jako člen skupiny typ jazyka XAML, který je zálohovaný díky obecného typu `x:TypeArguments` předává chovaly zadejte argumenty obecného konstruktoru zálohování. Pro odkaz na syntaxi, která se vztahují na rozhraní .NET Framework XAML Services použití `x:TypeArguments`, což zahrnuje příklady syntaxe, najdete v části [x: TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Protože `x:TypeArguments` přebírá řetězec a má základní typ převaděče, je obvykle deklarovaný XAML využití jako atribut.  
  
 V datový proud uzlu XAML informace deklarovaná `x:TypeArguments` lze získat z <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> na `StartObject` pozici v datovém proudu uzlu. Návratová hodnota <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> je seznam <xref:System.Xaml.XamlType> hodnoty. Rozhodnutí o tom, jestli typ jazyka XAML představuje obecného typu můžete provedeny voláním <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Pravidla a pravidla týkající se syntaxe pro obecné typy v jazyce XAML  
 V jazyce XAML musí být vždy reprezentován obecného typu jako omezené obecného; neomezeným obecného je nikdy k dispozici v systému typu XAML nebo datový proud uzlu XAML a není možné vyjádřit v XAML značek. Obecný může být odkazováno v rámci syntaxe atribut XAML, případech, kdy je omezení vnořené typy obecný odkazují `x:TypeArguments`, nebo pro případy, kdy `x:Type` poskytuje odkaz na typ CLR pro obecný typ. To je podporováno prostřednictvím <xref:System.Xaml.Schema.XamlTypeTypeConverter> třídy definované rozhraní .NET Framework XAML Services.  
  
 XAML atribut syntaxe formuláře ve povolené <xref:System.Xaml.Schema.XamlTypeTypeConverter> mění typické MSIL / konvence syntaxe CLR, který používá úhel závorky pro různé typy a omezení obecných typů a místo toho nahradí závorkách kontejneru omezení. Příklad, naleznete v části [x: TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Obecné typy a funkce jazyka XAML 2009  
 Pokud používáte XAML 2009 místo mapování modulu CLR základní typy získat běžné primitiv jazyka XAML typy, můžete použít [předdefinované typy jazyka XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako položky informace v `x:TypeArguments`. Je třeba deklarovat následující (předpony mapování není vidět, ale `x` je obor názvů jazyka XAML XAML pro XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Podpora obecné typy v WPF a jiné architektury v3.5  
 Pro použití XAML 2006, pokud je konkrétně cílem WPF [x: Class –](../../../docs/framework/xaml-services/x-class-directive.md) také je třeba zadat u stejného elementu jako `x:TypeArguments`, a tento element musí být kořenový element dokumentu XAML. Kořenový element musí být mapována obecného typu pomocí alespoň jeden typ argumentu. Příkladem je <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Možná řešení v oblasti podpory obecné použití zahrnují definování rozšíření vlastních značek, které může vrátit obecných typů, nebo zadáním zabalení třídy definice, které je odvozen od obecného typu, ale vyrovná obecná omezení v jeho vlastní definici třídy.  
  
 WPF a cílení na [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], můžete použít funkce jazyka XAML 2009 společně s `x:TypeArguments`, ale jenom pro přijít XAML (XAML, který zkompiluje značek není). Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
 Vlastní pracovní postupy v modelu Windows Workflow Foundation pro [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] není podporována Obecná použití XAML.  
  
## <a name="see-also"></a>Viz také  
 [x:TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
