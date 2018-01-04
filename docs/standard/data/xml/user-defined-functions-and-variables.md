---
title: "Uživatelem definované funkce a proměnné"
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
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6870861541a063c56f83dcb286d21a5a970d1b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="user-defined-functions-and-variables"></a>Uživatelem definované funkce a proměnné
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje sadu metod, které se používají k interakci s <xref:System.Xml.XPath.XPathDocument> data. Standardní funkce jazyka XPath lze rozšířit implementací rozšíření funkce a proměnné pro použití ve výrazech dotazů XPath. <xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metoda může přijmout odvozené z kontextu uživatelsky definované <xref:System.Xml.Xsl.XsltContext>. Uživatelem definované funkce se vyřeší kontext vlastní.  
  
 Rozšíření funkce a proměnné může být užitečné při prevenci útoků vkládání XML. Uživatelský vstup je v těchto scénářích přiřazené vlastní proměnné a zpracovává rozšíření funkce, nikoli jako nezpracovaná vstup zřetězen s pokynů pro zpracování. Rozšíření funkce a proměnné obsahovat uživatelský vstup, aby ho pouze funguje na XML data tak, jak má v designeru.  
  
 Pokud chcete rozšíření použít implementovat vlastní <xref:System.Xml.Xsl.XsltContext> třída společně s rozhraní <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable> podporující rozšíření funkce a proměnné. <xref:System.Xml.XPath.XPathExpression> Přidá vstup uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> na vlastní <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> Představuje kompilované dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracovat uzly identifikovaný výraz.  
  
 Následující příklad ukazuje implementaci vlastní kontextu třídy odvozené od <xref:System.Xml.Xsl.XsltContext>. Komentáře v kódu popisují členy třídy a jejich využití v vlastní funkce. Implementace funkce a proměnné a ukázkové aplikace, která používá tyto implementace postupujte podle tohoto segmentu kódu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Třídu, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> vyřeší a provede uživatelsky definované funkce. Tento příklad používá funkci identifikovaný deklaraci: `private int CountChar(string title, char charTocount)`.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Tato třída přeloží odkazy na uživatelem definované proměnné ve výrazech XPath dotazů za běhu. Instance této třídy je vytvořen a vrácený přepsané <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda vlastní <xref:System.Xml.Xsl.XsltContext> třídy.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Předchozí definicemi – třída v oboru, následující kód používá vlastní funkce pro počet znaků v elementech `Tasks.xml` dokumentu. Komentáře v kódu popisují kód, který sestavuje vlastní funkce a spouští se před `Tasks.xml` dokumentu.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Tento příklad používá následující data XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
