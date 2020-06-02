---
title: Odebrání obsahu uzlu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 02737c5b680321392d93d785b757c58f2b8da9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288651"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="69aeb-102">Odebrání obsahu uzlu v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="69aeb-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="69aeb-103">U typů uzlů, které dědí z <xref:System.Xml.XmlCharacterData> , což jsou <xref:System.Xml.XmlComment> <xref:System.Xml.XmlText> typy uzlů,, <xref:System.Xml.XmlCDataSection> , <xref:System.Xml.XmlWhitespace> a <xref:System.Xml.XmlSignificantWhitespace> , můžete odebrat znaky pomocí <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody, která odebere rozsah znaků z uzlu.</span><span class="sxs-lookup"><span data-stu-id="69aeb-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="69aeb-104">Pokud chcete zcela odebrat obsah, odeberte uzel obsahující obsah.</span><span class="sxs-lookup"><span data-stu-id="69aeb-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="69aeb-105">Pokud chcete zachovat uzel, ale obsah není správný, upravte obsah.</span><span class="sxs-lookup"><span data-stu-id="69aeb-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="69aeb-106">Informace o úpravách obsahu uzlu naleznete [v tématu Úprava uzlů, obsahu a hodnot v dokumentu XML](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="69aeb-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69aeb-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="69aeb-107">See also</span></span>

- [<span data-ttu-id="69aeb-108">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="69aeb-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
