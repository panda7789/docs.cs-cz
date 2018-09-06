---
title: Vstupy do třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e09828b827b12645ebbf37d62a346c8877bfba05
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865732"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Vstupy do třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda přijímá tři vstupní typy pro zdrojový dokument: objekt, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, <xref:System.Xml.XmlReader> objekt, který přečte zdrojový dokument nebo řetězec identifikátoru URI.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslCompiledTransform> Třídy zachová prázdné místo ve výchozím nastavení. Toto je v souladu s části 3.4 doporučení W3C XSLT 1.0 (části 3.4, http://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Rozhraní IXPathNavigable  
 <xref:System.Xml.XPath.IXPathNavigable> Rozhraní je implementováno v <xref:System.Xml.XmlNode> a <xref:System.Xml.XPath.XPathDocument> třídy. Tyto třídy představují mezipaměti dat XML.  
  
-   <xref:System.Xml.XmlNode> Třídy je založený na W3C Document Object Model (DOM) a obsahuje funkce pro úpravy.  
  
-   <xref:System.Xml.XPath.XPathDocument> Třída je úložiště jen pro čtení dat na základě modelu dat XPath. <xref:System.Xml.XPath.XPathDocument> zpracovává doporučené třídy pro XSLT. Poskytuje rychlejší výkon ve srovnání s <xref:System.Xml.XmlNode> třídy.  
  
> [!NOTE]
>  Transformace se vztahují k dokumentu jako celek. Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument. Transformace fragmentu uzlu, musíte vytvořit objekt, který obsahuje pouze fragmentu uzlu a předejte tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Další informace najdete v tématu [postupy: transformace fragmentu uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 V následujícím příkladu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody k transformaci soubor books.xml books.html souboru pomocí transform.xsl šablony stylů. Soubory books.xml a transform.xsl lze nalézt v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objekt XmlReader  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda načte z aktuálního uzlu <xref:System.Xml.XmlReader> přes všechny jeho podřízené objekty. To umožňuje využít část dokumentu jako kontext dokumentu. Poté, co <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda vrátí hodnotu, <xref:System.Xml.XmlReader> je umístěn na další uzel za konec dokumentu kontextu. Pokud je dosaženo konce dokumentu, <xref:System.Xml.XmlReader> je umístěn na konci souboru (EOF).  
  
 V následujícím příkladu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody k transformaci soubor books.xml books.html souboru pomocí transform.xsl šablony stylů. Soubory books.xml a transform.xsl lze nalézt v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Řetězec identifikátoru URI  
 Identifikátor URI dokumentu zdroje můžete určit také jako vaše XSLT vstup. <xref:System.Xml.XmlResolver> Slouží k rozpoznání identifikátoru URI. Můžete zadat <xref:System.Xml.XmlResolver> použít ji k <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Pokud <xref:System.Xml.XmlResolver> není zadán, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda používá výchozí <xref:System.Xml.XmlUrlResolver> bez pověření.  
  
 V následujícím příkladu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody k transformaci soubor books.xml books.html souboru pomocí transform.xsl šablony stylů. Soubory books.xml a transform.xsl lze nalézt v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Další informace najdete v tématu [překlad externích prostředků během XSLT zpracování](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
