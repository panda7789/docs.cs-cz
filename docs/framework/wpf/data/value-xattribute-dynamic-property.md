---
title: Value (dynamická vlastnost XAttribute)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.openlocfilehash: 32c15a89a976b5f9af12f040c43e724a25357ead
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920648"
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamická vlastnost XAttribute)

Získá nebo nastaví hodnotu atributu XML.

## <a name="syntax"></a>Syntaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

<xref:System.String> obsahující hodnotu tohoto atributu.

## <a name="exceptions"></a>Výjimky

|Typ výjimky|Podmínka|
| - |---------------|
|<xref:System.ArgumentNullException>|Při nastavování je `value` `null`.|

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní vlastnosti <xref:System.Xml.Linq.XAttribute.Value%2A> třídy <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ale tato dynamická vlastnost také podporuje oznamování změn.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Dynamické vlastnosti třídy XAttribute](value-xattribute-dynamic-property.md)
- [Atribut](attribute-xelement-dynamic-property.md)
