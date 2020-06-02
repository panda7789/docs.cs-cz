---
title: 'Postupy: Transformace fragmentu uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: e44f44db3e12c5e297f137fa247ecfc2d809dd4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287711"
---
# <a name="how-to-transform-a-node-fragment"></a>Postupy: Transformace fragmentu uzlu
Při transformaci dat obsažených v <xref:System.Xml.XmlDocument> objektu nebo <xref:System.Xml.XPath.XPathDocument> se transformace XSLT vztahují na dokument jako celek. Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu. Chcete-li transformovat fragment uzlu, je nutné vytvořit samostatný objekt obsahující pouze fragment uzlu a předat tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>Transformace fragmentu uzlu  
  
1. Vytvořte objekt obsahující zdrojový dokument.  
  
2. Najděte fragment uzlu, který chcete transformovat.  
  
3. Vytvořte samostatný objekt se pouze fragmentem uzlu.  
  
4. Předejte fragment uzlu do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad transformuje fragment uzlu a výstupy výsledků do konzoly.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Vstup  
  
##### <a name="booksxml"></a>Books. XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single. xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Výstup  
 Titul knihy je důvěryhodný člověk.  
  
## <a name="see-also"></a>Viz také

- [Používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md)
