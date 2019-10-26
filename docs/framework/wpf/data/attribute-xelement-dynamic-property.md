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
# <a name="attribute-xelement-dynamic-property"></a>Attribute (dynamická vlastnost XElement)

Získá indexer použitý k načtení instance atributu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

Indexer typu `XAttribute Item(String expandedName)`. Tento indexer Získá rozšířený název zadaného atributu a vrátí odpovídající <xref:System.Xml.Linq.XAttribute>, nebo `null`, pokud neexistuje žádný atribut se zadaným názvem.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Dynamické vlastnosti třídy XElement](attribute-xelement-dynamic-property.md)
- [Hodnota](value-xattribute-dynamic-property.md)
