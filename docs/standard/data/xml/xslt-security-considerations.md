---
title: Aspekty zabezpečení XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 526805dff9fc59ed317a38b2512c8a97a711227a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661734"
---
# <a name="xslt-security-considerations"></a>Aspekty zabezpečení XSLT
Jazyka XSLT obsahuje bohatou sadu funkcí, které vám poskytnou spoustu výkon a flexibilitu. Obsahuje řadu funkcí, které sice užitečná, může také zneužít vnějšího zdroje. Pokud chcete bezpečně používat XSLT, musí porozumět typům problémy se zabezpečením, které vznikají při použití XSLT a základní strategie, které můžete použít pokud chcete toto riziko omezit.  
  
## <a name="xslt-extensions"></a>Rozšíření XSLT  
 Dvě oblíbené rozšíření XSLT jsou objekty, skriptování a rozšíření list stylu. Tato rozšíření umožňují spouštět kód procesoru XSLT.  
  
-   Objekty rozšíření přidat možnosti programování na transformace XSL.  
  
-   Skripty můžete vložit pomocí list stylu `msxsl:script` element rozšíření.  
  
### <a name="extension-objects"></a>Rozšíření objektů  
 Rozšíření objekty jsou přidány pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Sada oprávnění FullTrust nutný k podpoře objektů rozšíření. Tím se zajistí, že zvýšení úrovně oprávnění neproběhne ani při spuštění rozšíření objektového kódu. Pokus o volání <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez oprávnění FullTrust za následek vyvolané výjimce zabezpečení.  
  
### <a name="style-sheet-scripts"></a>Styl listu skriptů  
 Skripty můžete vložit pomocí list stylu `msxsl:script` element rozšíření. Skript podpory je volitelná funkce na <xref:System.Xml.Xsl.XslCompiledTransform> třídu, která je ve výchozím nastavení zakázané. Skriptování, můžete jej povolit nastavením <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> vlastnost `true` a předání <xref:System.Xml.Xsl.XsltSettings> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolte skriptování, pouze když stylů pochází z důvěryhodného zdroje. Pokud nemůžete ověřit zdroj šablony stylů nebo šablony stylů nepochází z důvěryhodného zdroje, předejte `null` argument nastavení XSLT.  
  
## <a name="external-resources"></a>Externí zdroje  
 Jazyka XSLT, jako má funkce `xsl:import`, `xsl:include`, nebo `document()` funkce, kde je potřeba vyřešit identifikátor URI odkazy procesoru. <xref:System.Xml.XmlResolver> Třída se používá k překladu externích prostředků. Externí prostředky může být potřeba vyřešit v těchto dvou případů:  
  
-   Při kompilaci šablony stylů, <xref:System.Xml.XmlResolver> se používá pro `xsl:import` a `xsl:include` řešení.  
  
-   Při provádění transformace <xref:System.Xml.XmlResolver> se používá k překladu `document()` funkce.  
  
    > [!NOTE]
    >  `document()` Funkce je ve výchozím nastavení zakázán na <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Tuto funkci je možné povolit nastavením <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> vlastnost `true` a předání <xref:System.Xml.Xsl.XsltSettings> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody každý patří přetížení <xref:System.Xml.XmlResolver> jako jeden z jejích argumentů. Pokud <xref:System.Xml.XmlResolver> nezadá, výchozí <xref:System.Xml.XmlUrlResolver> se používá bez pověření.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolit `document()` fungovat pouze v případě, že šablony stylů pochází z důvěryhodného zdroje.  
  
 Následující seznam popisuje, kdy je vhodné zadat <xref:System.Xml.XmlResolver> objektu:  
  
-   Pokud XSLT procesu potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebné přihlašovací údaje.  
  
-   Pokud chcete omezit prostředky, které můžete přistupovat k procesu XSLT, můžete použít <xref:System.Xml.XmlSecureResolver> nastavte správné oprávnění. Použití <xref:System.Xml.XmlSecureResolver> třídy, pokud je potřeba otevřít prostředek, který není pod kontrolou, nebo, který není důvěryhodný.  
  
-   Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídy a použít ho k vyřešení zdroje.  
  
-   Pokud chcete zajistit, že jsou přístupné žádné externí prostředky, můžete zadat `null` pro <xref:System.Xml.XmlResolver> argument.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)
