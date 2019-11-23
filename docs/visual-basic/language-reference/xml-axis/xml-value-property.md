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
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592008"
---
# <a name="xml-value-property-visual-basic"></a>Vlastnost hodnoty XML (Visual Basic)

Poskytuje přístup k hodnotě prvního prvku kolekce objektů <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Syntaxe

```vb
object.Value
```

## <a name="parts"></a>Součásti

|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Kolekce objektů <xref:System.Xml.Linq.XElement>.|  

## <a name="return-value"></a>Návratová hodnota

 `String`, který obsahuje hodnotu prvního prvku kolekce, nebo `Nothing`, pokud je kolekce prázdná.

## <a name="remarks"></a>Poznámky

 Vlastnost <xref:System.Xml.Linq.XElement.Value%2A> usnadňuje přístup k hodnotě prvního prvku v kolekci objektů <xref:System.Xml.Linq.XElement>. Tato vlastnost nejprve ověří, zda kolekce obsahuje alespoň jeden objekt. Pokud je kolekce prázdná, vrátí tato vlastnost `Nothing`. V opačném případě tato vlastnost vrátí hodnotu vlastnosti <xref:System.Xml.Linq.XElement.Value%2A> prvního prvku v kolekci.

> [!NOTE]
> Při přístupu k hodnotě atributu XML pomocí identifikátoru '\@' se hodnota atributu vrátí jako `String` a nemusíte explicitně určovat vlastnost <xref:System.Xml.Linq.XAttribute.Value%2A>.

 Chcete-li získat přístup k dalším prvkům v kolekci, můžete použít vlastnost indexer rozšíření XML. Další informace najdete v tématu [vlastnost indexeru rozšíření](extension-indexer-property.md).

## <a name="inheritance"></a>Dědičnost

 Většina uživatelů nebude muset implementovat <xref:System.Collections.Generic.IEnumerable%601>, a proto může tuto část ignorovat.

 Vlastnost <xref:System.Xml.Linq.XElement.Value%2A> je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`. Vazba této vlastnosti rozšíření se podobá vazbě rozšiřujících metod: Pokud typ implementuje jedno z rozhraní a definuje vlastnost s názvem "value", má tato vlastnost přednost před vlastností Extension. Jinými slovy Tato vlastnost <xref:System.Xml.Linq.XElement.Value%2A> možné přepsat definováním nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak použít vlastnost <xref:System.Xml.Linq.XElement.Value%2A> pro přístup k prvnímu uzlu v kolekci objektů <xref:System.Xml.Linq.XElement>. V příkladu se používá vlastnost podřízené osy k získání kolekce všech podřízených uzlů s názvem `phone`, které jsou v objektu `contact`.

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 Tento kód zobrazí následující text:

 `Phone number: 206-555-0144`

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce objektů <xref:System.Xml.Linq.XAttribute>. V příkladu se používá vlastnost osa atributu k zobrazení hodnoty atributu `type` pro všechny `phone` prvky.

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 Tento kód zobrazí následující text:

 ```console
 home
 work
```

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Vlastnosti osy XML](index.md)
- [Literály XML](../xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Rozšiřující metody](../../programming-guide/language-features/procedures/extension-methods.md)
- [Vlastnost indexeru rozšíření](extension-indexer-property.md)
- [Vlastnost osy podřízeného XML](xml-child-axis-property.md)
- [Vlastnost osy atributu XML](xml-attribute-axis-property.md)
