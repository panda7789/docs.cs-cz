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
ms.openlocfilehash: 85422fb9e11d78e228577adc25cba746149c645a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371113"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace – operátor (Visual Basic)
Získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá zadané předponě oboru názvů XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Součásti  
 `xmlNamespacePrefix`  
 Nepovinný parametr. Řetězec, který identifikuje předponu oboru názvů XML. Je-li tento řetězec zadán, musí být platným identifikátorem XML. Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Pokud není zadána žádná předpona, je vrácen výchozí obor názvů. Pokud není zadán žádný výchozí obor názvů, je vrácen prázdný obor názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XNamespace>Objekt, který odpovídá předponě oboru názvů XML.  
  
## <a name="remarks"></a>Poznámky  
 `GetXmlNamespace`Operátor získá <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá předponě oboru názvů XML `xmlNamespacePrefix` .  
  
 Předpony oboru názvů XML lze použít přímo v literálech XML a vlastnostech osy XML. Je však nutné použít `GetXmlNamespace` operátor pro převod předpony oboru názvů na <xref:System.Xml.Linq.XNamespace> objekt předtím, než jej můžete použít ve svém kódu. K objektu můžete připojit Nekvalifikovaný název elementu <xref:System.Xml.Linq.XNamespace> , abyste získali plně kvalifikovaný <xref:System.Xml.Linq.XName> objekt, který mnoho [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metod vyžaduje.  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje `ns` jako předponu oboru názvů XML. Potom používá předponu oboru názvů k vytvoření literálu XML a přístup k prvnímu podřízenému uzlu, který má kvalifikovaný název `ns:phone` . Poté předá tento podřízený uzel dílčí `ShowName` rutinou, která vytvoří úplný název pomocí `GetXmlNamespace` operátoru. `ShowName`Podprogram pak předá do metody kvalifikovaný název <xref:System.Xml.Linq.XNode.Ancestors%2A> pro získání nadřazeného `ns:contact` uzlu.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Když zavoláte `TestGetXmlNamespace.RunSample()` , zobrazí se okno se zprávou, které obsahuje následující text:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Viz také

- [Imports – Příkaz (obor názvů XML)](../statements/imports-statement-xml-namespace.md)
- [Přístup ke XML v jazyce Visual Basic](../../programming-guide/language-features/xml/accessing-xml.md)
