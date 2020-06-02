---
title: Aspekty zabezpečení XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: 81db764016607ebe6facfc530dbb2bac8e6b8cfe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282505"
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
 Skripty mohou být vloženy do šablon stylů pomocí `msxsl:script` elementu rozšíření. Podpora skriptů je volitelná funkce pro <xref:System.Xml.Xsl.XslCompiledTransform> třídu, která je ve výchozím nastavení zakázaná. Skriptování lze povolit nastavením <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> vlastnosti na `true` a předání <xref:System.Xml.Xsl.XsltSettings> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodě.  
  
#### <a name="guidelines"></a>Pokyny  
 Povolit skriptování pouze v případě, že šablona stylů pochází z důvěryhodného zdroje. Pokud nemůžete ověřit zdroj šablony stylů nebo pokud šablona stylů nepochází z důvěryhodného zdroje, předejte `null` argument nastavení XSLT.  
  
## <a name="external-resources"></a>Externí zdroje  
 Jazyk XSLT obsahuje funkce, jako například `xsl:import` , `xsl:include` nebo `document()` funkce, kde procesor potřebuje přeložit odkazy identifikátoru URI. <xref:System.Xml.XmlResolver>Třída se používá k překladu externích prostředků. Externí prostředky může být potřeba vyřešit v následujících dvou případech:  
  
- Při kompilování předlohy se styly <xref:System.Xml.XmlResolver> se používá pro `xsl:import` a `xsl:include` rozlišení.  
  
- Při provádění transformace <xref:System.Xml.XmlResolver> se používá k vyřešení `document()` funkce.  
  
    > [!NOTE]
    > `document()`Funkce je ve výchozím nastavení zakázána u <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Tuto funkci lze povolit nastavením <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> vlastnosti na `true` a předání <xref:System.Xml.Xsl.XsltSettings> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodě.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Jednotlivé metody a zahrnují přetížení, která přijímají <xref:System.Xml.XmlResolver> jako jeden z argumentů. Pokud <xref:System.Xml.XmlResolver> není zadaný, použije se výchozí nastavení <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.  
  
#### <a name="guidelines"></a>Pokyny  
 Funkci povolte `document()` pouze v případě, že šablona stylů pochází z důvěryhodného zdroje.  
  
 Následující seznam popisuje, kdy možná budete chtít zadat <xref:System.Xml.XmlResolver> objekt:  
  
- Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.  
  
- Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění. Třídu použijte v případě, že <xref:System.Xml.XmlSecureResolver> potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.  
  
- Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídu a použít ji k řešení prostředků.  
  
- Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete `null` pro <xref:System.Xml.XmlResolver> argument zadat.  
  
## <a name="see-also"></a>Viz také

- [Transformace XSLT](xslt-transformations.md)
- [Překlad externích prostředků během zpracování XSLT](resolving-external-resources-during-xslt-processing.md)
- [Zabezpečení přístupu kódu](../../../framework/misc/code-access-security.md)
