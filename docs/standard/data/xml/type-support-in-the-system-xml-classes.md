---
title: Podpora typu v System.Xml třídy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569691"
---
# <a name="type-support-in-the-systemxml-classes"></a>Podpora typu v System.Xml třídy
V rozhraní .NET Framework verze 2.0 mají základní třídy XML vylepšené a zahrnují typ podpory funkce. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, A <xref:System.Xml.XPath.XPathNavigator> třídy zahrnují typ podpory funkce, včetně možnosti pro převod mezi typy schémat XML a běžné typy language runtime (CLR).  
  
 V rozhraní .NET Framework verze 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.XPath.XPathNavigator> třídy vylepšené a zahrnují typ podpory funkce.  
  
-   <xref:System.Xml.XmlReader> a <xref:System.Xml.XPath.XPathNavigator> třídy každý zahrnují **SchemaInfo** vlastnost, která vrací informace o schématu na uzlu.  
  
-   **ReadContentAs** a **ReadElementContentAs** a metody na <xref:System.Xml.XmlReader> třídy číst textové hodnoty a převést na hodnotu CLR v rámci jednoho volání metody.  
  
-   <xref:System.Xml.XmlWriter.WriteValue%2A> Metodu <xref:System.Xml.XmlWriter> třída převede na typ CLR na typ schématu XML při zápisu se XML.  
  
-   **ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy vrátit hodnotu uzlu a převeďte ho na hodnotu CLR v rámci jednoho volání metody.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 <xref:System.Xml.XmlConvert> třídy byly potřebné pro převod mezi typy schématu XML a CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Popisuje výchozí mapování datových typů XML pro typy CLR.  
  
 [Poznámky k implementaci podpory typů XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Popisuje některé podrobnosti implementace podporu typu.  
  
 [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Popisuje postup použití <xref:System.Xml.XmlConvert> třídy pro převod mezi typy schématu XML a CLR.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
