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
# <a name="elements-xelement-dynamic-property"></a>Elements (dynamická vlastnost XElement)

Získá indexer použitý k načtení podřízených prvků aktuálního prvku, které odpovídají zadanému rozbalenému názvu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

Indexer typu `IEnumerable<XElement> Item(String expandedName)`. Tento indexer Získá rozšířený název požadovaných podřízených prvků a vrátí odpovídající podřízené prvky ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.

Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](attribute-xelement-dynamic-property.md)
- [Element](element-xelement-dynamic-property.md)
- [Potomci](descendants-xelement-dynamic-property.md)
