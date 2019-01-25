---
title: '{} Řídicí sekvence – rozšíření značek'
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
ms.openlocfilehash: 8a065573abb5a230d2a51f1767bd8d2e829bccd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521267"
---
# <a name="-escape-sequence--markup-extension"></a>{} Řídicí sekvence / rozšíření značek
Poskytuje řídicí sekvence XAML pro hodnoty atributů. Řídicí sekvence povoluje následující hodnoty v atributu je interpretován jako literální.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Použití elementu vlastnosti XAML  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*literalValue*|Řetězcový literál, který následuje řídicí sekvence. Obvykle tento řetězec obsahuje otevřít nebo zavřít závorka ({nebo}).|  
  
## <a name="remarks"></a>Poznámky  
 Řídicí sekvence ({}) se používá tak, aby levou složenou závorku ({}) je možné jako literální znak v XAML.  
  
 Čtenáři XAML obvykle používají levou složenou závorku ({}) k označení vstupní bod rozšíření značek, ale nejprve zkontrolujte další znak k určení, zda je pravá složená závorka (}). Pouze když dvě složené závorky ({}) jsou sousedící, se považují za řídicí sekvence.  
  
 Pokud je řídicí sekvence, čtečky XAML by měl zpracovat zbývající část řetězce jako řetězec. Však pokud řídicí sekvence je u člena, který má konvertor typu, řetězec může projít převod typu při je interpretován tvůrci XAML.  
  
 Řídicí sekvence není rozšíření značek a nepochází ze třídy. Je však konvence, který by měly dodržovat čtenáři XAML (včetně vlastních čtenáři XAML).  
  
 Znak uvozovek (") nelze použít jako řídicí sekvence tímto způsobem. Pokud je potřeba nastavit jako hodnotu vlastnosti noncontent vlastnosti uvozovku, používat syntax prvku vlastnosti a umístěte znak uvozovek jako řetězec uvnitř elementu vlastnosti nebo použít znakové entity XML. Pro vlastnost obsahu může být znak uvozovek celého obsahu.  
  
 Řídicí sekvence ({}) je vyžadován často, při určování typu XML, který musí obsahovat obor názvů kvalifikátoru v umístění, kde se může zobrazit rozšíření značek XAML. To zahrnuje počáteční hodnotu atributu XAML a rozšíření značek, ihned po rovnítko (=). Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnotu atributu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Viz také:
- [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)
- [Znakové entity XML a jazyk XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
