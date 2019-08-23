---
title: Aspekty zabezpečení XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cf4a38ed08e0c569df62778c2ff80323ef261
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910492"
---
# <a name="xslt-security-considerations"></a>Aspekty zabezpečení XSLT
Jazyk XSLT nabízí bohatou sadu funkcí, které vám poskytnou skvělé možnosti výkonu a flexibility. Obsahuje mnoho funkcí, které jsou sice užitečné, ale můžou je využívat i mimo jiné zdroje. Aby bylo možné používat soubor XSLT bezpečně, je nutné pochopit typy problémů zabezpečení, ke kterým dochází při použití XSLT, a základní strategie, které můžete využít ke zmírnění těchto rizik.  
  
## <a name="xslt-extensions"></a>Rozšíření XSLT  
 Dvě oblíbená rozšíření XSLT jsou skripty a objekty rozšíření v šabloně stylů. Tato rozšíření umožňují procesoru XSLT spustit kód.  
  
- Objekty rozšíření přidávají možnosti programování do transformací XSL.  
  
- Skripty mohou být vloženy do předlohy se styly pomocí `msxsl:script` elementu rozšíření.  
  
### <a name="extension-objects"></a>Objekty rozšíření  
 Objekty rozšíření jsou přidány pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Sada oprávnění FullTrust je nutná k podpoře objektů rozšíření. Tím je zajištěno, že zvýšení oprávnění neproběhne, když je spuštěn kód objektu rozšíření. Pokus o volání <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez oprávnění FullTrust má za následek vyvolanou výjimku zabezpečení.  
  
### <a name="style-sheet-scripts"></a>Skripty šablon stylů  
 Skripty mohou být vloženy do šablon stylů pomocí `msxsl:script` elementu rozšíření. Podpora skriptů je volitelná funkce pro <xref:System.Xml.Xsl.XslCompiledTransform> třídu, která je ve výchozím nastavení zakázaná. Skriptování <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> lze povolit nastavením vlastnosti na `true` a <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> předání <xref:System.Xml.Xsl.XsltSettings> objektu metodě.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolit skriptování pouze v případě, že šablona stylů pochází z důvěryhodného zdroje. Pokud nemůžete ověřit zdroj šablony stylů nebo pokud šablona stylů nepochází z důvěryhodného zdroje, předejte `null` argument nastavení XSLT.  
  
## <a name="external-resources"></a>Externí zdroje  
 Jazyk XSLT obsahuje funkce, jako `xsl:import`například, `xsl:include`nebo `document()` funkce, kde procesor potřebuje přeložit odkazy identifikátoru URI. <xref:System.Xml.XmlResolver> Třída se používá k překladu externích prostředků. Externí prostředky může být potřeba vyřešit v následujících dvou případech:  
  
- Při kompilování předlohy <xref:System.Xml.XmlResolver> se styly se používá pro `xsl:import` a `xsl:include` rozlišení.  
  
- Při provádění transformace <xref:System.Xml.XmlResolver> se používá k `document()` vyřešení funkce.  
  
    > [!NOTE]
    > Funkce je ve výchozím nastavení zakázána <xref:System.Xml.Xsl.XslCompiledTransform> u třídy. `document()` Tuto funkci <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> lze povolit nastavením vlastnosti na `true` a <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> předání <xref:System.Xml.Xsl.XsltSettings> objektu metodě.  
  
 Jednotlivé metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> azahrnují<xref:System.Xml.XmlResolver> přetížení, která přijímají jako jeden z argumentů. <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Pokud není zadaný, použije se výchozí nastavení <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů. <xref:System.Xml.XmlResolver>  
  
#### <a name="guidelines"></a>Pokyny  
 `document()` Funkci povolte pouze v případě, že šablona stylů pochází z důvěryhodného zdroje.  
  
 Následující seznam popisuje, kdy možná budete chtít zadat <xref:System.Xml.XmlResolver> objekt:  
  
- Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.  
  
- Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění. Třídu použijte <xref:System.Xml.XmlSecureResolver> v případě, že potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.  
  
- Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídu a použít ji k řešení prostředků.  
  
- Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete `null` <xref:System.Xml.XmlResolver> pro argument zadat.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)
