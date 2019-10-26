---
title: Xml (dynamická vlastnost XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920718"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamická vlastnost XElement)

Získá neformátovaný obsah XML elementu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

<xref:System.String>, která představuje neformátovaný obsah XML elementu.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> <xref:System.Xml.Linq.XNode?displayProperty=fullName> třídy s parametrem `SaveOptions` nastaveným na <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](attribute-xelement-dynamic-property.md)
- [Hodnota](value-xelement-dynamic-property.md)
