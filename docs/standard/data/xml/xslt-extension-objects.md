---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 03e24153cc11c139fc9d9e692ef93bd82c51ee3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282594"
---
# <a name="xslt-extension-objects"></a>Objekty rozšíření XSLT
Objekty rozšíření slouží k rozšíření funkcí šablon stylů. Objekty rozšíření jsou spravovány <xref:System.Xml.Xsl.XsltArgumentList> třídou.  
  
 Níže jsou výhody použití objektu rozšíření místo vloženého skriptu:  
  
- Poskytuje lepší zapouzdření a opakované použití tříd.  
  
- Povoluje, aby byly šablony stylů menší a udržovatelnější.  
  
 Objekty rozšíření XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> objektu pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.  
  
> [!NOTE]
> Pro volání metody je vyžadována sada oprávnění FullTrust <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Další informace najdete v tématu [zabezpečení přístupu kódu](../../../framework/misc/code-access-security.md) a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř základních datových typů XPath `number` , `string` , `Boolean` a `node set` .  
  
 Všechny metody, které jsou definovány pomocí `params` klíčového slova, které umožňuje předat nespecifikovaný počet parametrů, není aktuálně podporována <xref:System.Xml.Xsl.XslCompiledTransform> třídou. Šablony stylů XSLT, které využívají jakoukoli metodu definovanou s `params` klíčovým slovem, nebudou správně fungovat. Podrobnosti najdete v tématu [param](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Použití objektu rozšíření XSLT  
  
1. Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> objekt a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.  
  
2. Zavolejte objekt rozšíření ze seznamu stylů.  
  
3. Předat <xref:System.Xml.Xsl.XsltArgumentList> objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.  
  
## <a name="see-also"></a>Viz také

- [Transformace XSLT](xslt-transformations.md)
- [Aspekty zabezpečení XSLT](xslt-security-considerations.md)
