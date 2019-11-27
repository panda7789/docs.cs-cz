---
title: GetXmlNamespace – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353196"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace – operátor (Visual Basic)
Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá zadané předponě oboru názvů XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Volitelná. Řetězec, který identifikuje předponu oboru názvů XML. Je-li tento řetězec zadán, musí být platným identifikátorem XML. Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Pokud není zadána žádná předpona, je vrácen výchozí obor názvů. Pokud není zadán žádný výchozí obor názvů, je vrácen prázdný obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `GetXmlNamespace` Získá objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá předponě oboru názvů XML `xmlNamespacePrefix`.  
  
 Předpony oboru názvů XML lze použít přímo v literálech XML a vlastnostech osy XML. Je však nutné použít operátor `GetXmlNamespace` k převedení předpony oboru názvů na objekt <xref:System.Xml.Linq.XNamespace> předtím, než jej můžete použít ve svém kódu. K objektu <xref:System.Xml.Linq.XNamespace> můžete připojit Nekvalifikovaný název elementu, abyste získali plně kvalifikovaný <xref:System.Xml.Linq.XName> objekt, který vyžaduje mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metod.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje `ns` jako předponu oboru názvů XML. Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu, který má kvalifikovaný název `ns:phone`. Poté předává tento podřízený uzel do dílčí rutiny `ShowName`, která vytvoří kvalifikovaný název pomocí operátoru `GetXmlNamespace`. Podprogram `ShowName` pak předá metodě <xref:System.Xml.Linq.XNode.Ancestors%2A>, aby získal nadřazený `ns:contact` uzel.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Při volání `TestGetXmlNamespace.RunSample()`se zobrazí okno se zprávou, které obsahuje následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Přístup k XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
