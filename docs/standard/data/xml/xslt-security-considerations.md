---
title: "Aspekty zabezpečení XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7388bbc388dd46a30486a2300150bc9d1566593e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-security-considerations"></a>Aspekty zabezpečení XSLT
Jazyk XSLT obsahuje bohatou sadu funkcí, které vám poskytnou značnou část výkon a flexibilitu. Obsahuje řadu funkcí, které sice užitečná, může také zneužít vnějšího zdroje. Abyste mohli bezpečně používat XSLT, musíte pochopit druhy problémy zabezpečení, které vznikají při použití XSLT a základní strategií, které můžete použít k toto riziko omezit.  
  
## <a name="xslt-extensions"></a>Rozšíření XSLT  
 Dvě oblíbených XSLT rozšíření jsou objekty skriptování a rozšíření list stylu. Tato rozšíření umožňují XSLT procesor pro spouštění kódu.  
  
-   Rozšíření objektů přidat programovací funkce XSL transformace.  
  
-   Skripty, lze jej vkládat do listu styl pomocí `msxsl:script` elementu rozšíření.  
  
### <a name="extension-objects"></a>Rozšíření objektů  
 Rozšíření objekty jsou přidány, pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda. Sada oprávnění FullTrust je vyžadovaný jako podpora objektů rozšíření. Tím se zajistí, že zvýšení úrovně oprávnění neodehrává při spuštění kódu objekt rozšíření. Probíhá pokus o volání <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda bez oprávnění FullTrust za následek výjimku zabezpečení hlášeny.  
  
### <a name="style-sheet-scripts"></a>Skripty list stylu  
 Skripty, lze jej vkládat do listu styl pomocí `msxsl:script` elementu rozšíření. Podpora skriptu je volitelná funkce v <xref:System.Xml.Xsl.XslCompiledTransform> třídu, která je ve výchozím nastavení zakázané. Může být povoleno skriptování nastavením <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> vlastnost `true` a předání <xref:System.Xml.Xsl.XsltSettings> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolte skriptování, pouze když šablony stylů pochází z důvěryhodného zdroje. Pokud nemůžete ověřit zdroj šablony stylů nebo šablony stylů nepochází z důvěryhodného zdroje, předejte `null` nastavení argumentu XSLT.  
  
## <a name="external-resources"></a>Externí zdroje  
 Jazyk XSLT je funkce, jako `xsl:import`, `xsl:include`, nebo `document()` funkce, kde je potřeba vyřešit URI odkazy na procesor. <xref:System.Xml.XmlResolver> Třída se používá k překladu externím prostředkům. Externí prostředky muset být vyřešen v těchto dvou případů:  
  
-   Při kompilaci šablony stylů <xref:System.Xml.XmlResolver> se používá pro `xsl:import` a `xsl:include` řešení.  
  
-   Při provádění transformace, <xref:System.Xml.XmlResolver> se používá k překladu `document()` funkce.  
  
    > [!NOTE]
    >  `document()` Funkce je ve výchozím nastavení zakázán na <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Tato funkce se dá nastavit podle nastavení <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> vlastnost `true` a předání <xref:System.Xml.Xsl.XsltSettings> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody každý patří přetížení, které přijímají <xref:System.Xml.XmlResolver> jako jeden z jeho argumenty. Pokud <xref:System.Xml.XmlResolver> není určena, výchozí <xref:System.Xml.XmlUrlResolver> bez pověření se používá.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolit `document()` fungovat pouze v případě, že šablony stylů pochází z důvěryhodného zdroje.  
  
 Následující seznam popisuje, pokud chcete zadat <xref:System.Xml.XmlResolver> objektu:  
  
-   Pokud proces XSLT potřebuje pro přístup k prostředkům sítě, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebná pověření.  
  
-   Pokud chcete omezit prostředky, ke kterým mají přístup proces XSLT, můžete použít <xref:System.Xml.XmlSecureResolver> s oprávněním správné nastavení. Použití <xref:System.Xml.XmlSecureResolver> třídy, pokud je třeba otevřít prostředek není řídíte, nebo které není důvěryhodný.  
  
-   Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídy a použít ho k vyřešení prostředky.  
  
-   Pokud chcete zajistit, že žádné externí prostředky ke kterým se přistupuje, můžete zadat `null` pro <xref:System.Xml.XmlResolver> argument.  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [Zabezpečení přístupu kódu](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
