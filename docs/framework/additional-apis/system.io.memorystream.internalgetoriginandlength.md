---
title: Typu MemoryStream není. InternalGetOriginAndLength – metoda (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284029"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>Typu MemoryStream není. InternalGetOriginAndLength – metoda

Získá interní hodnoty původu a délky streamu paměti.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Parametry

- `origin` <xref:System.Int32>\
  Když tato metoda vrátí hodnotu, posun pole bajtů zadané při vytváření nového objektu <xref:System.IO.MemoryStream>. Obsahuje 0, pokud bylo pole bajtů vytvořeno pomocí <xref:System.IO.MemoryStream>.

- `length` <xref:System.Int32>\
  Až tato metoda vrátí hodnotu, počet bajtů v paměťovém proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `MemoryStream.InternalGetOriginAndLength` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.IO>

**Sestavení:** mscorlib. dll (v mscorlib. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
