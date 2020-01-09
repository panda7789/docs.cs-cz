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
Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> přijímá tři vstupní typy pro zdrojový dokument: objekt, který implementuje rozhraní <xref:System.Xml.XPath.IXPathNavigable>, objekt <xref:System.Xml.XmlReader>, který čte zdrojový dokument, nebo identifikátor URI řetězce.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslCompiledTransform> ve výchozím nastavení zachovává prázdné znaky. To je v souladu s [oddílem 3,4 doporučení W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Rozhraní IXPathNavigable  
 Rozhraní <xref:System.Xml.XPath.IXPathNavigable> je implementováno v třídách <xref:System.Xml.XmlNode> a <xref:System.Xml.XPath.XPathDocument>. Tyto třídy reprezentují mezipaměť dat XML v paměti.  
  
- Třída <xref:System.Xml.XmlNode> je založena na formátu W3C model DOM (Document Object Model) (DOM) a zahrnuje možnosti úprav.  
  
- Třída <xref:System.Xml.XPath.XPathDocument> je úložiště dat jen pro čtení založené na datovém modelu XPath. <xref:System.Xml.XPath.XPathDocument> je doporučená třída pro zpracování XSLT. Ve srovnání s <xref:System.Xml.XmlNode> třídou poskytuje rychlejší výkon.  
  
> [!NOTE]
> Transformace se vztahují na dokument jako celek. Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu. Chcete-li transformovat fragment uzlu, je nutné vytvořit objekt obsahující pouze fragment uzlu a předat tento objekt metodě <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Další informace naleznete v tématu [How to: Transforming fragment Node](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 Následující příklad používá metodu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objekt XmlReader  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> se načte z aktuálního uzlu <xref:System.Xml.XmlReader> prostřednictvím všech jejích podřízených objektů. To umožňuje použít část dokumentu jako kontextový dokument. Po návratu metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> se <xref:System.Xml.XmlReader> umístí na další uzel po konci kontextu dokumentu. Pokud je dosaženo konce dokumentu, <xref:System.Xml.XmlReader> je umístěn na konci souboru (EOF).  
  
 Následující příklad používá metodu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identifikátor URI řetězce  
 Identifikátor URI zdrojového dokumentu můžete zadat také jako vstup XSLT. K překladu identifikátoru URI se používá <xref:System.Xml.XmlResolver>. Můžete určit <xref:System.Xml.XmlResolver> pro použití předáním do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Pokud není zadán <xref:System.Xml.XmlResolver>, metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> používá výchozí <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.  
  
 Následující příklad používá metodu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pro transformaci souboru Books. XML na soubor Books. HTML pomocí šablony stylů Transform. Xsl. Soubory Books. XML a Transform. xsl lze nalézt v tomto tématu: [Postupy: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Další informace najdete v tématu [řešení externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
