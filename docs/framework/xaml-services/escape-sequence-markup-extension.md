---
title: "Řídicí sekvence {} – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>{} – řídicí sekvence / rozšíření značek
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
  
 Otevřete závorek ({}) XAML čtečky obvykle používat k označení vstupní bod rozšíření značek; ale nejprve zkontrolujte další znak, který má-li zjistit, zda je pravé složené závorce (}). Jenom v případě, že sousedí na dva složené závorky ({}), se považují za řídicí sekvence.  
  
 V případě řídicí sekvence čtečky XAML by měl zpracovat zbytek řetězec jako řetězec. Ale pokud řídicí sekvence je použité na člena, který má převodník typu, řetězec může převod typů při ke interpretuje se zapisovačem XAML.  
  
 Řídicí sekvence není rozšíření značek a není podporována třídou. Je však názvů, který by měly dodržovat čtečky XAML (včetně vlastní čtečky XAML).  
  
 Uvozovky (") nelze použít jako řídicí sekvencí tímto způsobem. Pokud je nutné nastavit uvozovky jako hodnotu vlastnosti noncontent vlastnosti, použijte vlastnost element syntaxi a umístěte znak uvozovek jako řetězec uvnitř elementu vlastnost nebo použijte znakové entity XML. Pro vlastnost obsahu může být znak uvozovek celého obsahu.  
  
 Řídicí sekvence ({}) je vyžadován často, při zadávání typ XML, který musí zahrnovat kvalifikátor oboru názvů v umístění, kde se může objevit rozšíření značek XAML. To zahrnuje počáteční hodnoty atributu XAML a rozšíření značek, okamžitě po symbol rovná se (=). Následující příklad ukazuje řídicí sekvence pro obor názvů XML, který se zobrazí na začátku hodnotu atributu XAML.  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>Viz také  
 [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Znakové entity XML a jazyk XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
