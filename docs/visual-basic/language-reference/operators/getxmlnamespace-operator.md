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
ms.openlocfilehash: 757ca54e5ba370bf2cc48bc70499e7b43ec96ef6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751368"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace – operátor (Visual Basic)
Získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá zadané předpony oboru názvů XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelné. Řetězec, který identifikuje předponu oboru názvů XML. Pokud je zadané, musí být tento řetězec neplatný identifikátor XML. Další informace najdete v tématu [názvy z deklarované XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Pokud není zadána žádná předpona, vrátí se výchozí obor názvů. Pokud není zadán žádný výchozí obor názvů, je vrácena prázdný obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XNamespace> Objekt, který odpovídá předponu oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 `GetXmlNamespace` Získá operátor <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá předponu oboru názvů XML `xmlNamespacePrefix`.  
  
 Můžete používat předpony oboru názvů XML přímo v literály XML a vlastnosti OS XML. Ale musí používat `GetXmlNamespace` operátor převodu předpony oboru názvů <xref:System.Xml.Linq.XNamespace> objektu před použitím v kódu. Můžete přidat název nekvalifikované elementu do <xref:System.Xml.Linq.XNamespace> můžete získat plně kvalifikovaný <xref:System.Xml.Linq.XName> objekt, který mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody vyžadují.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje `ns` jako předponu oboru názvů XML. Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel, který má úplný název `ns:phone`. Pak předá tento podřízeného uzlu `ShowName` podprogram, který vytvoří úplný název pomocí `GetXmlNamespace` operátor. `ShowName` Podprogram pak předá kvalifikovaný název <xref:System.Xml.Linq.XNode.Ancestors%2A> metodu k získání nadřazené `ns:contact` uzlu.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Při volání `TestGetXmlNamespace.RunSample()`, zobrazí okno se zprávou, která obsahuje následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Přístup ke XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
