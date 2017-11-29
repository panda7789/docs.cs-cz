---
title: Parametry XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e66d98501bb0bd3a5d5cd5eacc0b09405c158522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-parameters"></a>Parametry XSLT
Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda. Kvalifikovaný název a identifikátor URI oboru názvů jsou přidruženy k objektu parametru v daném čase.  
  
### <a name="to-use-an-xslt-parameter"></a>Použití parametru XSLT  
  
1.  Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.  
  
2.  Parametr volejte z této šablony.  
  
3.  Předat <xref:System.Xml.Xsl.XsltArgumentList> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.  
  
## <a name="parameter-types"></a>Typy parametrů  
 Objekt parametr by měl odpovídat typu W3C. Následující tabulka uvádí odpovídající typy W3C ekvivalentní třídy rozhraní Microsoft .NET (typ), a zda je typ W3C XPath typ nebo typ XSLT.  
  
|Typ W3C|Ekvivalentní třída .NET (typ)|Typ XPath nebo XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **[] Objektem XPathNavigator nastaveným na**|XPath|  
  
 * Jde o ekvivalent sada uzlů, který obsahuje jeden uzel.  
  
 Pokud objekt parametr není jedním z výše uvedených tříd, převede se podle následujících pravidel. Common language runtime (CLR) číselnými typy jsou převedeny na <xref:System.Double>. <xref:System.DateTime> Typ je převeden na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable>typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>. **[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Všechny ostatní typy vyvolána chyba.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení počítané datum slevy. Datum slevy je vypočítána na 20 dní od data pořadí.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Vstup  
  
##### <a name="orderxml"></a>Order.XML  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>discount.xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Výstup  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
