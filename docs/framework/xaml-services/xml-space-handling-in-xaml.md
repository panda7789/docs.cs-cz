---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938720"
---
# <a name="xmlspace-handling-in-xaml"></a>Práce s atributem xml:space v jazyce XAML
`xml:space` Atribut je atribut definice XML, který deklaruje chování operací zpracování prázdných znaků v rámci elementu objektu. Toto chování platí pro veškerý obsah (vnitřní text) obsažené v rámci elementu kde `xml:space` je deklarován a také rozsahy pro podřízené prvky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- nebo –  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Poznámky  
 Definice `xml:space` atribut v XAML, včetně jeho dvě možné hodnoty pochází z `xml:space` definované jako "speciální atribut" specifikaci W3C pro XML.  
  
 Výchozí hodnota `xml:space` atribut je hodnota literálu `"default"`. Pro hodnotu `"default"`, nebo pokud `xml:space` není vůbec, uvedené chování významné parsování prázdné místo je výchozí zpracování, jak je definováno v tématu [– zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md).  
  
 Chcete-li zachovat mezer v obsahu elementu objektu, zadejte `xml:space="preserve"` u tohoto elementu objektu.  
  
 V části většiny interpretace `xml:space` efekty atribut a hodnota atributu oborem pro podřízené prvky.  
  
 Úplné informace o – zpracování mezerových znaků v XAML najdete v části [– zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md)
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
