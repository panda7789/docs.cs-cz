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
# <a name="element-xelement-dynamic-property"></a>Element (dynamická vlastnost XElement)

Získá indexer použitý k načtení instance podřízeného elementu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

Indexer typu `XElement Item(String expandedName)`. Tento indexer Získá rozšířený parametr názvu a vrátí odpovídající <xref:System.Xml.Linq.XElement>, nebo `null`, pokud neexistuje žádný element se zadaným názvem.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Element%2A> metodě <xref:System.Xml.Linq.XContainer?displayProperty=fullName> třídy.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Dynamické vlastnosti třídy XElement](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
