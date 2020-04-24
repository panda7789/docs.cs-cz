---
title: Odebrání uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: a34b92abc59215c3cb2b94afd88e2e30405b4e9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710307"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="58039-102">Odebrání uzlů z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="58039-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="58039-103">Chcete-li odebrat uzel z XML model DOM (Document Object Model) (DOM), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metodu pro odebrání konkrétního uzlu.</span><span class="sxs-lookup"><span data-stu-id="58039-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="58039-104">Když odeberete uzel, metoda odstraní podstrom patřící k odebíranému uzlu. To znamená, že pokud se nejedná o uzel typu list.</span><span class="sxs-lookup"><span data-stu-id="58039-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="58039-105">Chcete-li odebrat více uzlů z modelu DOM, <xref:System.Xml.XmlNode.RemoveAll%2A> použijte metodu k odebrání všech podřízených objektů a atributů (Pokud je k dispozici) aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="58039-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="58039-106">Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete uzel odebrat pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58039-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="58039-107">Chcete-li odebrat atributy, přečtěte si téma [Odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="58039-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58039-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="58039-108">See also</span></span>

- [<span data-ttu-id="58039-109">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="58039-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
