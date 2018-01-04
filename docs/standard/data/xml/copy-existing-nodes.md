---
title: "Zkopírujte existující uzly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c026d9f825375d74d53d5cc46969ff0f713bab1c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="37767-102">Zkopírujte existující uzly</span><span class="sxs-lookup"><span data-stu-id="37767-102">Copy Existing Nodes</span></span>
<span data-ttu-id="37767-103">Existuje mnoho metody a vlastnosti v XML objektu modelu DOM (Document) můžete použít k výběru uzlu, jako například **SelectSingleNode**, **ChildNodes [int i]**, **atributy [int i]**.</span><span class="sxs-lookup"><span data-stu-id="37767-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="37767-104">Jakmile uzlu je vybraná, můžete je do stromu pomocí jedné z metod vložení, které fungují pro tento typ konkrétním uzlu.</span><span class="sxs-lookup"><span data-stu-id="37767-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="37767-105">Pouze omezení pro vkládání uzlu do stromu je, že je dokument stále ve správném formátu po vložení uzlu.</span><span class="sxs-lookup"><span data-stu-id="37767-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="37767-106">Když stávající uzel vložíte do stromu modelu DOM, je odebrán z jeho původní pozice a přidat do cílové polohy.</span><span class="sxs-lookup"><span data-stu-id="37767-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37767-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="37767-107">See Also</span></span>  
 [<span data-ttu-id="37767-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="37767-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
