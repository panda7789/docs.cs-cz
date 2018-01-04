---
title: "Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b59f85eb0ef6646345eaef2a409f622c6fe4651
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="ef190-102">Namespace vlivu na Entity odkaz na rozšíření pro nové uzly, který obsahuje elementy a atributy</span><span class="sxs-lookup"><span data-stu-id="ef190-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="ef190-103">Protože obsah deklarace entita může obsahovat prakticky jakoukoli, je možné, který obsah by mohl obsahovat element jako `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="ef190-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="ef190-104">Když je analyzovat kód XML, `&aname;` není rozbalen s jeho obsahem nahrazení při analýze.</span><span class="sxs-lookup"><span data-stu-id="ef190-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="ef190-105">Rozšíření XML není provést, protože překlad názvů pro element nemůže proběhnout, dokud uzlu je umístěn v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ef190-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="ef190-106">Do té doby není k dispozici žádné znalosti o jaký obor názvů je v oboru.</span><span class="sxs-lookup"><span data-stu-id="ef190-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="ef190-107">Pokud uzel umístí do dokumentu, pak dojde k rozlišení názvů a výsledného obsahu entity je analyzován do její odpovídající uzly.</span><span class="sxs-lookup"><span data-stu-id="ef190-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef190-108">Jakmile dojde k rozšíření v uzlu odkazu nově vytvořené entity, se nikdy opakovat.</span><span class="sxs-lookup"><span data-stu-id="ef190-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="ef190-109">Proto oborů názvů používaných v Nahrazovací text pro prvek je vázána na čas, který je nastavený nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="ef190-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="ef190-110">Ale oboru názvů lze změnit pro existující odkaz uzly entity, když odeberete a vložte je někde jinde, nebo na uzlech odkaz entity, které jsou klonovat s **CloneNode** metoda.</span><span class="sxs-lookup"><span data-stu-id="ef190-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef190-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef190-111">See Also</span></span>  
 [<span data-ttu-id="ef190-112">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ef190-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
