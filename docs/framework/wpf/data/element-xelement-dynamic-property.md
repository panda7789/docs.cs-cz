---
title: Element (dynamická vlastnost XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920893"
---
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="63836-102">Element (dynamická vlastnost XElement)</span><span class="sxs-lookup"><span data-stu-id="63836-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="63836-103">Získá indexer použitý k načtení instance podřízeného elementu, který odpovídá zadanému rozšířenému názvu.</span><span class="sxs-lookup"><span data-stu-id="63836-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="63836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63836-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="63836-105">Hodnota nebo návratová hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="63836-105">Property value/return value</span></span>

<span data-ttu-id="63836-106">Indexer typu `XElement Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="63836-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="63836-107">Tento indexer Získá rozšířený parametr názvu a vrátí odpovídající <xref:System.Xml.Linq.XElement>, nebo `null`, pokud neexistuje žádný element se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="63836-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="63836-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63836-108">Remarks</span></span>

<span data-ttu-id="63836-109">Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Element%2A> metodě <xref:System.Xml.Linq.XContainer?displayProperty=fullName> třídy.</span><span class="sxs-lookup"><span data-stu-id="63836-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="63836-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63836-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="63836-111">Dynamické vlastnosti třídy XElement</span><span class="sxs-lookup"><span data-stu-id="63836-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="63836-112">Elements</span><span class="sxs-lookup"><span data-stu-id="63836-112">Elements</span></span>](elements-xelement-dynamic-property.md)
