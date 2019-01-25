---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab96d5bdefee0cd85d98174f8f7410e940cb12b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498369"
---
# <a name="xslt-extension-objects"></a>Objekty rozšíření XSLT
Rozšíření objektů se používají k rozšíření funkcí šablon stylů. Rozšíření objektů jsou udržovány <xref:System.Xml.Xsl.XsltArgumentList> třídy.  
  
 Následují výhody použití objekt rozšíření místo vloženého skriptu:  
  
-   Poskytuje lepší zapouzdření a opakované použití tříd.  
  
-   Povoluje stylů, aby bylo menší a jednodušší údržbu.  
  
 Objekty rozšíření XSLT se přidají do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.  
  
> [!NOTE]
>  Sada oprávnění FullTrust je potřeba volat <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Další informace najdete v tématu [zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md) a [NIB: Pojmenované sady oprávnění](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath data z `number`, `string`, `Boolean`, a `node set`.  
  
 Jakoukoli metodu, která je definována s `params` klíčové slovo, které umožňuje neurčené počtu parametrů, se aktuálně nepodporují <xref:System.Xml.Xsl.XslCompiledTransform> třídy. XSLT šablony stylů, které využívají jakékoli metody definované `params` – klíčové slovo nebude fungovat správně. Podrobnosti najdete v tématu [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Použití objektu rozšíření XSLT  
  
1.  Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.  
  
2.  Volání objektu rozšíření ze šablony stylů.  
  
3.  Předání <xref:System.Xml.Xsl.XsltArgumentList> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
