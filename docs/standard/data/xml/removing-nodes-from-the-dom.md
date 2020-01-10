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
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="b99c7-102">Odebrání uzlů z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="b99c7-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="b99c7-103">Chcete-li odebrat uzel z XML model DOM (Document Object Model) (DOM), použijte metodu <xref:System.Xml.XmlNode.RemoveChild%2A> k odebrání konkrétního uzlu.</span><span class="sxs-lookup"><span data-stu-id="b99c7-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="b99c7-104">Když odeberete uzel, metoda odstraní podstrom patřící k odebíranému uzlu. To znamená, že pokud se nejedná o uzel typu list.</span><span class="sxs-lookup"><span data-stu-id="b99c7-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="b99c7-105">Chcete-li odebrat více uzlů z modelu DOM, použijte metodu <xref:System.Xml.XmlNode.RemoveAll%2A> k odebrání všech podřízených objektů a atributů, pokud jsou k dispozici pro aktuální uzel.</span><span class="sxs-lookup"><span data-stu-id="b99c7-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="b99c7-106">Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete uzel odebrat pomocí metody <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="b99c7-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="b99c7-107">Chcete-li odebrat atributy, přečtěte si téma [Odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b99c7-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99c7-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b99c7-108">See also</span></span>

- [<span data-ttu-id="b99c7-109">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b99c7-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
