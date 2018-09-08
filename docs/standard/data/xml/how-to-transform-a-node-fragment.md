---
title: 'Postupy: transformace fragmentu uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb258b61664e1fdbf6604afdf69074c48cf5bda4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44134997"
---
# <a name="how-to-transform-a-node-fragment"></a>Postupy: transformace fragmentu uzlu
Při transformaci dat obsažených v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT se vztahují k dokumentu jako celek. Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument. Transformace fragmentu uzlu, musíte vytvořit samostatný objekt obsahující pouze fragmentu uzlu a předejte tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>Transformace fragmentu uzlu  
  
1.  Vytvořte objekt, který obsahuje zdrojový dokument.  
  
2.  Vyhledání fragmentu uzlu, který chcete transformovat.  
  
3.  Vytvořte samostatný objekt s právě fragmentu uzlu.  
  
4.  Předejte fragmentu uzlu na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu transformace fragmentu uzlu a vypíše výsledky do konzoly.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Vstup  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Výstup  
 Název knihy se požadavek spolehlivosti  
  
## <a name="see-also"></a>Viz také:

- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
