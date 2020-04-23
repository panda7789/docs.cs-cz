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
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072044"
---
# <a name="xarray-markup-extension"></a>x:Array – rozšíření značek

Poskytuje obecnou podporu pro pole objektů v XAML prostřednictvím rozšíření značek. To odpovídá typu `x:ArrayExtension` XAML v [MS-XAML].

## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`typeName`|Název typu, který `x:Array` bude obsahovat. `typeName`může být (a často je) předponou pro obor názvů XAML, který obsahuje definice typu XAML.|
|`arrayContents`|Obsah položek, který je přiřazen k `ArrayExtension.Items` vnitřní vlastnosti. Tyto položky jsou obvykle určeny jako jeden nebo `x:Array` více prvků objektu obsažených v otevírací a uzavírací značky. Očekává se, že zde zadané objekty budou přiřaditelné typu XAML určenému v . `typeName`|

## <a name="remarks"></a>Poznámky

`Type`je povinný atribut `x:Array` pro všechny prvky objektu. Hodnota `Type` parametru nemusí používat `x:Type` rozšíření značek; krátký název typu je typ XAML, který lze zadat jako řetězec.

V implementaci služby .NET XAML Services je vztah mezi vstupním typem XAML a výstupním CLR <xref:System.Type> vytvořeného pole ovlivněn kontextem služby pro rozšíření značek. Výstup <xref:System.Type> je <xref:System.Xaml.XamlType.UnderlyingType%2A> vstupní typ XAML, po vyhledání nezbytné <xref:System.Xaml.XamlType> na základě kontextu schématu <xref:System.Windows.Markup.IXamlTypeResolver> XAML a služby, které poskytuje kontext.

Při zpracování jsou obsah pole přiřazen `ArrayExtension.Items` y vnitřní vlastnosti. V <xref:System.Windows.Markup.ArrayExtension> implementaci je to <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>reprezentováno .

V implementaci služby .NET XAML Services je zpracování <xref:System.Windows.Markup.ArrayExtension> pro toto rozšíření značek definováno třídou. <xref:System.Windows.Markup.ArrayExtension>není zapečetěna a může být použita jako základ pro implementaci rozšíření značky pro vlastní typ pole.

`x:Array`je více určen pro obecné rozšiřitelnost jazyka v XAML. Ale `x:Array` může být také užitečné pro určení hodnot XAML určité vlastnosti, které berou XAML podporované kolekce jako jejich obsah strukturované vlastnosti. Můžete například zadat obsah <xref:System.Collections.IEnumerable> vlastnosti s `x:Array` použitím.

`x:Array`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. `x:Array`je částečně výjimkou z tohoto pravidla, protože místo `x:Array` poskytování alternativní zpracování hodnoty atributu poskytuje alternativní zpracování jeho vnitřní obsah textu. Toto chování umožňuje typy, které nemusí být podporovány existující model obsahu, které mají být seskupeny do pole a odkazoval se později v kódu na pozadí přístupem pojmenované pole; můžete volat <xref:System.Array> metody získat jednotlivé položky pole.

Všechna rozšíření značek v XAML používají{,} `)` závorky ( v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí zpracovat hodnotu atributu. Další informace o rozšířeních značek obecně naleznete v [tématu Převaděče typů a Rozšíření značek pro XAML](type-converters-and-markup-extensions.md).

V XAML 2009 `x:Array` je definovánjako jazyk primitivna namísto rozšíření značky. Další informace naleznete [v tématu Předdefinované typy pro běžné jazyková primitiva XAML](types-for-primitives.md).

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Prvky objektu, které `x:Array` nabývají, obvykle nejsou [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky, které existují v oboru názvů XAML a vyžadují mapování předpony na obor názvů XAML, který není výchozí.

Například následující je jednoduché pole dvou řetězců s `sys` předponou `x`(a také ) definovanou na úrovni pole.

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

Pro vlastní typy, které se používají jako prvky pole, musí třída také podporovat požadavky na vytvoření instance v XAML jako objektové prvky. Další informace naleznete v tématu [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).

## <a name="see-also"></a>Viz také

- [Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
