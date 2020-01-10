---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710333"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="3ae8e-102">Odebrání obsahu uzlu v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3ae8e-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="3ae8e-103">U typů uzlů, které dědí z <xref:System.Xml.XmlCharacterData>typy uzlů <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>a <xref:System.Xml.XmlSignificantWhitespace> můžete odebrat znaky pomocí metody <xref:System.Xml.XmlCharacterData.DeleteData%2A>, která odebere rozsah znaků z uzlu.</span><span class="sxs-lookup"><span data-stu-id="3ae8e-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="3ae8e-104">Pokud chcete zcela odebrat obsah, odeberte uzel obsahující obsah.</span><span class="sxs-lookup"><span data-stu-id="3ae8e-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="3ae8e-105">Pokud chcete zachovat uzel, ale obsah není správný, upravte obsah.</span><span class="sxs-lookup"><span data-stu-id="3ae8e-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="3ae8e-106">Informace o úpravách obsahu uzlu naleznete [v tématu Úprava uzlů, obsahu a hodnot v dokumentu XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="3ae8e-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae8e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ae8e-107">See also</span></span>

- [<span data-ttu-id="3ae8e-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3ae8e-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
