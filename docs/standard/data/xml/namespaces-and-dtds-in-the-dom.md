---
title: Obory názvů a specifikace DTD v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027804"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="4da6f-102">Obory názvů a specifikace DTD v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="4da6f-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="4da6f-103">Podpora dokumentu typ definice (DTD) complicate oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4da6f-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="4da6f-104">Například následující kód XML obsahuje výchozí atributy obsahující dvojteček při jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="4da6f-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="4da6f-105">Následující jsou uvedena možná řešení, pokud je povolený tento konstruktor:</span><span class="sxs-lookup"><span data-stu-id="4da6f-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
-   <span data-ttu-id="4da6f-106">`x:` Je zpracováván jako předponu oboru názvů, ale tuto předponu, musí být možné přeložit pomocí `xmlns:x` deklarace oboru názvů, který musí taky existovat někde jinde v DTD.</span><span class="sxs-lookup"><span data-stu-id="4da6f-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="4da6f-107">Jedná se o chybu pro tuto předponu mapování na něco jiného v dokumentu instance.</span><span class="sxs-lookup"><span data-stu-id="4da6f-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
-   <span data-ttu-id="4da6f-108">`x:` Je považován za předponu oboru názvů, ale tato předpona je vždy přeložit v rámci prvků instance.</span><span class="sxs-lookup"><span data-stu-id="4da6f-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="4da6f-109">To znamená, že předpona, která by mohla ve skutečnosti mapují na jiný obor názvů Uniform Resource Identifier (identifikátory URI), v závislosti na rozsahu oboru názvů ve kterém `item` element objeví.</span><span class="sxs-lookup"><span data-stu-id="4da6f-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="4da6f-110">Toto chování je předvídatelnější než uvedené v předchozích odrážky rozlišení, ale má jiné složité následky, protože vyžaduje materializace výchozí atributy.</span><span class="sxs-lookup"><span data-stu-id="4da6f-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
-   <span data-ttu-id="4da6f-111">Dvojtečka je ignorován, protože je v DTD a název atributu je `x:y`, žádná předpona a žádný obor názvů identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="4da6f-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
-   <span data-ttu-id="4da6f-112">Dvojtečka ve výchozí atribut vyvolá výjimku, informacemi o tom, že se nepodporují použití dvojteček v názvech definici DTD.</span><span class="sxs-lookup"><span data-stu-id="4da6f-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="4da6f-113">Výsledkem je předvídatelný chování, ale znamená, že nelze načíst řadu World Wide Web Consortium (W3C) publikovaný specifikace DTD.</span><span class="sxs-lookup"><span data-stu-id="4da6f-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
-   <span data-ttu-id="4da6f-114">Když uživatel požádá o ověření DTD, podpora oboru názvů pro celý dokument je vypnutý.</span><span class="sxs-lookup"><span data-stu-id="4da6f-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="4da6f-115">Umožňuje načíst W3C DTD a výsledkem je předvídatelný chování.</span><span class="sxs-lookup"><span data-stu-id="4da6f-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="4da6f-116">Kód XML v rozhraní Microsoft .NET Framework implementuje druhou možnost pro maximální kompatibility W3C.</span><span class="sxs-lookup"><span data-stu-id="4da6f-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da6f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4da6f-117">See also</span></span>

- [<span data-ttu-id="4da6f-118">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="4da6f-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
