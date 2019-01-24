---
title: Vlastnost indexeru rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 25a868afded83f28f5f56a9f19e050bbd32b24c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490827"
---
# <a name="extension-indexer-property-visual-basic"></a>Vlastnost indexeru rozšíření (Visual Basic)
Poskytuje přístup k jednotlivým prvkům v kolekci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object(index)  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Povinný parametr. Dotazovatelná kolekce. To znamená, že kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>.|  
|(|Povinný parametr. Označuje začátek vlastnost indexeru.|  
|`index`|Povinný parametr. Celočíselný výraz, který určuje pozice s nulovým základem elementu kolekce.|  
|)|Povinný parametr. Označuje konec vlastnost indexeru.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt v zadaném umístění v kolekci, nebo `Nothing` Pokud index je mimo rozsah.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost indexeru rozšíření můžete použít pro přístup k jednotlivým prvkům v kolekci. Tato vlastnost indexeru se obvykle používá ve výstupu vlastnosti osy XML. Podřízené XML a vlastnosti XML podřízené osy vrací kolekce <xref:System.Xml.Linq.XElement> objekty nebo hodnotu atributu.  
  
 Kompilátor jazyka Visual Basic převede vlastnosti indexeru rozšíření na volání `ElementAtOrDefault` metody. Na rozdíl od pole indexer `ElementAtOrDefault` vrátí metoda `Nothing` Pokud index je mimo rozsah. Toto chování je užitečné, když nelze snadno určit počet prvků v kolekci.  
  
 Tato vlastnost indexer je jako vlastnost rozšíření pro kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601>: používá se pouze v případě, kolekce nemá výchozí vlastnost nebo indexer.  
  
 Pro přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XAttribute> objekty, můžete použít XML `Value` vlastnost. Další informace najdete v tématu [vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat indexovací modul rozšíření pro přístup k druhý podřízený uzel v kolekci <xref:System.Xml.Linq.XElement> objekty. Kolekce lze přistupovat pomocí vlastnost podřízené osy, který získá všechny podřízené prvky s názvem `phone` v `contact` objektu.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XElement>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vlastnost hodnoty XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
