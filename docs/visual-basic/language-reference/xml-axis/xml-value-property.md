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
ms.openlocfilehash: 2b0719320db5843d5d010bfbd70e551646e3ded9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086336"
---
# <a name="xml-value-property-visual-basic"></a>Vlastnost hodnoty XML (Visual Basic)
Poskytuje přístup k hodnotě prvního prvku kolekce <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Kolekce <xref:System.Xml.Linq.XElement> objekty.|  
  
## <a name="return-value"></a>Návratová hodnota  
 A `String` , který obsahuje hodnotu elementu první kolekce, nebo `Nothing` Pokud kolekce je prázdná.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastnost usnadňuje přístup k hodnotě prvního prvku v kolekci <xref:System.Xml.Linq.XElement> objekty. Tato vlastnost nejprve zkontroluje, zda kolekce obsahuje minimálně jeden objekt. Pokud kolekce je prázdná, vrátí tato vlastnost `Nothing`. V opačném případě vrátí tato vlastnost hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnost první prvek v kolekci.  
  
> [!NOTE]
>  Když zobrazujete hodnota atributu XML pomocí "\@" identifikátor, jako je vrácena hodnota atributu `String` a není potřeba explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.  
  
 Pro přístup k další prvky v kolekci, můžete použít vlastnost indexeru rozšíření XML. Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dědičnost  
 Většina uživatelů nebudete muset implementovat <xref:System.Collections.Generic.IEnumerable%601>a proto můžete ignorovat tento oddíl.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastností je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`. Vazba této vlastnosti rozšíření se podobá vazba metod rozšíření: Pokud typ jednoho z rozhraní implementuje a definuje vlastnost s názvem "Value", tato vlastnost má vyšší prioritu než vlastnost extension. Jinými slovy to <xref:System.Xml.Linq.XElement.Value%2A> vlastnost může být přepsána definování nové vlastnosti do třídy, která implementuje `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití <xref:System.Xml.Linq.XElement.Value%2A> vlastnosti pro přístup k prvním uzlem v kolekci <xref:System.Xml.Linq.XElement> objekty. Vlastnost osy podřízeného v příkladu se používá k získání kolekce všech podřízených uzlech s názvem `phone` , které jsou `contact` objektu.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak má být získána hodnota atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objekty. V příkladu používá vlastnost osy atributu k zobrazení hodnoty `type` atribut pro všechny `phone` elementy.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [Vlastnost osy podřízeného XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Vlastnost osy atributu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
