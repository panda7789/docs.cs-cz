---
title: x:Array – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 7c728b63c16d8f24c4ad68d07e6d174f510204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xarray-markup-extension"></a>x:Array – rozšíření značek
Poskytuje obecné podporu pro pole objektů v jazyce XAML prostřednictvím rozšíření značek. To odpovídá `x:ArrayExtension` typ jazyka XAML v [MS-XAML].  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`typeName`|Název typu, vaše `x:Array` bude obsahovat. `typeName` může být (a často je) předponu pro jazyk XAML zadejte obor názvů, který obsahuje XAML definice.|  
|`arrayContents`|Obsah položky, který je přiřazen k vnitřní `ArrayExtension.Items` vlastnost. Obvykle jsou tyto položky zadané jako jeden nebo více objektů elementů obsažených v rámci `x:Array` otvírání a zavírání značky. Zadat objekty v tomto poli se měl přiřaditelné k typu XAML zadaný v `typeName`.|  
  
## <a name="remarks"></a>Poznámky  
 `Type` je povinný atribut pro všechny `x:Array` objektu elementy. A `Type` hodnota parametru není nutné používat `x:Type` – rozšíření značek; krátké název typu je typ jazyka XAML, které lze zadat jako řetězec.  
  
 V rozhraní .NET Framework XAML Services implementace, o vztah mezi vstupní typ jazyka XAML a výstup CLR <xref:System.Type> vytvořený pole je ovlivněno kontext služby pro rozšíření značek. Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typu XAML, po vyhledávání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu XAML a <xref:System.Windows.Markup.IXamlTypeResolver> service poskytuje kontext.  
  
 Při zpracování, že je obsah pole jsou přiřazeny `ArrayExtension.Items` vnitřní vlastnost. V <xref:System.Windows.Markup.ArrayExtension> implementace, to je reprezentována <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.  
  
 Implementace rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.ArrayExtension> třídy. <xref:System.Windows.Markup.ArrayExtension> není zapečetěná a může jako základ pro implementaci rozšíření značek pro typ vlastní pole.  
  
 `x:Array` je že více určený pro obecné rozšiřitelnosti jazyka v jazyce XAML. Ale `x:Array` může být také užitečná pro zadání hodnoty XAML určité vlastnosti, které provést podporované XAML kolekce jako strukturovaný vlastnost obsah. Například můžete zadat obsah <xref:System.Collections.IEnumerable> vlastnost s `x:Array` využití.  
  
 `x:Array` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. `x:Array` je částečně výjimkou tohoto pravidla, protože místo zpracování hodnota atributu alternativní, `x:Array` poskytuje alternativní zpracování část jeho obsahu vnitřní text. Toto chování umožňuje typy, které nemusí být podporován pomocí existujícího modelu obsahu seskupeny do pole a odkazuje později v kódu přístup k poli s názvem; můžete volat <xref:System.Array> metody k načtení pole jednotlivých položek.  
  
 Všechna rozšíření značek v jazyce XAML použít složené závorky ({,} `)` v jejich syntaxi atribut, který je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat hodnotu atributu. Další informace o rozšíření značek v obecné najdete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 V jazyce XAML 2009 `x:Array` je definován jako jazyk primitivní místo rozšíření značek. Další informace najdete v tématu [předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Obvykle objekt prvky, které naplnit `x:Array` nejsou elementy, které existují v [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] oboru názvů jazyka XAML a vyžadovat předponu mapování do oboru názvů jazyka XAML, jiné než výchozí.  
  
 Například následující je jednoduché pole dva řetězce, pomocí `sys` předpony (a také `x`) definované na úrovni pole.  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 Pro vlastní typy, které se používají jako elementy pole musí podporovat třídu i požadavky na vytváření instancí v jazyce XAML jako elementy objektu. Další informace najdete v tématu [XAML a vlastní třídy pro grafický subsystém WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
