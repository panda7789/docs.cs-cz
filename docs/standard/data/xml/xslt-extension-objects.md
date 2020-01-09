---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 6ad5b5140239ad7dc0ad72e65d10af744dfbd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709709"
---
# <a name="xslt-extension-objects"></a>Objekty rozšíření XSLT
Objekty rozšíření slouží k rozšíření funkcí šablon stylů. Objekty rozšíření jsou spravovány třídou <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Níže jsou výhody použití objektu rozšíření místo vloženého skriptu:  
  
- Poskytuje lepší zapouzdření a opakované použití tříd.  
  
- Povoluje, aby byly šablony stylů menší a udržovatelnější.  
  
 Objekty rozšíření XSLT jsou přidány do objektu <xref:System.Xml.Xsl.XsltArgumentList> pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.  
  
> [!NOTE]
> Pro volání metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> je vyžadována sada oprávnění FullTrust. Další informace najdete v tématu [zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md) a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř základních datových typů XPath `number`, `string`, `Boolean`a `node set`.  
  
 Jakákoliv metoda, která je definována s klíčovým slovem `params`, které umožňuje předání nespecifikovaného počtu parametrů, není aktuálně podporována třídou <xref:System.Xml.Xsl.XslCompiledTransform>. Šablony stylů XSLT, které využívají libovolnou metodu definovanou s klíčovým slovem `params`, nebudou správně fungovat. Podrobnosti najdete v tématu [param](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Použití objektu rozšíření XSLT  
  
1. Vytvořte objekt <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Zavolejte objekt rozšíření ze seznamu stylů.  
  
3. Předejte objekt <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
