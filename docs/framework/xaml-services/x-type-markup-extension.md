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
ms.openlocfilehash: e4d56c5b5deda0bd1df8827020e0b76cc6276c1c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844855"
---
# <a name="xtype-markup-extension"></a>x:Type – rozšíření značek
CLR poskytuje <xref:System.Type> objekt, který je základní typ pro zadaný typ XAML.  
  
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
|`prefix`|Volitelné. Předpona, která mapuje jiné než výchozí obor názvů XAML. Zadání předpony není často nutné. Viz poznámky.|  
|`typeNameValue`|Požadováno. Název typu, který je možné přeložit na aktuální výchozí XAML obor názvů; nebo zadaného mapování předpony Pokud `prefix` pochází.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Type` Podobné funkce, která se má rozšíření značek `typeof()` operátor v jazyce C# nebo `GetType` operátor v aplikaci Microsoft Visual Basicu.  
  
 `x:Type` – Rozšíření značek poskytuje chování převod z řetězce pro vlastnosti, které přijmout typ <xref:System.Type>. Vstup je typu XAML. Vztah mezi XAML typ vstupu a výstupu CLR <xref:System.Type> , který se nachází výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupu <xref:System.Xaml.XamlType>, po vyhledání nezbytné <xref:System.Xaml.XamlType> na základě kontext schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver>service poskytuje kontext.  
  
 V rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.TypeExtension> třídy.  
  
 Implementace konkrétní verzi rozhraní framework, některé vlastnosti, která trvat <xref:System.Type> jako hodnotu můžete přijmout přímo název typu (řetězcové hodnoty typ `Name`). Implementace toto chování je však komplexní scénáře. Příklady najdete v části "Poznámky k použití WPF", který následuje.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `x:Type` řetězec identifikátoru je přiřazen jako <xref:System.Windows.Markup.TypeExtension.TypeName%2A> hodnoty základního <xref:System.Windows.Markup.TypeExtension> rozšíření třídy. V části výchozí kontext schématu XAML pro rozhraní .NET Framework XAML Services, která je založena na typy CLR, hodnota tohoto atributu je buď <xref:System.Reflection.MemberInfo.Name%2A> požadovaného typu, nebo, který obsahuje <xref:System.Reflection.MemberInfo.Name%2A> předchází předponu pro obor názvů XAML jiné než výchozí mapování.  
  
 `x:Type` – Rozšíření značek lze použít v syntaxi elementu objektu. V takovém případě zadáte hodnotu <xref:System.Windows.Markup.TypeExtension.TypeName%2A> vlastnost je potřeba správně inicializovat rozšíření.  
  
 `x:Type` – Rozšíření značek můžete také použít jako atribut podrobné; však není typické použití: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Výchozí Namespace XAML a mapování typu  
 Výchozí obor názvů XAML pro programování WPF obsahuje většinu typů XAML, které potřebujete pro typické scénáře XAML; Při odkazování na hodnoty typu XAML proto můžete vyhnout často předpony. Můžete potřebovat k mapování předpony, pokud odkazujete na typ z vlastních sestavení nebo pro typy, které existují v WPF sestavení, ale jsou z oboru názvů CLR, který nebyl namapován na výchozí obor názvů XAML. Další informace o předpon oborů názvů XAML a mapování oborů názvů CLR naleznete v tématu [obory názvů XAML a mapování Namespace pro WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Zadejte vlastnosti této podpory Typename jako String  
 WPF podporuje techniky, které umožňují určující hodnotu některé vlastnosti typu <xref:System.Type> bez nutnosti `x:Type` použití rozšíření značky. Místo toho můžete zadat hodnotu jako řetězec, který označuje typ. Příklady jsou <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> a <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Podpora pro toto chování není k dispozici prostřednictvím převaděče typů a rozšíření značek. Místo toho jde odložení chování implementované pomocí <xref:System.Windows.FrameworkElementFactory>.  
  
 Technologie Silverlight podporuje podobné konvence. Ve skutečnosti Silverlight aktuálně nepodporuje `{x:Type}` v jeho podporu jazyka XAML a nepřijímá `{x:Type}` použití mimo několik okolností, které jsou určené pro podporu migrace WPF Silverlight XAML. Proto je integrovaná do všech vyhodnocení nativních vlastností Silverlight chování typename jako řetězec kde <xref:System.Type> je hodnota.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 poskytuje další podporu pro obecné typy a upravuje chování funkce `x:TypeArguments` a `x:Type` pro tuto funkci podporují.  
  
-   `x:TypeArguments` a element přidruženého objektu pro vytváření instancí obecné objektu může být u jiných elementů než kořenovém adresáři. Další informace najdete v části "XAML 2009" v [x: TypeArguments – direktiva](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 podporuje syntaxi pro zadání omezení obecného typu v kódu. To může využívat `x:TypeArguments`, `x:Type`, nebo dvě funkce v kombinaci.  
  
-   Implementaci WPF XAML při zpracování XAML 2009, pro zatížení také přidá tuto funkci pro implicitní typ chování převod vlastnosti na určité rozhraní, které používají typ <xref:System.Type>.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro volný XAML (XAML, který není kompilována značka). Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Style>  
 [Styly a šablony](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
