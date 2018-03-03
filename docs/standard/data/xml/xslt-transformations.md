---
title: Transformace XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63c73fc48d0beaeb3a77acc464734b11410467a0
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="xslt-transformations"></a>Transformace XSLT
Šablony stylů transformace XSLT (Extensible Language) umožňuje transformace do jiného dokumentu, který se liší ve formátu nebo struktura obsah zdrojový dokument XML. Můžete například XSLT transformace XML do kódu HTML k použití na webu a transformují je na dokument, který obsahuje pouze pole, které jsou vyžadována danou aplikací. Tento proces transformace je zadána [doporučení W3C XSL transformace XSLT () verze 1.0](https://www.w3.org/TR/xslt-10/).  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesor XSLT v rozhraní .NET. <xref:System.Xml.Xsl.XslCompiledTransform> Třídy podporuje [doporučení W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework verze 2.0. <xref:System.Xml.Xsl.XslCompiledTransform> Třída je nové implementace modulu XSLT. Obsahuje vylepšení výkonu a nové funkce zabezpečení. Doporučený postup je vytvoření XSLT aplikací pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Poskytuje informace o používání <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 [Migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Popisuje, jak do migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy.  
  
 [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Poskytuje informace o používání kompilátoru XSLT.  
  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Poskytuje informace o používání <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](../../../../docs/standard/data/xml/index.md)
