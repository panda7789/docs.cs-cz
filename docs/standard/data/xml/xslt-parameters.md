---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282529"
---
# <a name="xslt-parameters"></a>Parametry XSLT
Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody pomocí metody. Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu Parameter.  
  
### <a name="to-use-an-xslt-parameter"></a>Použití parametru XSLT  
  
1. Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> objekt a přidejte parametr pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.  
  
2. Zavolejte parametr ze seznamu stylů.  
  
3. Předat <xref:System.Xml.Xsl.XsltArgumentList> objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.  
  
## <a name="parameter-types"></a>Typy parametrů  
 Objekt Parameter by měl odpovídat typu W3C. V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní třídy Microsoft .NET (typ) a zda typ W3C je typ XPath nebo typ XSLT.  
  
|Typ W3C|Ekvivalentní třída .NET (typ)|Typ XPath nebo XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|SOUBORU|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator []**|XPath|  
  
 * To je ekvivalent sady uzlů, která obsahuje jeden uzel.  
  
 Pokud objekt Parameter není jedna z výše uvedených tříd, je převedena podle následujících pravidel. Číselné typy modulu CLR (Common Language Runtime) jsou převedeny na <xref:System.Double> . <xref:System.DateTime>Typ je převeden na <xref:System.String> . <xref:System.Xml.XPath.IXPathNavigable>typy jsou převedeny na <xref:System.Xml.XPath.XPathNavigator> . **Prvek XPathNavigator []** je převeden na <xref:System.Xml.XPath.XPathNodeIterator> .  
  
 Všechny ostatní typy vyvolávají chybu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu k vytvoření parametru pro uchování počítaného data slevy. Datum slevy se počítá jako 20 dní od data objednávky.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Vstup  
  
##### <a name="orderxml"></a>Order. XML  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>sleva. xsl  
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

- [Transformace XSLT](xslt-transformations.md)
