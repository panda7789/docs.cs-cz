---
title: Odebrání uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46576558"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="2275a-102">Odebrání uzlů z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="2275a-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="2275a-103">Chcete-li odebrat uzel z XML Document Object Model (DOM), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metoda odebrání určitého uzlu.</span><span class="sxs-lookup"><span data-stu-id="2275a-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="2275a-104">Při odebírání uzlu metodu odebere podstrom, které patří k uzlu odebírá; To znamená pokud není uzel typu list.</span><span class="sxs-lookup"><span data-stu-id="2275a-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="2275a-105">Chcete-li odebrat více uzlů z modelu DOM, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metoda odebrat všechny podřízené prvky a atributy, pokud je k dispozici pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="2275a-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="2275a-106">Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete odebrat uzel pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2275a-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="2275a-107">Chcete-li odebrat atributy, naleznete v tématu [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="2275a-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2275a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2275a-108">See also</span></span>

- [<span data-ttu-id="2275a-109">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="2275a-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
