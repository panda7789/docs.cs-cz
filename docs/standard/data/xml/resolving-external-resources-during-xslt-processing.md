---
title: Překlad externích prostředků během zpracování XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710281"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Překlad externích prostředků během zpracování XSLT
V případě transformace XSLT může být několikrát nutné přeložit externí prostředky.  
  
## <a name="using-the-xmlresolver-class"></a>Použití třídy objekt XmlResolver  
 Třída <xref:System.Xml.XmlResolver> slouží k překladu externích prostředků. Následující tabulka popisuje, kdy se <xref:System.Xml.XmlResolver> během zpracování XSLT zapojí.  
  
|Úloha XSLT|K čemu se objekt XmlResolver používá|  
|---------------|--------------------------------------|  
|Zkompilujte šablonu stylů.|Vyřešte identifikátor URI pro šablonu stylů.<br /><br /> \- a -<br /><br /> Přeložit odkazy identifikátoru URI v jakémkoli `xsl:import` nebo `xsl:include` prvky.|  
|Spusťte šablonu stylů.|Vyřešte identifikátor URI kontextu dokumentu.<br /><br /> \- a -<br /><br /> Přeloží odkazy identifikátoru URI v jakýchkoli funkcích XSLT `document()`.|  
  
 Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zahrnují přetížení, která přebírají objekt <xref:System.Xml.XmlResolver> jako jeden z jeho argumentů. Pokud není zadaný <xref:System.Xml.XmlResolver>, použije se výchozí <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.  
  
 Následující seznam popisuje, kdy možná budete chtít zadat objekt <xref:System.Xml.XmlResolver>:  
  
- Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.  
  
- Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění. Třídu <xref:System.Xml.XmlSecureResolver> použijte v případě, že potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.  
  
- Pokud chcete přizpůsobit chování, můžete implementovat vlastní třídu <xref:System.Xml.XmlResolver> a použít ji k řešení prostředků.  
  
- Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete pro argument <xref:System.Xml.XmlResolver> zadat `null`.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje šablonu stylů uloženou v síťovém prostředku. Objekt <xref:System.Xml.XmlUrlResolver> Určuje pověření nutná pro přístup k šabloně stylů.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
