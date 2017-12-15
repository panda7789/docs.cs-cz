---
title: Vlastnost hodnoty XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9294c2d1d83dce3bca2abc22ee9c70296fc8014
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="xml-value-property-visual-basic"></a>Vlastnost hodnoty XML (Visual Basic)
Poskytuje přístup k hodnotě první prvek kolekce <xref:System.Xml.Linq.XElement> objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`object`|Požadováno. Kolekce <xref:System.Xml.Linq.XElement> objekty.|  
  
## <a name="return-value"></a>Návratová hodnota  
 A `String` obsahující hodnotu první prvek kolekce, nebo `Nothing` Pokud kolekce je prázdná.  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastnost usnadňuje přístup k hodnotě prvním elementem v kolekci <xref:System.Xml.Linq.XElement> objekty. Tato vlastnost nejprve ověří, zda kolekce obsahuje minimálně jeden objekt. Pokud je kolekce prázdná, vrátí tato vlastnost `Nothing`. Jinak, vrátí tato vlastnost hodnotu <xref:System.Xml.Linq.XElement.Value%2A> vlastnost první prvek v kolekci.  
  
> [!NOTE]
>  Když k hodnotě atributu XML pomocí ' @' identifikátor, jako je vrácena hodnota atributu `String` a není nutné explicitně zadat <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnost.  
  
 Pro přístup k další elementy v kolekci, můžete použít vlastnost indexeru rozšíření XML. Další informace najdete v tématu [vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Dědičnost  
 Většina uživatelé nebudou mít k implementaci <xref:System.Collections.Generic.IEnumerable%601>a proto můžete ignorovat v této části.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Vlastnost je vlastnost rozšíření pro typy, které implementují `IEnumerable(Of XElement)`. Vazba této vlastnosti rozšíření je třeba vazby metod rozšíření: Pokud typu implementuje jednomu z rozhraní a definuje vlastnost, která má název "Value", tato vlastnost má vyšší prioritu než vlastnost rozšíření. Jinými slovy to <xref:System.Xml.Linq.XElement.Value%2A> mohou být přepsány vlastnosti definovat nové vlastnosti ve třídě, která implementuje `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Xml.Linq.XElement.Value%2A> vlastnost, která má přístup k první uzel v kolekci <xref:System.Xml.Linq.XElement> objekty. Příklad používá vlastnost osy podřízeného k získání kolekce všechny podřízené uzly s názvem `phone` , které jsou v `contact` objektu.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak získat hodnotu atributu XML z kolekce <xref:System.Xml.Linq.XAttribute> objekty. Příklad používá vlastnost osy atributu k zobrazit hodnotu `type` atribut pro všechny `phone` elementy.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Tento kód zobrazí následující text:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Vlastnost indexeru rozšíření](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [Vlastnost osy podřízeného XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [Vlastnost osy atributu XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
