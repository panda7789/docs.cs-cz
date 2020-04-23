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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071358"
---
# <a name="xtype-markup-extension"></a>x:Type – rozšíření značek

Dodává objekt CLR, <xref:System.Type> který je základním typem pro zadaný typ XAML.

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
|`prefix`|Nepovinný parametr. Předpona, která mapuje nevýchozí obor názvů XAML. Zadání předpony často není nutné. Viz Poznámky.|
|`typeNameValue`|Povinná hodnota. Název typu, který lze řešit na aktuální výchozí obor názvů XAML; nebo zadanou mapovanou `prefix` předponu, pokud je zadána.|

## <a name="remarks"></a>Poznámky

Rozšíření `x:Type` značek má podobnou funkci `typeof()` jako operátor v `GetType` jazyce C# nebo operátor v jazyce Microsoft Visual Basic.

Rozšíření `x:Type` značek poskytuje chování převodu od řetězce pro vlastnosti, které berou typ <xref:System.Type>. Vstup je typ XAML. Vztah mezi vstupní maml typu a <xref:System.Type> výstup CLR <xref:System.Type> je, že výstup <xref:System.Xaml.XamlType.UnderlyingType%2A> je vstup <xref:System.Xaml.XamlType>, po vyhledání nezbytné <xref:System.Xaml.XamlType> na <xref:System.Windows.Markup.IXamlTypeResolver> základě kontextu schématu XAML a služby, které poskytuje kontext.

Ve službě .NET XAML Services je zpracování pro <xref:System.Windows.Markup.TypeExtension> toto rozšíření značek definováno třídou.

V implementacich konkrétní architektury některé <xref:System.Type> vlastnosti, které berou jako hodnotu můžete přijmout `Name`název typu přímo (hodnota řetězce typu ). Implementace tohoto chování je však složitý scénář. Příklady naleznete v části "WPF Poznámky k použití", která následuje.

Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `x:Type` po přidělení řetězce <xref:System.Windows.Markup.TypeExtension.TypeName%2A> identifikátoru jako <xref:System.Windows.Markup.TypeExtension> hodnota základní třídy rozšíření. Ve výchozím kontextu schématu XAML pro služby .NET XAML Services, který je založen na <xref:System.Reflection.MemberInfo.Name%2A> typech CLR, <xref:System.Reflection.MemberInfo.Name%2A> je hodnota tohoto atributu buď požadovaného typu, nebo obsahuje předponu pro mapování oboru názvů XAML, které není výchozí.

Rozšíření `x:Type` značek lze použít v syntaxi prvku objektu. V tomto případě je nutné <xref:System.Windows.Markup.TypeExtension.TypeName%2A> zadat hodnotu vlastnosti správně inicializovat rozšíření.

Rozšíření `x:Type` značek lze také použít jako podrobný atribut; toto použití však není typické:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

### <a name="default-xaml-namespace-and-type-mapping"></a>Výchozí obor názvů XAML a mapování typů

Výchozí obor názvů XAML pro programování WPF obsahuje většinu typů XAML, které potřebujete pro typické scénáře XAML; proto se často můžete vyhnout předpony při odkazování na hodnoty typu XAML. Možná budete muset mapovat předponu, pokud odkazujete na typ z vlastního sestavení nebo pro typy, které existují v sestavení WPF, ale pocházejí z oboru názvů CLR, který nebyl mapován na výchozí obor názvů XAML. Další informace o předponách, oborech názvů XAML a mapování oborů názvů CLR naleznete v [tématu XAML Namespaces and Namespace Mapping for WPF XAML](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).

### <a name="type-properties-that-support-typename-as-string"></a>Vlastnosti typu, které podporují typename jako řetězec

WPF podporuje techniky, které umožňují určení hodnoty <xref:System.Type> některých `x:Type` vlastností typu bez nutnosti použití rozšíření značky. Místo toho můžete zadat hodnotu jako řetězec, který pojmenuje typ. Příklady tohoto <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> jsou <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>a . Podpora pro toto chování není poskytována prostřednictvím převaděčů typu nebo rozšíření značek. Místo toho se jedná o <xref:System.Windows.FrameworkElementFactory>chování časově rozlišené implementované prostřednictvím .

Program Silverlight podporuje podobnou konvenci. Ve skutečnosti program Silverlight aktuálně `{x:Type}` nepodporuje jazykovou podporu XAML `{x:Type}` a nepřijímá použití mimo několik okolností, které jsou určeny pro podporu migrace WPF-Silverlight XAML. Proto typename-as-string chování je vestavěné pro všechny silverlight <xref:System.Type> nativní hodnocení vlastností, kde a je hodnota.

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 poskytuje další podporu pro obecné typy a `x:TypeArguments` `x:Type` upravuje chování funkcí a poskytovat tuto podporu.

- `x:TypeArguments`a přidružený prvek objektu pro instanci obecného objektu může být na jiné prvky než kořen. Další informace naleznete v části "XAML 2009" [x:TypeArguments směrnice](xtypearguments-directive.md).

- XAML 2009 podporuje syntaxi pro určení omezení obecného typu ve značkách. To může používat `x:TypeArguments`, `x:Type`, nebo dva prvky v kombinaci.

- WPF XAML implementace při zpracování XAML 2009 pro zatížení také přidá tuto možnost <xref:System.Type>implicitní chování převodu typu pro určité vlastnosti rozhraní, které používají typ .

V WPF můžete použít funkce XAML 2009, ale pouze pro volné XAML (XAML, který není zkompilován značky). XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Style>
- [Styly a šablony](../fundamentals/styles-templates-overview.md)
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
