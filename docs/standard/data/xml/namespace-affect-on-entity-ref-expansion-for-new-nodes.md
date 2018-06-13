---
title: Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2ba9964f17380e868ea5fe906a40f8b491018a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568898"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="0d887-102">Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy</span><span class="sxs-lookup"><span data-stu-id="0d887-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="0d887-103">Protože obsah deklarace entita může obsahovat prakticky jakoukoli, je možné, který obsah by mohl obsahovat element jako `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="0d887-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="0d887-104">Když je analyzovat kód XML, `&aname;` není rozbalen s jeho obsahem nahrazení při analýze.</span><span class="sxs-lookup"><span data-stu-id="0d887-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="0d887-105">Rozšíření XML není provést, protože překlad názvů pro element nemůže proběhnout, dokud uzlu je umístěn v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0d887-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="0d887-106">Do té doby není k dispozici žádné znalosti o jaký obor názvů je v oboru.</span><span class="sxs-lookup"><span data-stu-id="0d887-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="0d887-107">Pokud uzel umístí do dokumentu, pak dojde k rozlišení názvů a výsledného obsahu entity je analyzován do její odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="0d887-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d887-108">Jakmile dojde k rozšíření v uzlu odkazu nově vytvořené entity, se nikdy opakovat.</span><span class="sxs-lookup"><span data-stu-id="0d887-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="0d887-109">Proto oborů názvů používaných v Nahrazovací text pro prvek je vázána na čas, který je nastavený nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="0d887-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="0d887-110">Ale oboru názvů lze změnit pro existující odkaz uzly entity, když odeberete a vložte je někde jinde, nebo na uzlech odkaz entity, které jsou klonovat s **CloneNode** metoda.</span><span class="sxs-lookup"><span data-stu-id="0d887-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d887-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d887-111">See Also</span></span>  
 [<span data-ttu-id="0d887-112">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0d887-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
