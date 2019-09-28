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
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592170"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace – operátor (Visual Basic)
Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá zadané předponě oboru názvů XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelný parametr. Řetězec, který identifikuje předponu oboru názvů XML. Je-li tento řetězec zadán, musí být platným identifikátorem XML. Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Pokud není zadána žádná předpona, je vrácen výchozí obor názvů. Pokud není zadán žádný výchozí obor názvů, je vrácen prázdný obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `GetXmlNamespace` Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML `xmlNamespacePrefix`.  
  
 Předpony oboru názvů XML lze použít přímo v literálech XML a vlastnostech osy XML. Je však nutné použít operátor `GetXmlNamespace` pro převod předpony oboru názvů na objekt <xref:System.Xml.Linq.XNamespace> předtím, než jej můžete použít ve svém kódu. Chcete-li získat plně kvalifikovaný objekt <xref:System.Xml.Linq.XName>, který vyžaduje mnoho metod [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete k objektu <xref:System.Xml.Linq.XNamespace> připojit Nekvalifikovaný název elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu, který má kvalifikovaný název `ns:phone`. Pak předá tento podřízený uzel dílčí rutině `ShowName`, která vytvoří kvalifikovaný název pomocí operátoru `GetXmlNamespace`. Podprogram `ShowName` poté předává kvalifikovaný název metodě <xref:System.Xml.Linq.XNode.Ancestors%2A> pro získání nadřazeného uzlu `ns:contact`.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Když zavoláte `TestGetXmlNamespace.RunSample()`, zobrazí se okno se zprávou, které obsahuje následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Přístup k XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
