---
title: Kopírování existujících uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864127"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="a77e6-102">Kopírování existujících uzlů</span><span class="sxs-lookup"><span data-stu-id="a77e6-102">Copy Existing Nodes</span></span>
<span data-ttu-id="a77e6-103">Existuje mnoho metod a vlastností v XML dokumentu objektu modelu modelu DOM () vám pomůže se vyberte uzel, jako je například **SelectSingleNode**, **ChildNodes [int můžu]**, **atributy [int můžu]**.</span><span class="sxs-lookup"><span data-stu-id="a77e6-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="a77e6-104">Po výběru uzlu ji můžete vložit do stromu pomocí jedné z metod vložení, které fungují pro daný typ konkrétní uzel.</span><span class="sxs-lookup"><span data-stu-id="a77e6-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="a77e6-105">Jediným omezením při vkládání uzlu do stromu je, že dokument přesto musí být ve správném formátu po vložení uzlu.</span><span class="sxs-lookup"><span data-stu-id="a77e6-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="a77e6-106">Když existující uzel je vložen do stromu modelu DOM, je odebrán z jeho původní pozice a přidány do cílového umístění.</span><span class="sxs-lookup"><span data-stu-id="a77e6-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77e6-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a77e6-107">See also</span></span>

- [<span data-ttu-id="a77e6-108">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="a77e6-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
