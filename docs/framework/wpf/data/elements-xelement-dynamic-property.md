---
title: Elements (dynamická vlastnost XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920851"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="91f42-102">Elements (dynamická vlastnost XElement)</span><span class="sxs-lookup"><span data-stu-id="91f42-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="91f42-103">Získá indexer použitý k načtení podřízených prvků aktuálního prvku, které odpovídají zadanému rozbalenému názvu.</span><span class="sxs-lookup"><span data-stu-id="91f42-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="91f42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91f42-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="91f42-105">Hodnota nebo návratová hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="91f42-105">Property value/return value</span></span>

<span data-ttu-id="91f42-106">Indexer typu `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="91f42-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="91f42-107">Tento indexer Získá rozšířený název požadovaných podřízených prvků a vrátí odpovídající podřízené prvky ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.</span><span class="sxs-lookup"><span data-stu-id="91f42-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="91f42-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91f42-108">Remarks</span></span>

<span data-ttu-id="91f42-109">Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="91f42-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="91f42-110">Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="91f42-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="91f42-111">Tato vlastnost používá odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="91f42-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="91f42-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91f42-112">See also</span></span>

- [<span data-ttu-id="91f42-113">Dynamické vlastnosti třídy XElement</span><span class="sxs-lookup"><span data-stu-id="91f42-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="91f42-114">Element</span><span class="sxs-lookup"><span data-stu-id="91f42-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="91f42-115">Potomci</span><span class="sxs-lookup"><span data-stu-id="91f42-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
