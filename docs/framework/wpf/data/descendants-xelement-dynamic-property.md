---
title: Descendants (dynamická vlastnost XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920886"
---
# <a name="descendants-xelement-dynamic-property"></a><span data-ttu-id="c6eb2-102">Descendants (dynamická vlastnost XElement)</span><span class="sxs-lookup"><span data-stu-id="c6eb2-102">Descendants (XElement dynamic property)</span></span>

<span data-ttu-id="c6eb2-103">Získá indexer použitý k načtení všech následníků aktuálního prvku, který se shoduje se zadaným rozbaleným názvem.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-103">Gets an indexer used to retrieve all the descendant elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6eb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6eb2-104">Syntax</span></span>

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="c6eb2-105">Hodnota nebo návratová hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c6eb2-105">Property value/return value</span></span>

<span data-ttu-id="c6eb2-106">Indexer typu `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="c6eb2-107">Tento indexer získá rozbalený název zadaných potomkových prvků a vrátí vyhovující podřízené elementy ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-107">This indexer takes the expanded name of the specified descendant elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6eb2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6eb2-108">Remarks</span></span>

<span data-ttu-id="c6eb2-109">Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="c6eb2-110">Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="c6eb2-111">Tato vlastnost používá odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="c6eb2-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6eb2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6eb2-112">See also</span></span>

- [<span data-ttu-id="c6eb2-113">Dynamické vlastnosti třídy XElement</span><span class="sxs-lookup"><span data-stu-id="c6eb2-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="c6eb2-114">Elements</span><span class="sxs-lookup"><span data-stu-id="c6eb2-114">Elements</span></span>](elements-xelement-dynamic-property.md)
