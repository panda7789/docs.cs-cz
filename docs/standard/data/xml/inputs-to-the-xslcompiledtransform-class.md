---
title: Vstupy do třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: 9aae85aa4516dc0555e959358ba1b7db3002145d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710736"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Vstupy do třídy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda přijímá tři vstupní typy zdrojového dokumentu: objekt, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní, <xref:System.Xml.XmlReader> objekt, který čte zdrojový dokument, nebo identifikátor URI řetězce.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> Třída ve výchozím nastavení zachovává prázdné znaky. To je v souladu s [oddílem 3,4 doporučení W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Rozhraní IXPathNavigable  
 <xref:System.Xml.XPath.IXPathNavigable> Rozhraní je implementováno v třídách <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlNode> a. Tyto třídy reprezentují mezipaměť dat XML v paměti.  
  
- <xref:System.Xml.XmlNode> Třída je založena na model DOM (Document Object Model) W3C (DOM) a zahrnuje možnosti úprav.  
  
- <xref:System.Xml.XPath.XPathDocument> Třída je úložiště dat jen pro čtení založené na datovém modelu XPath. <xref:System.Xml.XPath.XPathDocument>je doporučenou třídou pro zpracování XSLT. V <xref:System.Xml.XmlNode> porovnání s třídou poskytuje rychlejší výkon.  
  
> [!NOTE]
> Transformace se vztahují na dokument jako celek. Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu. Chcete-li transformovat fragment uzlu, je nutné vytvořit objekt obsahující pouze fragment uzlu a předat tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě. Další informace naleznete v tématu [How to: Transforming fragment Node](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objekt XmlReader  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> se načte z aktuálního uzlu <xref:System.Xml.XmlReader> všech jejích podřízených objektů. To umožňuje použít část dokumentu jako kontextový dokument. Poté, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> co metoda vrátí, <xref:System.Xml.XmlReader> je umístěn na dalším uzlu po konci kontextu dokumentu. Pokud je dosaženo konce dokumentu, <xref:System.Xml.XmlReader> je umístěn na konci souboru (EOF).  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identifikátor URI řetězce  
 Identifikátor URI zdrojového dokumentu můžete zadat také jako vstup XSLT. <xref:System.Xml.XmlResolver> Používá se k překladu identifikátoru URI. Můžete určit, <xref:System.Xml.XmlResolver> aby se použilo předáním do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Pokud <xref:System.Xml.XmlResolver> není zadán, použije <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda výchozí <xref:System.Xml.XmlUrlResolver> hodnotu bez pověření.  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Další informace najdete v tématu [řešení externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Viz také

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
