---
title: "Prázdné znaky a mezer významné zpracování při načítání modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="1ca35-102">Prázdné znaky a mezer významné zpracování při načítání modelu DOM</span><span class="sxs-lookup"><span data-stu-id="1ca35-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="1ca35-103">Při načítání dokumentu, můžete nastavit možnost zachování mezer a vytvořit **XmlWhitespace** uzly ve stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1ca35-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="1ca35-104">Chcete-li vytvořit mezer uzly, nastavte **PreserveWhitespace** vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="1ca35-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="1ca35-105">Pokud je nastavena na **false**, který je výchozí, nejsou vytvořeny uzly mezer.</span><span class="sxs-lookup"><span data-stu-id="1ca35-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="1ca35-106">Uzly významné prázdné znaky se vždycky zachovají, a **XmlSignificantWhitespace** uzly jsou vždy vytvořené v paměti představují tato data, bez ohledu na to, že v nastavení **PreserveWhitespace** příznak.</span><span class="sxs-lookup"><span data-stu-id="1ca35-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="1ca35-107">Pokud dokument je načtena z čtečka čipových karet, potom nastavení z **PreserveWhitespace** příznak vlastnost na **třídou XMLDocument nastavenou na** třída má vliv na vytváření **XmlWhitespace** uzly pouze tehdy, když **WhitespaceHandling** vlastnost **XmlTextReader** není nastavený na **: WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="1ca35-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="1ca35-108">Je hodnota **WhitespaceHandling** vlastnost čtecímu modulu, který má přednost před nastavením tohoto příznaku na **třídou XMLDocument nastavenou na**.</span><span class="sxs-lookup"><span data-stu-id="1ca35-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="1ca35-109">Další informace o **XmlSignificantWhitespace**, najdete v části <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="1ca35-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca35-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ca35-110">See Also</span></span>  
 [<span data-ttu-id="1ca35-111">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="1ca35-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
