---
title: GetXmlNamespace – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603480"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace – operátor (Visual Basic)
Získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá zadané předpony oboru názvů XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelné. Řetězec, který identifikuje Předpona oboru názvů XML. Pokud je zadaný, tento řetězec musí být platný identifikátor XML. Další informace najdete v tématu [názvy z deklarovaný XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Pokud žádná předpona. není zadaný, je vrácen výchozí obor názvů. Pokud není zadán žádný výchozí obor názvů, je vrácena prázdného oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XNamespace> Objekt, který odpovídá Předpona oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 `GetXmlNamespace` Získá operátor <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá Předpona oboru názvů XML `xmlNamespacePrefix`.  
  
 XML – předpony oboru názvů přímo v literály XML a vlastnosti osy XML můžete použít. Ale musí používat `GetXmlNamespace` operátor převést předpony oboru názvů <xref:System.Xml.Linq.XNamespace> objektu před použitím v kódu. Přidáte-název nekvalifikované elementu k <xref:System.Xml.Linq.XNamespace> objekt, který chcete získat plně kvalifikovaný <xref:System.Xml.Linq.XName> objektu, který mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody vyžadují.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje `ns` jako předponu oboru názvů XML. Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel, který má úplný název `ns:phone`. Poté předá tento podřízený uzel k `ShowName` podprogramu, který vytvoří úplný název pomocí `GetXmlNamespace` operátor. `ShowName` Podprogramu pak předá kvalifikovaný název do <xref:System.Xml.Linq.XNode.Ancestors%2A> metoda získat nadřazené `ns:contact` uzlu.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Při volání `TestGetXmlNamespace.RunSample()`, zobrazí se okno se zprávou, která obsahuje následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Přístup XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
