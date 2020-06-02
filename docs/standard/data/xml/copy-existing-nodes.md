---
title: Kopírování existujících uzlů
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289210"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="5cff0-102">Kopírování existujících uzlů</span><span class="sxs-lookup"><span data-stu-id="5cff0-102">Copy Existing Nodes</span></span>
<span data-ttu-id="5cff0-103">Existuje mnoho metod a vlastností v souboru XML model DOM (Document Object Model) (DOM), které můžete použít k výběru uzlu, například **SelectSingleNode**, **ChildNodes [int i]**, **atributů [int i]**.</span><span class="sxs-lookup"><span data-stu-id="5cff0-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="5cff0-104">Po výběru uzlu jej můžete vložit do stromu pomocí jedné z metod vložení, které fungují pro daný typ uzlu.</span><span class="sxs-lookup"><span data-stu-id="5cff0-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="5cff0-105">Jediným omezením pro vložení uzlu do stromu je, že dokument musí být po vložení uzlu stále správně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="5cff0-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="5cff0-106">Když je existující uzel vložen do stromu modelu DOM, je odebrán z původní pozice a přidán na jeho cílovou pozici.</span><span class="sxs-lookup"><span data-stu-id="5cff0-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cff0-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cff0-107">See also</span></span>

- [<span data-ttu-id="5cff0-108">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5cff0-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
