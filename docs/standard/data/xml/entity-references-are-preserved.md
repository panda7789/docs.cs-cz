---
title: Odkazy na entity se zachovají.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 652a044bf1b5293bc9c36477a46a78d9851f1810
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568482"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="e30b0-102">Odkazy na entity se zachovají.</span><span class="sxs-lookup"><span data-stu-id="e30b0-102">Entity References are Preserved</span></span>
<span data-ttu-id="e30b0-103">Pokud není odkaz na entitu rozšířit, ale je zachovaná, sestavení XML modelu DOM (Document Object) **XmlEntityReference** uzlu, pokud se setká s odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="e30b0-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="e30b0-104">Pomocí následující kód XML</span><span class="sxs-lookup"><span data-stu-id="e30b0-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="e30b0-105">sestavení modelu DOM **XmlEntityReference** uzlu, když narazí `&publisher;` odkaz.</span><span class="sxs-lookup"><span data-stu-id="e30b0-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="e30b0-106">**XmlEntityReference** obsahuje podřízené uzly zkopírovat z obsahu v deklaraci entity.</span><span class="sxs-lookup"><span data-stu-id="e30b0-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="e30b0-107">V předchozím příkladu kódu obsahuje text v deklaraci entity, takže **XmlText** uzlu je vytvořen jako podřízený uzel entity uzlu odkazu.</span><span class="sxs-lookup"><span data-stu-id="e30b0-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="e30b0-108">![Stromové struktury pro odkazy na zachované entity](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="e30b0-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="e30b0-109">Stromovou strukturu pro odkazy na entity, které se zachovají</span><span class="sxs-lookup"><span data-stu-id="e30b0-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="e30b0-110">Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořené z **XmlEntity** uzlu deklarace entity došlo.</span><span class="sxs-lookup"><span data-stu-id="e30b0-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e30b0-111">Uzly zkopírovaných z **XmlEntity** nejsou vždy přesné kopie jednou umístěn v uzlu odkazu entity.</span><span class="sxs-lookup"><span data-stu-id="e30b0-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="e30b0-112">Může být obory názvů, které jsou v oboru v uzlu odkazu entity a která ovlivňuje finální konfiguraci podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="e30b0-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="e30b0-113">Ve výchozím nastavení, jako například obecné entity `&abc;` zachovány a **XmlEntityReference** uzlů vždy vytvořené.</span><span class="sxs-lookup"><span data-stu-id="e30b0-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30b0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e30b0-114">See Also</span></span>  
 [<span data-ttu-id="e30b0-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="e30b0-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
