---
title: Obory názvů a specifikace DTD v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 22762e3a7003d9b28a53c7b500829aaa41924c6d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710593"
---
# <a name="namespaces-and-dtds-in-the-dom"></a><span data-ttu-id="52b54-102">Obory názvů a specifikace DTD v modelu DOM</span><span class="sxs-lookup"><span data-stu-id="52b54-102">Namespaces and DTDs in the DOM</span></span>
<span data-ttu-id="52b54-103">Definice typu dokumentu (DTD) komplikuje podporu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="52b54-103">Document type definitions (DTDs) complicate namespace support.</span></span> <span data-ttu-id="52b54-104">Například následující kód XML obsahuje výchozí atributy obsahující dvojtečky ve svých názvech.</span><span class="sxs-lookup"><span data-stu-id="52b54-104">For example, the following XML contains default attributes containing colons in their names.</span></span>  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 <span data-ttu-id="52b54-105">Níže jsou uvedena možná řešení, pokud je tato konstrukce povolená:</span><span class="sxs-lookup"><span data-stu-id="52b54-105">The following are possible resolutions if this construct is allowed:</span></span>  
  
- <span data-ttu-id="52b54-106">`x:` Je považován za předponu oboru názvů, ale tuto předponu je nutné přeložit pomocí deklarace `xmlns:x` oboru názvů, která musí také existovat někde v DTD.</span><span class="sxs-lookup"><span data-stu-id="52b54-106">The `x:` is treated as a namespace prefix, but this prefix must be resolvable using an `xmlns:x` namespace declaration, which must also exist somewhere in the DTD.</span></span> <span data-ttu-id="52b54-107">Namapování této předpony na jinou hodnotu v dokumentu instance je chyba.</span><span class="sxs-lookup"><span data-stu-id="52b54-107">It is an error to map this prefix to something different in the instance document.</span></span>  
  
- <span data-ttu-id="52b54-108">`x:` Je považován za předponu oboru názvů, ale tato předpona je vždy vyřešena v kontextu prvků instance.</span><span class="sxs-lookup"><span data-stu-id="52b54-108">The `x:` is treated as a namespace prefix, but this prefix is always resolved in the context of the instance elements.</span></span> <span data-ttu-id="52b54-109">To znamená, že předpona může být ve skutečnosti namapována na různé obory názvů identifikátorů URI (Uniform Resource Identifier) `item` , v závislosti na oboru názvů, ve kterém se prvek zobrazí.</span><span class="sxs-lookup"><span data-stu-id="52b54-109">This means the prefix could actually map to different namespace Uniform Resource Identifiers (URIs), depending on the namespace scope in which the `item` element appears.</span></span> <span data-ttu-id="52b54-110">Toto chování je více předvídatelné než řešení uvedené v předchozí odrážce, ale má jiné složité důsledky, protože vyžaduje, aby byly výchozí atributy vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="52b54-110">This behavior is more predictable than the resolution given in the earlier bullet, but it has other complicated ramifications because it requires the default attributes be materialized.</span></span>  
  
- <span data-ttu-id="52b54-111">Dvojtečka se ignoruje, protože je v definici DTD a název atributu je `x:y`, bez předpony a ŽÁDNÉho identifikátoru URI oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="52b54-111">The colon is ignored because it is in a DTD, and the name of the attribute is `x:y`, no prefix and no namespace URI.</span></span>  
  
- <span data-ttu-id="52b54-112">Dvojtečka ve výchozím atributu vyvolá výjimku, která říká, že dvojtečky v názvech uvnitř DTD nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="52b54-112">The colon in the default attribute throws an exception, saying that colons in names inside a DTD are not supported.</span></span> <span data-ttu-id="52b54-113">Výsledkem je předvídatelné chování, ale znamená, že nemůžete načíst mnoho publikovaných definic DTD konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="52b54-113">This results in a predictable behavior, but means you cannot load many of the World Wide Web Consortium (W3C) published DTDs.</span></span>  
  
- <span data-ttu-id="52b54-114">Když uživatel vyžádá ověření DTD, podpora oboru názvů pro celý dokument je vypnuta.</span><span class="sxs-lookup"><span data-stu-id="52b54-114">When the user requests DTD validation, namespace support for the entire document is turned off.</span></span> <span data-ttu-id="52b54-115">Díky tomu je možné načíst specifikace DTD W3C a výsledky v předvídatelném chování.</span><span class="sxs-lookup"><span data-stu-id="52b54-115">This makes it possible to load W3C DTDs and results in a predictable behavior.</span></span>  
  
 <span data-ttu-id="52b54-116">XML v Microsoft .NET Framework implementuje druhou možnost maximální kompatibility W3C.</span><span class="sxs-lookup"><span data-stu-id="52b54-116">The XML in the Microsoft .NET Framework implements the second option for maximum W3C compatibility.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b54-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="52b54-117">See also</span></span>

- [<span data-ttu-id="52b54-118">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="52b54-118">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
