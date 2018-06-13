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
ms.openlocfilehash: d3731a5249788b509c48623d8fa2284541f996ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563117"
---
# <a name="xtype-markup-extension"></a>x:Type – rozšíření značek
Poskytuje modulu CLR <xref:System.Type> objekt, který je základní typ pro zadaný typ jazyka XAML.  
  
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
|`prefix`|Volitelné. Předpona, která se mapuje jiné než výchozí oboru názvů jazyka XAML. Zadání předpony není často nutné. V části poznámky.|  
|`typeNameValue`|Požadováno. Název typu přeložit na aktuální výchozí XAML obor názvů; nebo zadané mapování předpony Pokud `prefix` pochází.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Type` Podobné funkce, která se má – rozšíření značek `typeof()` operátor v jazyce C# nebo `GetType` operátor v aplikaci Microsoft Visual Basic.  
  
 `x:Type` – Rozšíření značek poskytuje chování převod z řetězce pro vlastnosti, které typu <xref:System.Type>. Vstup je typ jazyka XAML. Vztah mezi vstupní typ jazyka XAML a výstup CLR <xref:System.Type> je, že výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupu <xref:System.Xaml.XamlType>, po vyhledávání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver>service poskytuje kontext.  
  
 V rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.TypeExtension> třídy.  
  
 V implementacích konkrétní framework některé vlastnosti, které přebírají <xref:System.Type> jako hodnotu může přijmout název typu přímo (s řetězcovou hodnotou obsahující typ `Name`). Implementace toto chování je však komplexní scénář. Příklady najdete v části "Poznámky pro použití WPF", který následuje.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `x:Type` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.TypeExtension.TypeName%2A> hodnotu základní <xref:System.Windows.Markup.TypeExtension> rozšíření třídy. V části výchozí kontext schématu XAML pro rozhraní .NET Framework XAML Services, která je založena na typy CLR, hodnota tohoto atributu je buď <xref:System.Reflection.MemberInfo.Name%2A> požadovaného typu, nebo který obsahuje <xref:System.Reflection.MemberInfo.Name%2A> sebou předponu pro obor názvů jiný než výchozí XAML mapování.  
  
 `x:Type` – Rozšíření značek mohou být používány syntaxe element objektu. V takovém případě určující hodnotu <xref:System.Windows.Markup.TypeExtension.TypeName%2A> vlastnost je potřeba správně inicializovat rozšíření.  
  
 `x:Type` – Rozšíření značek lze také jako atribut podrobné; však není Typická tuto použijte: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Výchozí Namespace XAML a mapování typu  
 Výchozí obor názvů jazyka XAML pro programování WPF obsahuje většinu typů XAML, které jsou potřeba pro typické scénáře XAML; Při odkazování na hodnoty typu XAML proto můžete vyhnout často předpony. Možná budete muset namapovat předpony, pokud odkazujete typu z vlastního sestavení nebo pro typy, které existují v sestavení WPF, ale jsou od CLR oboru názvů, který nebyl namapovaný na výchozí obor názvů jazyka XAML. Další informace o předpony, obory názvů jazyka XAML a obory názvů mapování CLR najdete v tématu [obory názvů jazyka XAML a mapování Namespace pro jazyk XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Zadejte vlastnosti tento podporu Typename – jako – řetězec  
 WPF podporuje techniky, které umožňují určující hodnotu některých vlastností typu <xref:System.Type> bez nutnosti `x:Type` využití rozšíření značek. Místo toho můžete zadat hodnotu jako řetězec, který názvy typu. Příklady jsou <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> a <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Podpora pro toto chování není k dispozici prostřednictvím převaděče typů nebo rozšíření značek. Místo toho jedná o odložení chování implementuje pomocí <xref:System.Windows.FrameworkElementFactory>.  
  
 Program Silverlight podporuje podobné konvence. Ve skutečnosti Silverlight aktuálně nepodporuje `{x:Type}` v jeho podporu jazyka XAML a nepřijímá `{x:Type}` použití mimo za určitých okolností, které jsou určeny pro podporu migrace WPF Silverlight XAML. Proto je integrovaný do všech testování nativní vlastnost Silverlight chování typename jako řetězec kde <xref:System.Type> je hodnota.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 poskytuje další podporu pro obecné typy a mění chování funkce `x:TypeArguments` a `x:Type` pro tuto funkci podporují.  
  
-   `x:TypeArguments` a element přidruženého objektu pro vytváření instancí obecný objekt může být u jiných elementů než kořenu. Další informace najdete v části "XAML 2009" [x: TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 podporuje syntaxi pro určení omezení obecného typu v kódu. To mohou být využívána `x:TypeArguments`, pomocí `x:Type`, nebo tyto dvě funkce v kombinaci.  
  
-   Implementace WPF XAML při zpracování jazyka XAML 2009, pro zatížení tato funkce také přidá do chování typu implicitní převod některé vlastnosti framework, které používají typ <xref:System.Type>.  
  
 V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009 ale jenom pro přijít XAML (XAML, který zkompiluje značek není). Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Style>  
 [Styly a šablony](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
