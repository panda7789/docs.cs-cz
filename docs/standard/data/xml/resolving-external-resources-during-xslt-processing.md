---
title: "Řešení externím prostředkům během zpracování XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2bb115e14f8ff5d1065d87335d4d9021bd32ddd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Řešení externím prostředkům během zpracování XSLT
Existují několikrát během transformace XSLT, kdy budete muset vyřešit externím prostředkům.  
  
## <a name="using-the-xmlresolver-class"></a>Používání třídy objekt XmlResolver  
 <xref:System.Xml.XmlResolver> Třída se používá k překladu externím prostředkům. Následující tabulka popisuje, kdy <xref:System.Xml.XmlResolver> spojené se stane při zpracování XSLT.  
  
|Úloha XSLT|Co objekt XmlResolver se používá pro|  
|---------------|--------------------------------------|  
|Zkompilujte šablony stylů.|Vyřešte identifikátor URI šablony stylů.<br /><br /> - a -<br /><br /> Vyřešit odkazy na URI v žádném `xsl:import` nebo `xsl:include` elementy.|  
|Spusťte šablony stylů.|Identifikátor URI dokumentu kontextu přeložit.<br /><br /> - a -<br /><br /> Vyřešit odkazy na URI ve všech XSLT `document()` funkce.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody patří přetížení, které provést <xref:System.Xml.XmlResolver> objektu jako jeden z jeho argumenty. Pokud <xref:System.Xml.XmlResolver> není určena, výchozí <xref:System.Xml.XmlUrlResolver> bez pověření se používá.  
  
 Následující seznam popisuje, pokud chcete zadat <xref:System.Xml.XmlResolver> objektu:  
  
-   Pokud proces XSLT potřebuje pro přístup k prostředkům sítě, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebná pověření.  
  
-   Pokud chcete omezit prostředky, ke kterým mají přístup proces XSLT, můžete použít <xref:System.Xml.XmlSecureResolver> s oprávněním správné nastavení. Použití <xref:System.Xml.XmlSecureResolver> třídy, pokud je třeba otevřít prostředek není řídíte, nebo které není důvěryhodný.  
  
-   Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídy a použít ho k vyřešení prostředky.  
  
-   Pokud chcete zajistit, že žádné externí prostředky ke kterým se přistupuje, můžete zadat `null` pro <xref:System.Xml.XmlResolver> argument.  
  
## <a name="example"></a>Příklad  
 Následující příklad zkompiluje stylů, která je uložena na síťovém prostředku. <xref:System.Xml.XmlUrlResolver> Objektu určuje přihlašovací údaje potřebné pro přístup k šabloně stylů.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
