---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458802"
---
# <a name="xmlspace-handling-in-xaml"></a>Práce s atributem xml:space v jazyce XAML
Atribut `xml:space` je atribut definovaný v jazyce XML, který deklaruje významné chování zpracování bílého místa v rámci elementu objektu. Toto chování je relevantní pro veškerý obsah (vnitřní text) obsažený v elementu, kde je `xml:space` deklarována, a také obory pro podřízené prvky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- nebo-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Poznámky  
 Definice atributu `xml:space` v jazyce XAML, včetně jeho dvou možných hodnot, je odvozena od `xml:space` definována jako "speciální atribut" specifikacemi W3C Specification for XML.  
  
 Výchozí hodnota atributu `xml:space` je hodnota literálu `"default"`. V případě hodnoty `"default"`, nebo pokud `xml:space` není uvedena vůbec, je chování významné analýzy bílého místa výchozím zpracováním, jak je definováno v tématu [zpracování prázdných míst v jazyce XAML](whitespace-processing-in-xaml.md).  
  
 Chcete-li zachovat prázdné znaky v obsahu elementu objektu, zadejte `xml:space="preserve"` na tento prvek objektu.  
  
 V rámci většiny výkladů jsou účinky atributů `xml:space` a hodnota atributu vymezeny na podřízené prvky.  
  
 Úplné informace o zpracování bílého místa v jazyce XAML naleznete v tématu [prázdné místo zpracování v jazyce XAML](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpracování prázdných míst v jazyce XAML](whitespace-processing-in-xaml.md)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
