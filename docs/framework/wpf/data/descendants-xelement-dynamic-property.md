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
# <a name="descendants-xelement-dynamic-property"></a>Descendants (dynamická vlastnost XElement)

Získá indexer použitý k načtení všech následníků aktuálního prvku, který se shoduje se zadaným rozbaleným názvem.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

Indexer typu `IEnumerable<XElement> Item(String expandedName)`. Tento indexer získá rozbalený název zadaných potomkových prvků a vrátí vyhovující podřízené elementy ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.

Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](attribute-xelement-dynamic-property.md)
- [Elements](elements-xelement-dynamic-property.md)
