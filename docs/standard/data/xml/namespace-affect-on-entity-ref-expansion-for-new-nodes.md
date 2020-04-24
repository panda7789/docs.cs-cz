---
title: Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 4772e3f7365069c537c4ec3bc8571f2f710bc9fc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710619"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="061d2-102">Vliv oboru názvů na rozšíření odkazu na entitu pro nové uzly, který obsahují elementy a atributy</span><span class="sxs-lookup"><span data-stu-id="061d2-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="061d2-103">Vzhledem k tomu, že obsah deklarace entity může obsahovat téměř cokoli, existuje možnost, že obsah může obsahovat element jako `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="061d2-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="061d2-104">Když je kód XML analyzován, `&aname;` není rozbalený s jeho náhradním obsahem v době analýzy.</span><span class="sxs-lookup"><span data-stu-id="061d2-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="061d2-105">Rozšíření XML není provedeno, protože překlad oboru názvů pro element nemůže nastat, dokud není uzel umístěn v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="061d2-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="061d2-106">Až do této doby nebudete znát obor názvů, který je v oboru.</span><span class="sxs-lookup"><span data-stu-id="061d2-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="061d2-107">Když je uzel umístěn do dokumentu, pak dojde k překladu oboru názvů a výsledný obsah entity se analyzuje v příslušných uzlech.</span><span class="sxs-lookup"><span data-stu-id="061d2-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="061d2-108">Jakmile dojde k rozšíření u nově vytvořeného uzlu odkazu na entitu, nikdy se znovu nespustí.</span><span class="sxs-lookup"><span data-stu-id="061d2-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="061d2-109">Proto jsou obory názvů použité v náhradním textu pro element vázány v době, kdy je nastaven nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="061d2-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="061d2-110">Obor názvů lze však změnit pro existující uzly odkazů na entity, když je odeberete a vložíte někam jinam nebo na referenční uzly entit, které jsou naklonovány metodou **CloneNode** .</span><span class="sxs-lookup"><span data-stu-id="061d2-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061d2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="061d2-111">See also</span></span>

- [<span data-ttu-id="061d2-112">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="061d2-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
