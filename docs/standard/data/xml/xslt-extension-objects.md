---
title: "Rozšíření objektů XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2916f7da6b990cddef9b86559a71b5206351d558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-extension-objects"></a>Rozšíření objektů XSLT
Rozšíření objektů se používají k rozšíření funkcí stylů. Rozšíření objektů jsou udržované <xref:System.Xml.Xsl.XsltArgumentList> třídy.  
  
 Následují výhody použití rozšíření namísto objektu vložený skript:  
  
-   Poskytuje lepší zapouzdření a opakovaného použití třídy.  
  
-   Umožňuje stylů menší a více udržovatelný.  
  
 XSLT rozšíření objekty jsou přidány na <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda. Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.  
  
> [!NOTE]
>  Sada oprávnění FullTrust je třeba volat <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda. Další informace najdete v tématu [zabezpečení přístupu kódu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) a [NIB: pojmenované sady oprávnění](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath data z `number`, `string`, `Boolean`, a `node set`.  
  
 Libovolné metody, která je definovaná pomocí `params` – klíčové slovo, která umožňuje neurčené počet parametrů, není aktuálně podporována <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Šablony stylů XSLT, které využívají jakékoli metody definované s `params` – klíčové slovo nebude pracovat správně. Podrobnosti najdete v tématu [parametry](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Chcete-li použít objekt XSLT rozšíření  
  
1.  Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.  
  
2.  Volání objektu rozšíření z této šablony.  
  
3.  Předat <xref:System.Xml.Xsl.XsltArgumentList> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
