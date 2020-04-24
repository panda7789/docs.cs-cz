---
title: Zpracování mezer a významných mezer při načítání modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 834644a07d790401a1131d6d901f144ef90dc495
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710021"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="f375d-102">Zpracování mezer a významných mezer při načítání modelu DOM</span><span class="sxs-lookup"><span data-stu-id="f375d-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="f375d-103">Při načítání dokumentu můžete nastavit možnost zachovat prázdné znaky a vytvořit uzly **XmlWhitespace** ve stromu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f375d-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="f375d-104">Chcete-li vytvořit uzly s prázdným znakem, nastavte vlastnost **PreserveWhitespace** na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="f375d-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="f375d-105">Pokud je vlastnost nastavena na **hodnotu false**, což je výchozí nastavení, nevytvoří se uzly s prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="f375d-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="f375d-106">Významné uzly s bílým prostorem jsou vždy zachovány a uzly **XmlSignificantWhitespace** jsou vždy vytvořeny v paměti, aby představovaly tato data, a to bez ohledu na nastavení příznaku **PreserveWhitespace** .</span><span class="sxs-lookup"><span data-stu-id="f375d-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="f375d-107">Pokud je dokument načten z čtecího modulu, nastavení vlastnosti příznak **PreserveWhitespace** třídy **XmlDocument** má vliv na vytváření uzlů **XmlWhitespace** pouze v případě, že vlastnost **WhitespaceHandling** ve třídě **XmlTextReader** není nastavena na **WhitespaceHandling. None**.</span><span class="sxs-lookup"><span data-stu-id="f375d-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="f375d-108">Jedná se o hodnotu vlastnosti **WhitespaceHandling** ve čtečce, která má přednost před nastavením tohoto příznaku v **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="f375d-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="f375d-109">Další informace o **XmlSignificantWhitespace**naleznete v tématu <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="f375d-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f375d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f375d-110">See also</span></span>

- [<span data-ttu-id="f375d-111">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f375d-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
