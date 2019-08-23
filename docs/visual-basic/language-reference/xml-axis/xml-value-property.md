---
title: Vlastnost hodnoty XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942980"
---
# <a name="xml-value-property-visual-basic"></a>Vlastnost hodnoty XML (Visual Basic)
Poskytuje přístup k hodnotě prvního prvku kolekce <xref:System.Xml.Linq.XElement> objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Povinný parametr. <xref:System.Xml.Linq.XElement> Kolekce objektů.|  
  
## <a name="return-value"></a>Návratová hodnota  
 , Který obsahuje hodnotu prvního prvku kolekce, nebo `Nothing` Pokud je kolekce prázdná. `String`  
  
## <a name="remarks"></a>Poznámky  
 Vlastnost usnadňuje přístup k hodnotě prvního prvku v <xref:System.Xml.Linq.XElement> kolekci objektů. <xref:System.Xml.Linq.XElement.Value%2A> Tato vlastnost nejprve ověří, zda kolekce obsahuje alespoň jeden objekt. Pokud je kolekce prázdná, vrátí `Nothing`Tato vlastnost. V opačném případě tato vlastnost vrátí hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnosti prvního prvku v kolekci.  
  
> [!NOTE]
> Při přístupu k hodnotě atributu XML pomocí\@identifikátoru se hodnota atributu vrátí `String` jako a <xref:System.Xml.Linq.XAttribute.Value%2A> nemusíte explicitně zadávat vlastnost.  
  
 Chcete-li získat přístup k dalším prvkům v kolekci, můžete použít vlastnost indexer rozšíření XML. Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dědičnost  
 Většina uživatelů nebude muset implementovat <xref:System.Collections.Generic.IEnumerable%601>, a proto může tuto část ignorovat.  
  
 Vlastnost je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`. <xref:System.Xml.Linq.XElement.Value%2A> Vazba této vlastnosti rozšíření se podobá vazbě rozšiřujících metod: Pokud typ implementuje jedno z rozhraní a definuje vlastnost s názvem "value", má tato vlastnost přednost před vlastností Extension. Jinými slovy Tato <xref:System.Xml.Linq.XElement.Value%2A> vlastnost může být přepsána definováním nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:System.Xml.Linq.XElement.Value%2A> vlastnost pro přístup k prvnímu uzlu v <xref:System.Xml.Linq.XElement> kolekci objektů. V příkladu se používá vlastnost podřízené osy k získání kolekce všech podřízených uzlů s názvem `phone` , které jsou `contact` v objektu.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objektů. V příkladu se používá vlastnost osa atributu k zobrazení hodnoty `type` atributu pro všechny `phone` elementy.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Tento kód zobrazí následující text:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [Vlastnost osy podřízeného XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Vlastnost osy atributu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
