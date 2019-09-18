---
title: '{}Řídicí sekvence – rozšíření značek'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053865"
---
# <a name="-escape-sequence--markup-extension"></a>{} – řídicí sekvence / rozšíření značek
Poskytuje řídicí sekvenci jazyka XAML pro hodnoty atributu. Řídicí sekvence umožňuje interpretovat následné hodnoty v atributu jako literál.  
  
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
|*literalValue*|Literální řetězec, který následuje za řídicí sekvencí. Tento řetězec obvykle obsahuje levou nebo uzavírací složenou závorku ({nebo}).|  
  
## <a name="remarks"></a>Poznámky  
 Řídicí sekvence ({}) se používá, aby bylo možné použít levou složenou závorku ({) jako literální znak v jazyce XAML.  
  
 Čtečky XAML obvykle používají levou složenou závorku ({) k označení vstupního bodu rozšíření značek, ale nejprve si vyžádají další znak a určí, zda se jedná o pravou složenou závorku (}). Pouze v případě, že dvě složené{}závorky () jsou sousední, jsou považovány za řídicí sekvenci.  
  
 Pokud řídicí sekvence je zjištěna, čtečka XAML by měla zpracovat zbytek řetězce jako řetězec. Pokud je však řídicí sekvence použita pro člena, který má konvertor typu, může řetězec přecházet při převodu typu, když je interpretován zapisovačem XAML.  
  
 Řídicí sekvence není rozšířením značek a není zálohována třídou. Nicméně se jedná o konvenci, kterou by měli respektovat čtenáři XAML (včetně vlastních čtenářů XAML).  
  
 Uvozovky (") nelze použít jako řídicí sekvenci tímto způsobem. Pokud potřebujete nastavit uvozovky jako hodnotu vlastnosti pro vlastnost neobsahující vlastnosti, použijte syntaxi elementu vlastností a umístěte uvozovky jako řetězec uvnitř elementu vlastnosti nebo použijte entitu znaků XML. V případě vlastnosti obsahu může být uvozovka celým obsahem.  
  
 Řídicí sekvence ({}) se často vyžaduje při určení typu XML, který musí obsahovat kvalifikátor oboru názvů v umístění, kde se může zobrazit rozšíření značek XAML. To zahrnuje začátek hodnoty atributu XAML a v rozšíření značek hned po znaménku rovná se (=). Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnoty atributu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Viz také:

- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Znakové entity XML a jazyk XAML](xml-character-entities-and-xaml.md)
