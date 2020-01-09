---
title: Podpora typu v třídách System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710099"
---
# <a name="type-support-in-the-systemxml-classes"></a>Podpora typu v třídách System.Xml
V .NET Framework verze 2,0 byly základní třídy XML vylepšeny, aby zahrnovaly funkce podpory typů. Třídy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.XPath.XPathNavigator> zahrnují funkce podpory typů včetně možnosti konverze mezi typy schémat XML a typy modulu CLR (Common Language Runtime).  
  
 V .NET Framework verze 2,0 byly vylepšeny třídy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>a <xref:System.Xml.XPath.XPathNavigator>, aby zahrnovaly funkce podpory typů.  
  
- Mezi třídy <xref:System.Xml.XmlReader> a <xref:System.Xml.XPath.XPathNavigator> patří vlastnost **SchemaInfo** , která vrací informace o schématu v uzlu.  
  
- **ReadContentAs** a **metody ReadElementContentAs** a metody třídy <xref:System.Xml.XmlReader> čtou textovou hodnotu a převedou je na hodnotu CLR v rámci jediné volání metody.  
  
- Metoda <xref:System.Xml.XmlWriter.WriteValue%2A> třídy <xref:System.Xml.XmlWriter> při zapisování XML převede typ CLR na typ schématu XML.  
  
- Vlastnosti **ValueAs** a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> třídy <xref:System.Xml.XPath.XPathNavigator> vracejí hodnotu uzlu a převedou je na hodnotu CLR v rámci jediného volání metody.  
  
> [!NOTE]
> Ve .NET Framework verze 1,0 byla <xref:System.Xml.XmlConvert> třída nutná k převodu mezi schématy XML a typy CLR.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování datových typů XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Popisuje výchozí mapování datových typů XML na typy CLR.  
  
 [Poznámky k implementaci podpory typů XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Popisuje některé podrobnosti implementace podpory typu.  
  
 [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Popisuje, jak použít třídu <xref:System.Xml.XmlConvert> k převedení mezi schématy XML a typy CLR.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
