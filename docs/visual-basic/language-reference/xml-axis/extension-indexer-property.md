---
title: "Vlastnost indexeru rozšíření (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a>Vlastnost indexeru rozšíření (Visual Basic)
Poskytuje přístup k jednotlivé elementy v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object(index)  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Dotazovatelná kolekce. To znamená, kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.|  
|(|Požadováno. Označuje začátek vlastnost indexeru.|  
|`index`|Požadováno. Celé číslo výraz, který určuje pozice s nulovým základem elementu kolekce.|  
|)|Požadováno. Označuje konec vlastnost indexeru.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt v zadaném umístění v kolekci, nebo `Nothing` Pokud index je mimo rozsah.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost indexeru rozšíření slouží pro přístup k jednotlivé elementy v kolekci. Tato vlastnost indexer se obvykle používá na výstup vlastnosti osy XML. Podřízené XML a vlastnosti podřízené osy XML vrátí kolekce <xref:System.Xml.Linq.XElement> objekty nebo hodnota atributu.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metoda. Na rozdíl od indexer pole `ElementAtOrDefault` metoda vrátí `Nothing` Pokud index je mimo rozsah. Toto chování je užitečné, když nelze snadno určit počet elementů v kolekci.  
  
 Tato vlastnost indexeru je jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, že kolekce nemá indexer nebo výchozí vlastnost.  
  
 Pro přístup k hodnotě prvním elementem v kolekci <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, můžete použít soubor XML `Value` vlastnost. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat indexovací modul rozšíření pro přístup k druhý podřízený uzel v kolekci <xref:System.Xml.Linq.XElement> objekty. Kolekce přistupuje pomocí vlastnost osy podřízeného, který získá všech podřízených elementů s názvem `phone` v `contact` objektu.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML – literály](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
