---
title: Vlastnost indexeru rozšíření
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352700"
---
# <a name="extension-indexer-property-visual-basic"></a>Vlastnost indexeru rozšíření (Visual Basic)
Poskytuje přístup k jednotlivým prvkům v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Kolekce Queryable. To znamená, že kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.|  
|(|Požadováno. Označuje začátek vlastnosti indexeru.|  
|`index`|Požadováno. Celočíselný výraz, který určuje pozici prvku kolekce na základě nuly.|  
|)|Požadováno. Označuje konec vlastnosti indexeru.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt ze zadaného umístění v kolekci, nebo `Nothing`, pokud je index mimo rozsah.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci. Tato vlastnost indexeru se obvykle používá ve výstupu vlastností osy XML. Vlastnosti podřízenosti a podřízené osy XML vrací kolekce objektů <xref:System.Xml.Linq.XElement> nebo hodnoty atributu.  
  
 Kompilátor Visual Basic převádí vlastnosti indexeru rozšíření na volání metody `ElementAtOrDefault`. Na rozdíl od indexeru pole vrací metoda `ElementAtOrDefault` `Nothing`, pokud je index mimo rozsah. Toto chování je užitečné, pokud nemůžete snadno určit počet prvků v kolekci.  
  
 Tato vlastnost indexeru je stejná jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, že kolekce nemá indexer nebo výchozí vlastnost.  
  
 Pro přístup k hodnotě prvního prvku v kolekci objektů <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> můžete použít vlastnost `Value` XML. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít indexer rozšíření pro přístup k druhému podřízenému uzlu v kolekci objektů <xref:System.Xml.Linq.XElement>. Ke kolekci je přistupovaná pomocí vlastnosti podřízené osy, která získá všechny podřízené prvky s názvem `phone` v objektu `contact`.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Tento kód zobrazí následující text:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
