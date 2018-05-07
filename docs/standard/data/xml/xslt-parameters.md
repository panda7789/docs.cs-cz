---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef57d16c52100398919563205a97205be3c5dd7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 Pokud objekt parametr není jedním z výše uvedených tříd, převede se podle následujících pravidel. Common language runtime (CLR) číselnými typy jsou převedeny na <xref:System.Double>. <xref:System.DateTime> Typ je převeden na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>. **[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
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
