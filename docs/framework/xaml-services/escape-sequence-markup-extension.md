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
ms.openlocfilehash: a90f6928d68eddd29762e6206769dd7f07704e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564518"
---
# <a name="-escape-sequence--markup-extension"></a>{} Řídicí sekvence / rozšíření značek
Poskytuje řídicí sekvence XAML pro hodnoty atributu. Řídicí sekvence umožňuje následující hodnoty atributu budou interpretovat jako literál.  
  
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
|*literalValue*|Řetězcový literál, který následuje řídicí sekvence. Obvykle obsahuje tento řetězec otevřené nebo zavřít závorek ({nebo}).|  
  
## <a name="remarks"></a>Poznámky  
 Řídicí sekvence ({}) se používá, aby otevřete složená závorka ({}) můžete použít jako literál v jazyce XAML.  
  
 Otevřete závorek ({}) XAML čtečky obvykle používat k označení vstupní bod rozšíření značek; ale nejprve zkontrolujte další znak, který má-li zjistit, zda je pravé složené závorce (}). Pouze pokud jsou obě složené závorky ({}) jsou přiléhající, se považují za řídicí sekvence.  
  
 V případě řídicí sekvence čtečky XAML by měl zpracovat zbytek řetězec jako řetězec. Ale pokud řídicí sekvence je použité na člena, který má převodník typu, řetězec může převod typů při ke interpretuje se zapisovačem XAML.  
  
 Řídicí sekvence není rozšíření značek a není podporována třídou. Je však názvů, který by měly dodržovat čtečky XAML (včetně vlastní čtečky XAML).  
  
 Uvozovky (") nelze použít jako řídicí sekvencí tímto způsobem. Pokud je nutné nastavit uvozovky jako hodnotu vlastnosti noncontent vlastnosti, použijte vlastnost element syntaxi a umístěte znak uvozovek jako řetězec uvnitř elementu vlastnost nebo použijte znakové entity XML. Pro vlastnost obsahu může být znak uvozovek celého obsahu.  
  
 Řídicí sekvence ({}) je vyžadován často, při zadávání typ XML, který musí zahrnovat kvalifikátor oboru názvů v umístění, kde se může objevit rozšíření značek XAML. To zahrnuje počáteční hodnoty atributu XAML a rozšíření značek, okamžitě po symbol rovná se (=). Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnotu atributu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Viz také  
 [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Znakové entity XML a jazyk XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
