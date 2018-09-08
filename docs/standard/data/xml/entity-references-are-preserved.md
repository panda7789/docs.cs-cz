---
title: Odkazy na entity jsou zachovány.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204314"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="88767-102">Odkazy na entity jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="88767-102">Entity References are Preserved</span></span>
<span data-ttu-id="88767-103">Pokud odkaz na entitu není rozbalen, ale zachovají, sestavení XML Document Object Model (DOM) **XmlEntityReference** uzlu, pokud se setká s odkazu na entitu.</span><span class="sxs-lookup"><span data-stu-id="88767-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="88767-104">Pomocí následující kód XML</span><span class="sxs-lookup"><span data-stu-id="88767-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="88767-105">sestavení modelu DOM **XmlEntityReference** uzlu, pokud se setká `&publisher;` odkaz.</span><span class="sxs-lookup"><span data-stu-id="88767-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="88767-106">**XmlEntityReference** obsahuje podřízené uzly, které jsou kopírovány z obsahu entity prohlášení.</span><span class="sxs-lookup"><span data-stu-id="88767-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="88767-107">Předchozí příklad kódu obsahuje text v entity prohlášení, takže **XmlText** uzel je vytvořen jako podřízený uzel uzlu odkazu entity.</span><span class="sxs-lookup"><span data-stu-id="88767-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="88767-108">![Stromová struktura pro odkazy na entity zachovaných](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="88767-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="88767-109">Stromovou strukturu pro odkazy na entity, které jsou zachovány</span><span class="sxs-lookup"><span data-stu-id="88767-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="88767-110">Podřízené uzly **XmlEntityReference** jsou kopie všech podřízených uzlů vytvořené z **XmlEntity** uzlu, když došlo k deklaraci entity.</span><span class="sxs-lookup"><span data-stu-id="88767-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88767-111">Uzly zkopírovanými z **XmlEntity** nejsou vždy přesné kopie jednou umístit odkaz uzlu entity.</span><span class="sxs-lookup"><span data-stu-id="88767-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="88767-112">Může být obory názvů, které jsou v rozsahu v uzlu odkazu entity a, který má vliv na konečnou konfiguraci podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="88767-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="88767-113">Ve výchozím nastavení, jako jsou obecné entity `&abc;` jsou zachovány a **XmlEntityReference** vždy vytvoří uzly.</span><span class="sxs-lookup"><span data-stu-id="88767-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88767-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88767-114">See also</span></span>

- [<span data-ttu-id="88767-115">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="88767-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
