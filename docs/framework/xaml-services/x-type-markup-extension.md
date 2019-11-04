---
title: x:Type – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459914"
---
# <a name="xtype-markup-extension"></a>x:Type – rozšíření značek
Dodává objekt CLR <xref:System.Type>, který je základním typem pro zadaný typ XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`prefix`|Volitelné. Předpona, která mapuje nevýchozí obor názvů XAML. Zadání předpony není často nutné. Viz poznámky.|  
|`typeNameValue`|Požadováno. Název typu, který lze přeložit na aktuální výchozí obor názvů XAML; nebo zadanou mapovanou předponu, pokud je dodána `prefix`.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Type` rozšíření značek má podobnou funkci operátoru `typeof()` v C# nebo operátoru `GetType` v Microsoft Visual Basic.  
  
 Rozšíření `x:Type` značek poskytuje chování převodu z řetězce pro vlastnosti, které přebírají typ <xref:System.Type>. Vstup je typ XAML. Vztah mezi vstupním typem XAML a výstupním CLR <xref:System.Type> je, že výstupní <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupního <xref:System.Xaml.XamlType>po vyhledání potřebných <xref:System.Xaml.XamlType> na základě kontextu schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver> služby, kterou poskytuje kontext.  
  
 V .NET Framework služby XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.TypeExtension> třídou.  
  
 V konkrétních implementacích rozhraní některé vlastnosti, které přijímají <xref:System.Type> jako hodnotu, mohou přijmout název typu přímo (Řetězcová hodnota typu `Name`). Nicméně implementace tohoto chování je složitý scénář. Příklady najdete v části "poznámky k použití WPF", které následují.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `x:Type` identifikátoru je přiřazen jako hodnota <xref:System.Windows.Markup.TypeExtension.TypeName%2A> základní třídy rozšíření <xref:System.Windows.Markup.TypeExtension>. V rámci výchozího kontextu schématu XAML pro .NET Framework služby XAML, která je založena na typech CLR, je hodnota tohoto atributu buď <xref:System.Reflection.MemberInfo.Name%2A> požadovaného typu, nebo obsahuje, který <xref:System.Reflection.MemberInfo.Name%2A> předchází předponu pro mapování oboru názvů jazyka XAML, který není výchozí.  
  
 Rozšíření značek `x:Type` lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.Markup.TypeExtension.TypeName%2A> pro správnou inicializaci rozšíření.  
  
 Rozšíření značek `x:Type` lze také použít jako atribut verbose; Toto použití však není typické: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Výchozí obor názvů jazyka XAML a mapování typů  
 Výchozí obor názvů XAML pro programování WPF obsahuje většinu typů XAML, které potřebujete pro typické scénáře XAML. Proto lze při odkazování na hodnoty typu XAML často vyhýbat předpony. Je možné, že budete muset namapovat předponu, pokud odkazujete na typ z vlastního sestavení nebo pro typy, které existují v sestavení WPF, ale jsou z oboru názvů CLR, který nebyl namapován na výchozí obor názvů jazyka XAML. Další informace o předponách, oborech názvů XAML a mapování oborů názvů CLR naleznete v tématu [obory názvů XAML a mapování oboru názvů pro WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Vlastnosti typu, které podporují TypeName jako řetězec  
 WPF podporuje techniky, které umožňují zadat hodnotu některých vlastností typu <xref:System.Type> bez nutnosti použití rozšíření značek `x:Type`. Místo toho můžete zadat hodnotu jako řetězec, který bude název typu. Příklady jsou <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> a <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Podpora pro toto chování není poskytována pomocí převaděčů typu nebo rozšíření značek. Místo toho se jedná o chování při odložení implementovaného prostřednictvím <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight podporuje podobnou konvenci. Program Silverlight v současné době nepodporuje `{x:Type}` v jeho podpoře jazyka XAML a nepřijímá `{x:Type}` použití mimo několik okolností, které jsou určeny k podpoře migrace XAML v technologii WPF-Silverlight. Proto je chování TypeName-As-String vestavěné pro všechna vyhodnocení nativních vlastností Silverlightu, kde <xref:System.Type> je hodnota.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 poskytuje další podporu pro obecné typy a upravuje chování funkcí `x:TypeArguments` a `x:Type` k poskytnutí této podpory.  
  
- `x:TypeArguments` a přidružený prvek objektu pro instanci generického objektu může být na jiných prvcích než kořen. Další informace naleznete v části "XAML 2009" [direktivy x:TypeArguments –](x-typearguments-directive.md).  
  
- XAML 2009 podporuje syntaxi pro určení omezení obecného typu v označení. To lze použít `x:TypeArguments`, `x:Type`nebo pomocí dvou funkcí v kombinaci.  
  
- Implementace XAML jazyka WPF při zpracování XAML 2009 pro načtení také přidá tuto možnost do chování implicitního převodu typu pro určité vlastnosti rozhraní, které používají typ <xref:System.Type>.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro volný kód XAML (XAML, který není zkompilován jako kód). XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Style>
- [Styly a šablony](../wpf/controls/styling-and-templating.md)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
