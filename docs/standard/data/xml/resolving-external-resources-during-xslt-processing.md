---
title: Překlad externích prostředků během zpracování XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 958699b8e3a00cfe3f8fd8ac4bb96914dcd0598c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137587"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Překlad externích prostředků během zpracování XSLT
Existují několikrát během transformace XSLT, kdy budete muset vyřešit externím prostředkům.  
  
## <a name="using-the-xmlresolver-class"></a>Pomocí třídy objekt XmlResolver  
 <xref:System.Xml.XmlResolver> Třída se používá k překladu externích prostředků. Následující tabulka popisuje, kdy <xref:System.Xml.XmlResolver> stane používané během zpracování XSLT.  
  
|Úloha XSLT|Co objekt XmlResolver slouží|  
|---------------|--------------------------------------|  
|Zkompilujte šablony stylů.|Rozpoznat identifikátor URI šablony stylů.<br /><br /> - a -<br /><br /> Identifikátor URI odkazy v libovolném `xsl:import` nebo `xsl:include` elementy.|  
|Spuštění šablony stylů.|Identifikátor URI dokumentu kontextu přeložit.<br /><br /> - a -<br /><br /> Identifikátor URI odkazy v jakékoli XSLT `document()` funkce.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody přetížení, která přijímají patří <xref:System.Xml.XmlResolver> objektu jako jeden z jejích argumentů. Pokud <xref:System.Xml.XmlResolver> nezadá, výchozí <xref:System.Xml.XmlUrlResolver> se používá bez pověření.  
  
 Následující seznam popisuje, kdy je vhodné zadat <xref:System.Xml.XmlResolver> objektu:  
  
-   Pokud XSLT procesu potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebné přihlašovací údaje.  
  
-   Pokud chcete omezit prostředky, které můžete přistupovat k procesu XSLT, můžete použít <xref:System.Xml.XmlSecureResolver> nastavte správné oprávnění. Použití <xref:System.Xml.XmlSecureResolver> třídy, pokud je potřeba otevřít prostředek, který není pod kontrolou, nebo, který není důvěryhodný.  
  
-   Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídy a použít ho k vyřešení zdroje.  
  
-   Pokud chcete zajistit, že jsou přístupné žádné externí prostředky, můžete zadat `null` pro <xref:System.Xml.XmlResolver> argument.  
  
## <a name="example"></a>Příklad  
 Následující příklad se zkompiluje šablony stylů, která je uložená na síťovém prostředku. <xref:System.Xml.XmlUrlResolver> Objekt Určuje přihlašovací údaje potřebné pro přístup k šabloně stylů.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- <xref:System.Xml.Xsl.XsltSettings>  
- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
