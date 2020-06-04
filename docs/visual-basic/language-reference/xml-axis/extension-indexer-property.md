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
ms.openlocfilehash: c91061d49e22e648b7bf75a812071b352793abcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401339"
---
# <a name="extension-indexer-property-visual-basic"></a>Vlastnost indexeru rozšíření (Visual Basic)
Poskytuje přístup k jednotlivým prvkům v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`object`|Povinná hodnota. Kolekce Queryable. To znamená, že kolekce implementující <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> .|  
|(|Povinná hodnota. Označuje začátek vlastnosti indexeru.|  
|`index`|Povinná hodnota. Celočíselný výraz, který určuje pozici prvku kolekce na základě nuly.|  
|)|Povinná hodnota. Označuje konec vlastnosti indexeru.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt ze zadaného umístění v kolekci, nebo `Nothing` Pokud je index mimo rozsah.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci. Tato vlastnost indexeru se obvykle používá ve výstupu vlastností osy XML. Vlastnosti podřízenosti a podřízené osy XML vrací kolekce <xref:System.Xml.Linq.XElement> objektů nebo hodnoty atributu.  
  
 Kompilátor Visual Basic převádí vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metody. Na rozdíl od indexeru pole, `ElementAtOrDefault` Metoda vrátí, `Nothing` Pokud je index mimo rozsah. Toto chování je užitečné, pokud nemůžete snadno určit počet prvků v kolekci.  
  
 Tato vlastnost indexeru je stejná jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> : používá se pouze v případě, že kolekce nemá indexer nebo výchozí vlastnost.  
  
 Chcete-li získat přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> objektů nebo <xref:System.Xml.Linq.XAttribute> , můžete použít `Value` vlastnost XML. Další informace najdete v tématu [vlastnost hodnoty XML](xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít indexer rozšíření pro přístup k druhému podřízenému uzlu v kolekci <xref:System.Xml.Linq.XElement> objektů. Ke kolekci je přistupovaná pomocí vlastnosti podřízené osy, která vrací všechny podřízené prvky s názvem `phone` v `contact` objektu.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Tento kód zobrazí následující text:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](index.md)
- [Literály XML](../xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Vlastnost hodnoty XML](xml-value-property.md)
