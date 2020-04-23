---
title: '{}Escape Sequence – rozšíření značek'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071743"
---
# <a name="-escape-sequence--markup-extension"></a>{}Escape sekvence / značkovací rozšíření

Poskytuje řídicí sekvenci XAML pro hodnoty atributů. Sekvence escape umožňuje následné hodnoty v atributu, které mají být interpretovány jako literál.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object property="{} literalValue" .../>
```

## <a name="xaml-property-element-usage"></a>Použití elementu vlastnosti XAML

```xaml
<object>
  <object.property>
    {} literalValue
  </object.property>
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|*literalValue*|Literál řetězec, který následuje sekvence escape. Obvykle tento řetězec obsahuje otevřenou nebo zavřít složená závorka ({ nebo }).|

## <a name="remarks"></a>Poznámky

Sekvence escape{}( ) se používá tak, aby otevřená závorka ({) může být použita jako literál znak v XAML.

Čtečky XAML obvykle používají otevřenou složenou závorku ({) k označení vstupního bodu rozšíření značek; nejprve však zkontrolují další znak a zkontrolují, zda se jedná o uzavírací složenou závorku (}). Pouze v případě,{}že dvě závorky ( ) jsou přilehlé, jsou považovány za únikovou sekvenci.

Pokud dojde k escape sekvence, čtečka XAML by měl zpracovat zbytek řetězce jako řetězec. Pokud je však sekvence escape použita na člena, který má převaděč typu, řetězec může projít převodem typu, pokud je interpretován zapisovatelem XAML.

Sekvence escape není rozšíření značky a není zálohována třídou. Je však konvence, která xaml čtenáři (včetně vlastních čteček XAML) by měl respektovat.

Uvozovky (") nelze tímto způsobem použít jako řídicí sekvenci. Pokud potřebujete nastavit uvozovky jako hodnotu vlastnosti pro vlastnost neobsahu, použijte syntaxi prvku vlastnosti a umístěte uvozovku jako řetězec uvnitř elementu vlastnosti nebo použijte entitu znaků XML. Pro vlastnost obsahu může být uvozovka celý obsah.

Sekvence escape{}( ) je často vyžadována při zadávání typu XML, který musí obsahovat kvalifikátor oboru názvů v umístění, kde se může zobrazit rozšíření značek XAML. Toto umístění zahrnuje začátek hodnoty atributu XAML a v rozšíření značky bezprostředně za rovnítkem (=). Následující příklad ukazuje sekvence escape pro obor názvů XML, který se zobrazí na začátku hodnoty atributu XAML.

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>Viz také

- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions.md)
- [Znakové entity XML a jazyk XAML](xml-character-entities.md)
