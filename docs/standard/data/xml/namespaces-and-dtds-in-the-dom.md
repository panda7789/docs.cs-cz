---
title: "Obory názvů a specifikace DTD v modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87a03883622ba63a8d999907305356905b36bf1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="56d69-102">Obory názvů a specifikace DTD v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="56d69-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="56d69-103">Podpora complicate obor názvů typu definice (specifikace DTD) dokumentu.</span><span class="sxs-lookup"><span data-stu-id="56d69-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="56d69-104">Například následující kód XML obsahuje výchozí atributy, která obsahuje dvojtečky jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="56d69-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="56d69-105">Toto jsou možná řešení, pokud je povolena tato konstrukce:</span><span class="sxs-lookup"><span data-stu-id="56d69-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="56d69-106">`x:` Je zpracovaná jako Předpona oboru názvů, ale tato předpona musí být možné přeložit pomocí `xmlns:x` deklaraci oboru názvů, který musí někde existovat také ve DTD.</span><span class="sxs-lookup"><span data-stu-id="56d69-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="56d69-107">Jedná se o chybu mapovat tuto předponu něco jiného v dokumentu instance.</span><span class="sxs-lookup"><span data-stu-id="56d69-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="56d69-108">`x:` Je považován za předponu oboru názvů, ale tato předpona je vždy přeložit v kontextu instance elementů.</span><span class="sxs-lookup"><span data-stu-id="56d69-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="56d69-109">To znamená, že předpona, která může ve skutečnosti mapování na jiný obor názvů identifikátory Uniform Resource (Identifier), v závislosti na oboru názvů, ve kterém `item` prvek se zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="56d69-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="56d69-110">Toto chování je předvídatelnější než zadaná v dřívější odrážka rozlišení, ale má jiné složité následky, protože vyžaduje vyžaduje výchozí atributy.</span><span class="sxs-lookup"><span data-stu-id="56d69-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="56d69-111">Dvojtečkou se ignoruje, protože je v DTD a název atributu je `x:y`, žádná předpona a žádný identifikátor URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56d69-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="56d69-112">Dvojtečka v výchozí atribut vyvolá výjimku, informacemi o tom, že použití dvojteček v názvech definici DTD nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="56d69-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="56d69-113">Výsledkem je předvídatelný chování, ale nemůže načíst řadu World Wide Web Consortium (W3C) znamená publikovaný specifikace DTD.</span><span class="sxs-lookup"><span data-stu-id="56d69-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="56d69-114">Pokud uživatel požádá o ověření DTD, podpora obor názvů pro celý dokument je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="56d69-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="56d69-115">Díky tomu je možné načíst specifikace DTD W3C a výsledkem je předvídatelný chování.</span><span class="sxs-lookup"><span data-stu-id="56d69-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="56d69-116">Kód XML v rozhraní Microsoft .NET Framework implementuje druhá možnost pro maximální kompatibility W3C.</span><span class="sxs-lookup"><span data-stu-id="56d69-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d69-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="56d69-117">See Also</span></span>  
 [<span data-ttu-id="56d69-118">XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="56d69-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
