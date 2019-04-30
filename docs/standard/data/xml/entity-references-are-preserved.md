---
title: Odkazy na entity jsou zachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934525"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="b5665-102">Odkazy na entity jsou zachované</span><span class="sxs-lookup"><span data-stu-id="b5665-102">Entity References are Preserved</span></span>
<span data-ttu-id="b5665-103">Pokud odkaz na entitu není rozbalen, ale zachovají, sestavení XML Document Object Model (DOM) **XmlEntityReference** uzlu, pokud se setká s odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="b5665-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="b5665-104">Pomocí následující kód XML</span><span class="sxs-lookup"><span data-stu-id="b5665-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="b5665-105">sestavení modelu DOM **XmlEntityReference** uzlu, pokud se setká `&publisher;` odkaz.</span><span class="sxs-lookup"><span data-stu-id="b5665-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="b5665-106">**XmlEntityReference** obsahuje podřízené uzly, které jsou kopírovány z obsahu entity prohlášení.</span><span class="sxs-lookup"><span data-stu-id="b5665-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="b5665-107">Předchozí příklad kódu obsahuje text v entity prohlášení, takže **XmlText** uzel je vytvořen jako podřízený uzel uzlu odkazu entity.</span><span class="sxs-lookup"><span data-stu-id="b5665-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="b5665-108">![Stromová struktura pro odkazy na entity zachovaných](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="b5665-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="b5665-109">Stromovou strukturu pro odkazy na entity, které jsou zachovány</span><span class="sxs-lookup"><span data-stu-id="b5665-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="b5665-110">Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořené z **XmlEntity** uzlu, když došlo k deklaraci entity.</span><span class="sxs-lookup"><span data-stu-id="b5665-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5665-111">Uzly zkopírovanými z **XmlEntity** nejsou vždy přesné kopie jednou umístit odkaz uzlu entity.</span><span class="sxs-lookup"><span data-stu-id="b5665-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="b5665-112">Může být obory názvů, které jsou v rozsahu v uzlu odkazu entity a, který má vliv na konečnou konfiguraci podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="b5665-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="b5665-113">Ve výchozím nastavení, jako jsou obecné entity `&abc;` jsou zachovány a **XmlEntityReference** vždy vytvoří uzly.</span><span class="sxs-lookup"><span data-stu-id="b5665-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5665-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5665-114">See also</span></span>

- [<span data-ttu-id="b5665-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b5665-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
