---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924942"
---
# <a name="xslt-extension-objects"></a>Objekty rozšíření XSLT
Objekty rozšíření slouží k rozšíření funkcí šablon stylů. Objekty rozšíření jsou spravovány <xref:System.Xml.Xsl.XsltArgumentList> třídou.  
  
 Níže jsou výhody použití objektu rozšíření místo vloženého skriptu:  
  
- Poskytuje lepší zapouzdření a opakované použití tříd.  
  
- Povoluje, aby byly šablony stylů menší a udržovatelnější.  
  
 Objekty rozšíření XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> objektu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> pomocí metody. Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.  
  
> [!NOTE]
> Pro volání <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody je vyžadována sada oprávnění FullTrust. Další informace najdete v tématu [zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md) a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř `number`základních datových typů XPath, `string`, `Boolean`a `node set`.  
  
 Všechny metody, které jsou definovány pomocí `params` klíčového slova, které umožňuje předat nespecifikovaný počet parametrů, není aktuálně podporována <xref:System.Xml.Xsl.XslCompiledTransform> třídou. Šablony stylů XSLT, které využívají jakoukoli metodu definovanou s `params` klíčovým slovem, nebudou správně fungovat. Podrobnosti najdete v tématu [param](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Použití objektu rozšíření XSLT  
  
1. Vytvořte objekt a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. <xref:System.Xml.Xsl.XsltArgumentList>  
  
2. Zavolejte objekt rozšíření ze seznamu stylů.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> Předat objekt<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
