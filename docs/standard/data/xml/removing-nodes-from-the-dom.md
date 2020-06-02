---
title: Odebrání uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5df95700bb1e84aa5f3adcc752b2314dc964477b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288638"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="ce5ad-102">Odebrání uzlů z modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ce5ad-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="ce5ad-103">Chcete-li odebrat uzel z XML model DOM (Document Object Model) (DOM), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metodu pro odebrání konkrétního uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="ce5ad-104">Když odeberete uzel, metoda odstraní podstrom patřící k odebíranému uzlu. To znamená, že pokud se nejedná o uzel typu list.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="ce5ad-105">Chcete-li odebrat více uzlů z modelu DOM, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metodu k odebrání všech podřízených objektů a atributů (Pokud je k dispozici) aktuálního uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="ce5ad-106">Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap> , můžete uzel odebrat pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ce5ad-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="ce5ad-107">Chcete-li odebrat atributy, přečtěte si téma [Odebrání atributů z uzlu elementu v modelu DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="ce5ad-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5ad-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce5ad-108">See also</span></span>

- [<span data-ttu-id="ce5ad-109">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ce5ad-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
