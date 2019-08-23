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
ms.openlocfilehash: 043c37a17375bf2dcdad9e4b429cfca7b96ef7cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966976"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Vstupy do třídy XslCompiledTransform
Metoda přijímá tři vstupní typy zdrojového dokumentu: objekt, který <xref:System.Xml.XPath.IXPathNavigable> implementuje rozhraní, <xref:System.Xml.XmlReader> objekt, který čte zdrojový dokument, nebo identifikátor URI řetězce. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> Třída ve výchozím nastavení zachovává prázdné znaky. To je v souladu s [oddílem 3,4 doporučení W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Rozhraní IXPathNavigable  
 Rozhraní je implementováno <xref:System.Xml.XmlNode> v třídách <xref:System.Xml.XPath.XPathDocument>a. <xref:System.Xml.XPath.IXPathNavigable> Tyto třídy reprezentují mezipaměť dat XML v paměti.  
  
- <xref:System.Xml.XmlNode> Třída je založena na model DOM (Document Object Model) W3C (DOM) a zahrnuje možnosti úprav.  
  
- <xref:System.Xml.XPath.XPathDocument> Třída je úložiště dat jen pro čtení založené na datovém modelu XPath. <xref:System.Xml.XPath.XPathDocument>je doporučenou třídou pro zpracování XSLT. V <xref:System.Xml.XmlNode> porovnání s třídou poskytuje rychlejší výkon.  
  
> [!NOTE]
> Transformace se vztahují na dokument jako celek. Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu. Chcete-li transformovat fragment uzlu, je nutné vytvořit objekt obsahující pouze fragment uzlu a předat tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě. Další informace najdete v tématu [jak: Transformuje fragment](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)uzlu.  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl najdete v tomto tématu: [Postupy: Provede transformaci XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objekt XmlReader  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> se načte z aktuálního uzlu <xref:System.Xml.XmlReader> všech jejích podřízených objektů. To umožňuje použít část dokumentu jako kontextový dokument. Poté, co metoda vrátí, je umístěn na dalším uzlu po konci kontextu dokumentu. <xref:System.Xml.XmlReader> <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Pokud je dosaženo konce dokumentu, <xref:System.Xml.XmlReader> je umístěn na konci souboru (EOF).  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl najdete v tomto tématu: [Postupy: Provede transformaci XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identifikátor URI řetězce  
 Identifikátor URI zdrojového dokumentu můžete zadat také jako vstup XSLT. <xref:System.Xml.XmlResolver> Používá se k překladu identifikátoru URI. Můžete určit, <xref:System.Xml.XmlResolver> aby se použilo předáním <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> do metody. Pokud není zadán <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> , použije metoda výchozí <xref:System.Xml.XmlUrlResolver> hodnotu bez pověření. <xref:System.Xml.XmlResolver>  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodu pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl najdete v tomto tématu: [Postupy: Provede transformaci XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Další informace najdete v tématu [řešení externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
