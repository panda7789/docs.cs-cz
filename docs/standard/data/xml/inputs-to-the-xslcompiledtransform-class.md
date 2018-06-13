---
title: Vstupy XslCompiledTransform – třída
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc909b666b90d8c8825e7dbef33e48b6126bd7c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572837"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Vstupy XslCompiledTransform – třída
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda přijímá tři vstupních typů pro zdrojový dokument: objekt, který implementuje <xref:System.Xml.XPath.IXPathNavigable> rozhraní <xref:System.Xml.XmlReader> objekt, který čte zdrojový dokument nebo řetězce URI.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslCompiledTransform> Třída zachovává mezer ve výchozím nastavení. Toto je v souladu s části 3.4 doporučení W3C XSLT 1.0 (část 3.4, http://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable rozhraní  
 <xref:System.Xml.XPath.IXPathNavigable> Rozhraní je implementováno v <xref:System.Xml.XmlNode> a <xref:System.Xml.XPath.XPathDocument> třídy. Tyto třídy představují mezipaměť v paměti se XML data.  
  
-   <xref:System.Xml.XmlNode> Třída je založena na W3C Model DOM (Document Object) a obsahuje funkce pro úpravy.  
  
-   <xref:System.Xml.XPath.XPathDocument> Třída je jen pro čtení datové úložiště, na základě modelu dat XPath. <xref:System.Xml.XPath.XPathDocument> zpracovává doporučené třídu pro XSLT. Poskytuje vyšší výkon ve srovnání s <xref:System.Xml.XmlNode> třídy.  
  
> [!NOTE]
>  Transformace se vztahují k dokumentu jako celku. Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu. K transformaci fragment uzlu, musíte vytvořit objekt obsahující pouze fragment uzlu a předat tento objekt, který chcete <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda. Další informace najdete v tématu [postupy: transformace Fragment uzlu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metoda k transformaci souboru books.xml books.html soubor pomocí šablony stylů transform.xsl. Soubory books.xml a transform.xsl najdete v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objekt XmlReader  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda načte z aktuálního uzlu <xref:System.Xml.XmlReader> prostřednictvím všechny její podřízené položky. To umožňuje používat část dokument jako dokument kontextu. Po <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda vrátí <xref:System.Xml.XmlReader> je umístěn na další uzel za konec dokumentu kontextu. Když je dosaženo konce dokumentu, <xref:System.Xml.XmlReader> je nastavený na konec souboru (EOF).  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metoda k transformaci souboru books.xml books.html soubor pomocí šablony stylů transform.xsl. Soubory books.xml a transform.xsl najdete v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Řetězec identifikátoru URI  
 Můžete také určit zdrojový dokument URI jako vaše XSLT vstup. <xref:System.Xml.XmlResolver> Se používá k překladu identifikátor URI. Můžete zadat <xref:System.Xml.XmlResolver> předáním jeho <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda. Pokud <xref:System.Xml.XmlResolver> není zadán, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda používá výchozí <xref:System.Xml.XmlUrlResolver> bez pověření.  
  
 Následující příklad používá <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metoda k transformaci souboru books.xml books.html soubor pomocí šablony stylů transform.xsl. Soubory books.xml a transform.xsl najdete v tomto tématu: [postup: provedení transformace XSLT pomocí sestavení](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Další informace najdete v tématu [řešení externí prostředky během XSLT zpracování](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
