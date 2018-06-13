---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: af971ad9ea74e123b939ff8d8488e4e45c5d4aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563464"
---
# <a name="xmlspace-handling-in-xaml"></a>Práce s atributem xml:space v jazyce XAML
`xml:space` Se atribut definované XML, který deklaruje chování významný mezerový znak zpracování v rámci elementu objektu. Toto chování je relevantní pro veškerý obsah (vnitřní text) obsažených v elementu kde `xml:space` je deklarován a také rozsahy pro podřízené elementy.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- nebo –  
  
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
 [Zpracování prázdných znaků v jazyku XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
