---
title: "Odstranění uzlů z modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 866859ed1104d24c225d4daa3776548112417fde
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="36caf-102">Odstranění uzlů z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="36caf-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="36caf-103">Chcete-li odebrat uzel z XML modelu DOM (Document Object), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metoda odebrat konkrétní uzel.</span><span class="sxs-lookup"><span data-stu-id="36caf-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="36caf-104">Při odebrání uzlu metoda odebere podstrom, které patří k uzlu odebírána; To znamená pokud není uzlem typu list.</span><span class="sxs-lookup"><span data-stu-id="36caf-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="36caf-105">Pokud chcete odstranit z modelu DOM více uzlů, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metoda odebrat všechny podřízené objekty a atributy, pokud je k dispozici, aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="36caf-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="36caf-106">Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete odebrat uzel pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="36caf-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="36caf-107">Chcete-li odebrat atributy, přečtěte si téma [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="36caf-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36caf-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="36caf-108">See Also</span></span>  
 [<span data-ttu-id="36caf-109">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="36caf-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
