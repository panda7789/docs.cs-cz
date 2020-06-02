---
title: Transformace XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 92d0af1519260d458d3954beaef38e698142367a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288300"
---
# <a name="xslt-transformations"></a>Transformace XSLT
Extensible Stylesheet Language Transformation (XSLT) umožňuje transformovat obsah zdrojového dokumentu XML do jiného dokumentu, který je ve formátu nebo struktuře jiný. Můžete například použít XSLT k transformaci XML do HTML pro použití na webu nebo k transformaci na dokument, který obsahuje pouze pole požadovaná aplikací. Tento proces transformace je určen [doporučením XSLT verze 1,0 W3C Transformers (XSLT)](https://www.w3.org/TR/xslt-10/).  
  
 <xref:System.Xml.Xsl.XslCompiledTransform>Třída je procesor XSLT v rozhraní .NET. <xref:System.Xml.Xsl.XslCompiledTransform>Třída podporuje [doporučení W3C XSLT 1,0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Třída je zastaralá ve verzi .NET Framework 2,0. <xref:System.Xml.Xsl.XslCompiledTransform>Třída je nová implementace modulu XSLT. Zahrnuje vylepšení výkonu a nové funkce zabezpečení. Doporučeným postupem je vytvoření aplikací XSLT pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md)  
 Poskytuje informace o použití <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 [Migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md)  
 Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.  
  
 [Kompilátor XSLT (xsltc.exe)](xslt-compiler-xsltc-exe.md)  
 Poskytuje informace o použití kompilátoru XSLT.  
  
 [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)  
 Poskytuje informace o použití <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Související oddíly  
 [Dokumenty a data XML](index.md)
