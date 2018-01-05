---
title: "Úpravy pomocí objektem XPathNavigator nastaveným na Data XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a967ee63a5ae9e9cc3abc5250af40ea7ba836a07
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="bfc83-102">Úpravy pomocí objektem XPathNavigator nastaveným na Data XML</span><span class="sxs-lookup"><span data-stu-id="bfc83-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="bfc83-103"><xref:System.Xml.XPath.XPathNavigator> Třída poskytuje metody pro vložení, upravovat a odebírat uzly a hodnoty z dokumentu XML obsažených v <xref:System.Xml.XmlDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="bfc83-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="bfc83-104">Chcete-li používat některé z těchto metod vložit, upravovat a odebírat uzly a hodnoty, <xref:System.Xml.XPath.XPathNavigator> objekt musí být upravitelné, který je jeho <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> vlastnosti musí mít hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="bfc83-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfc83-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bfc83-105">In This Section</span></span>  
 [<span data-ttu-id="bfc83-106">Vložení dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bfc83-107">Popisuje postup vložení na stejné úrovni, podřízený, atribut uzly a hodnoty pro <xref:System.Xml.XmlDocument> pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfc83-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="bfc83-108">Změna dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bfc83-109">Popisuje postup úpravy uzlů a hodnoty v <xref:System.Xml.XmlDocument> pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfc83-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="bfc83-110">Odebrání dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bfc83-111">Popisuje, jak odebrat uzly a hodnoty ze <xref:System.Xml.XmlDocument> pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfc83-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc83-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfc83-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="bfc83-113">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="bfc83-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="bfc83-114">Načítání dat XML pomocí XPathDocument a XmlDocument</span><span class="sxs-lookup"><span data-stu-id="bfc83-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="bfc83-115">Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="bfc83-116">Přístup k datům XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="bfc83-117">Ověření schématu pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="bfc83-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
