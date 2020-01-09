---
title: Aspekty zabezpečení XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: e6e490c0f637aace57dacc88ef49cc9be87532cd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709683"
---
# <a name="xslt-security-considerations"></a>Aspekty zabezpečení XSLT
Jazyk XSLT nabízí bohatou sadu funkcí, které vám poskytnou skvělé možnosti výkonu a flexibility. Obsahuje mnoho funkcí, které jsou sice užitečné, ale můžou je využívat i mimo jiné zdroje. Aby bylo možné používat soubor XSLT bezpečně, je nutné pochopit typy problémů zabezpečení, ke kterým dochází při použití XSLT, a základní strategie, které můžete využít ke zmírnění těchto rizik.  
  
## <a name="xslt-extensions"></a>Rozšíření XSLT  
 Dvě oblíbená rozšíření XSLT jsou skripty a objekty rozšíření v šabloně stylů. Tato rozšíření umožňují procesoru XSLT spustit kód.  
  
- Objekty rozšíření přidávají možnosti programování do transformací XSL.  
  
- Skripty mohou být vloženy do předlohy se styly pomocí elementu `msxsl:script`ho rozšíření.  
  
### <a name="extension-objects"></a>Objekty rozšíření  
 Objekty rozšíření jsou přidány pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Sada oprávnění FullTrust je nutná k podpoře objektů rozšíření. Tím je zajištěno, že zvýšení oprávnění neproběhne, když je spuštěn kód objektu rozšíření. Pokus o volání metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> bez oprávnění FullTrust má za následek vyvolanou výjimku zabezpečení.  
  
### <a name="style-sheet-scripts"></a>Skripty šablon stylů  
 Skripty mohou být vloženy do předlohy se styly pomocí elementu `msxsl:script`ho rozšíření. Podpora skriptů je volitelná funkce <xref:System.Xml.Xsl.XslCompiledTransform> třídy, která je ve výchozím nastavení zakázána. Skriptování lze povolit nastavením vlastnosti <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> na `true` a předáním objektu <xref:System.Xml.Xsl.XsltSettings> metodě <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolit skriptování pouze v případě, že šablona stylů pochází z důvěryhodného zdroje. Pokud nemůžete ověřit zdroj šablony stylů nebo pokud šablona stylů nepochází z důvěryhodného zdroje, předejte `null` argumentu nastavení XSLT.  
  
## <a name="external-resources"></a>Externí prostředky  
 Jazyk XSLT obsahuje funkce, jako jsou `xsl:import`, `xsl:include`nebo funkce `document()`, kde procesor potřebuje přeložit odkazy identifikátoru URI. Třída <xref:System.Xml.XmlResolver> slouží k překladu externích prostředků. Externí prostředky může být potřeba vyřešit v následujících dvou případech:  
  
- Při kompilování předlohy se styly se <xref:System.Xml.XmlResolver> používá pro `xsl:import` a řešení `xsl:include`.  
  
- Při provádění transformace se používá <xref:System.Xml.XmlResolver> k vyřešení `document()` funkce.  
  
    > [!NOTE]
    > Funkce `document()` je ve výchozím nastavení pro třídu <xref:System.Xml.Xsl.XslCompiledTransform> zakázána. Tuto funkci můžete povolit nastavením vlastnosti <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> na `true` a předáním objektu <xref:System.Xml.Xsl.XsltSettings> metodě <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
 Každá z metod <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zahrnuje přetížení, která přijímají <xref:System.Xml.XmlResolver> jako jeden z jejích argumentů. Pokud není zadaný <xref:System.Xml.XmlResolver>, použije se výchozí <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.  
  
#### <a name="guidelines"></a>Pokyny  
 Funkci `document()` povolte pouze v případě, že šablona stylů pochází z důvěryhodného zdroje.  
  
 Následující seznam popisuje, kdy možná budete chtít zadat objekt <xref:System.Xml.XmlResolver>:  
  
- Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.  
  
- Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění. Třídu <xref:System.Xml.XmlSecureResolver> použijte v případě, že potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.  
  
- Pokud chcete přizpůsobit chování, můžete implementovat vlastní třídu <xref:System.Xml.XmlResolver> a použít ji k řešení prostředků.  
  
- Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete pro argument <xref:System.Xml.XmlResolver> zadat `null`.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Překlad externích prostředků během zpracování XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security.md)
