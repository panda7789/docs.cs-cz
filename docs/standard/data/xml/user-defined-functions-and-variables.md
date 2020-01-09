---
title: Uživatelem definované funkce a proměnné
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: 7040c2ccf6e3bfc6efcbec3505c633c6c3c6508f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710060"
---
# <a name="user-defined-functions-and-variables"></a>Uživatelem definované funkce a proměnné
Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k interakci s daty <xref:System.Xml.XPath.XPathDocument>. Standardní funkce XPath můžete doplnit implementací funkcí rozšíření a proměnných pro použití ve výrazech dotazů XPath. Metoda <xref:System.Xml.XPath.XPathExpression.SetContext%2A> může přijmout uživatelsky definovaný kontext odvozený od <xref:System.Xml.Xsl.XsltContext>. Uživatelsky definované funkce jsou vyřešeny vlastním kontextem.  
  
 Funkce a proměnné rozšíření mohou být užitečné při prevenci útoků injektáže XML. V těchto scénářích je uživatelský vstup přiřazen k vlastním proměnným a zpracován funkcí rozšíření, nikoli jako nezpracovaný vstup zřetězený s pokyny pro zpracování. Funkce rozšíření a proměnné obsahují uživatelský vstup, takže fungují pouze na datech XML, která jsou určena návrhářem.  
  
 Chcete-li použít rozšíření, implementujte vlastní třídu <xref:System.Xml.Xsl.XsltContext> spolu s rozhraními <xref:System.Xml.Xsl.IXsltContextFunction> a <xref:System.Xml.Xsl.IXsltContextVariable>, které podporují funkce a proměnné rozšíření. <xref:System.Xml.XPath.XPathExpression> přidá vstup uživatele s jeho <xref:System.Xml.Xsl.XsltArgumentList> do vlastního <xref:System.Xml.Xsl.XsltContext>.  
  
 <xref:System.Xml.XPath.XPathExpression> představuje kompilovaný dotaz, který <xref:System.Xml.XPath.XPathNavigator> používá k vyhledání a zpracování uzlů identifikovaných výrazem.  
  
 Následující příklad ukazuje implementaci třídy vlastního kontextu odvozenou z <xref:System.Xml.Xsl.XsltContext>. Komentáře v kódu popisují členy třídy a jejich použití ve vlastních funkcích. Implementace funkcí a proměnných a ukázková aplikace, která používá tyto implementace, se řídí tímto segmentem kódu.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextFunction>. Třída, která implementuje <xref:System.Xml.Xsl.IXsltContextFunction> řeší a provádí uživatelsky definované funkce. Tento příklad používá funkci identifikovanou deklarací: `private int CountChar(string title, char charTocount)`.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Následující kód implementuje <xref:System.Xml.Xsl.IXsltContextVariable>. Tato třída překládá odkazy na uživatelsky definované proměnné ve výrazech dotazů XPath za běhu. Instance této třídy je vytvořena a vrácena přepsanou metodou <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> třídy Custom <xref:System.Xml.Xsl.XsltContext>.  
  
 Komentáře kódu popisují členy třídy.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 S definicemi předchozí třídy v oboru používá následující kód vlastní funkci pro počítání znaků v prvcích `Tasks.xml` dokumentu. Komentáře v kódu popisují kód, který zkompiluje vlastní funkci a spustí jej v dokumentu `Tasks.xml`.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Tento příklad používá následující data XML.  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
