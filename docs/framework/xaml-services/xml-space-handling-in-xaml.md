---
title: "Práce s atributem xml:space v jazyce XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a>Práce s atributem xml:space v jazyce XAML
`xml:space` Se atribut definované XML, který deklaruje chování významný mezerový znak zpracování v rámci elementu objektu. Toto chování je relevantní pro veškerý obsah (vnitřní text) obsažených v elementu kde `xml:space` je deklarován a také rozsahy pro podřízené elementy.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-nebo –  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Poznámky  
 Definice pro `xml:space` atribut v jazyce XAML, včetně jeho dvě možné hodnoty je odvozený od `xml:space` podle definice jako "speciální atribut" W3C specifikace XML.  
  
 Výchozí hodnota `xml:space` atribut je literálovou hodnotou `"default"`. Pro hodnotu `"default"`, nebo pokud `xml:space` není uvedené ve všech chování analýza významný mezerový znak je výchozí zpracování, jak jsou definovány v sekci [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Pokud chcete zachovat prázdných znaků v obsahu elementu objektu, zadejte `xml:space="preserve"` u tohoto objektu elementu.  
  
 V části většiny interpretace `xml:space` atribut dopady a hodnota atributu je v oboru podřízené elementy.  
  
 Úplné informace o zpracování prázdných znaků v jazyce XAML, najdete v části [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
