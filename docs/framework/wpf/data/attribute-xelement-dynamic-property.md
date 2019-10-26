---
title: Attribute (dynamická vlastnost XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 2b645575a5b6876ffbb52a999c4e05a2de037493
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920914"
---
# <a name="attribute-xelement-dynamic-property"></a><span data-ttu-id="91cff-102">Attribute (dynamická vlastnost XElement)</span><span class="sxs-lookup"><span data-stu-id="91cff-102">Attribute (XElement dynamic property)</span></span>

<span data-ttu-id="91cff-103">Získá indexer použitý k načtení instance atributu, který odpovídá zadanému rozšířenému názvu.</span><span class="sxs-lookup"><span data-stu-id="91cff-103">Gets an indexer used to retrieve the attribute instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="91cff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91cff-104">Syntax</span></span>

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="91cff-105">Hodnota nebo návratová hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="91cff-105">Property value/return value</span></span>

<span data-ttu-id="91cff-106">Indexer typu `XAttribute Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="91cff-106">An indexer of the type `XAttribute Item(String expandedName)`.</span></span> <span data-ttu-id="91cff-107">Tento indexer Získá rozšířený název zadaného atributu a vrátí odpovídající <xref:System.Xml.Linq.XAttribute>, nebo `null`, pokud neexistuje žádný atribut se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="91cff-107">This indexer takes the expanded name of the specified attribute and returns the corresponding <xref:System.Xml.Linq.XAttribute>, or `null` if there is no attribute with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="91cff-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91cff-108">Remarks</span></span>

<span data-ttu-id="91cff-109">Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="91cff-109">This property is equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="91cff-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91cff-110">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [<span data-ttu-id="91cff-111">Dynamické vlastnosti třídy XElement</span><span class="sxs-lookup"><span data-stu-id="91cff-111">XElement Class Dynamic Properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="91cff-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="91cff-112">Value</span></span>](value-xattribute-dynamic-property.md)
