---
title: 'Postupy: transformace Fragment uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd35e469a16dc2fdb3a7f4afd89d04f67185cd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-a-node-fragment"></a>Postupy: transformace Fragment uzlu
Při transformaci data obsažená v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT vztahují k dokumentu jako celku. Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu. K transformaci fragment uzlu, musíte vytvořit samostatný objekt obsahující pouze fragment uzlu a předat tento objekt, který chcete <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>K transformaci fragment uzlu  
  
1.  Vytvořte objekt, který obsahuje zdrojový dokument.  
  
2.  Vyhledejte fragment uzlu, který si přejete transformace.  
  
3.  Vytvořte samostatný objekt s právě fragment uzlu.  
  
4.  Předat uzlu fragment k <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad transformuje fragment uzlu a výsledky do konzoly.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Vstup  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Výstup  
 Název adresáře je Man spolehlivosti  
  
## <a name="see-also"></a>Viz také  
 [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
