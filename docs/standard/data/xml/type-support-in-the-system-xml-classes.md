---
title: Podpora typu v třídách System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026884"
---
# <a name="type-support-in-the-systemxml-classes"></a>Podpora typu v třídách System.Xml
V rozhraní .NET Framework verze 2.0 mají základní třídy XML vylepšené a zahrnují typ funkce podpory. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, A <xref:System.Xml.XPath.XPathNavigator> třídy zahrnují funkce podpory typu, včetně možnosti pro převod mezi typy schémat XML a běžné language runtime (CLR) typy.  
  
 V rozhraní .NET Framework verze 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, a <xref:System.Xml.XPath.XPathNavigator> třídy vylepšené a zahrnují typ funkce podpory.  
  
- <xref:System.Xml.XmlReader> a <xref:System.Xml.XPath.XPathNavigator> třídy každý zahrnují **položka SchemaInfo** vlastnost, která vrátí informace o schématu na uzlu.  
  
- **ReadContentAs** a **ReadElementContentAs** a metody <xref:System.Xml.XmlReader> třídy číst textové hodnoty a převeďte jej na hodnotu CLR v rámci jednoho volání metody.  
  
- <xref:System.Xml.XmlWriter.WriteValue%2A> Metodu <xref:System.Xml.XmlWriter> třídy při výpisu XML převádí typ CLR na typ schématu XML.  
  
- **ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> vlastnosti <xref:System.Xml.XPath.XPathNavigator> třídy vrátit hodnotu uzlu a převeďte jej na hodnotu CLR v rámci jednoho volání metody.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0 <xref:System.Xml.XmlConvert> třídy byly potřebné pro převod mezi typy schématu XML a CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Popisuje výchozí mapování datových typů XML na typy CLR.  
  
 [Poznámky k implementaci podpory typů XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Tento článek popisuje některé podrobnosti o podpoře implementace typu.  
  
 [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Popisuje způsob použití <xref:System.Xml.XmlConvert> pro převod mezi typy schématu XML a CLR.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
