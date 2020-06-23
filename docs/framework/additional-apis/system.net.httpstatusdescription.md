---
title: HttpStatusDescription – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990337"
---
# <a name="httpstatusdescription-class"></a>HttpStatusDescription – třída

Poskytuje standardní popisy stavu HTTP. Tuto třídu nelze zdědit.

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="get-method"></a>Get – metoda

Vrátí popis přidružený k zadanému kódu stavu HTTP.

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>Parametry

`code` <xref:System.Int32>

Stavový kód protokolu HTTP, například `404` .

### <a name="return-value"></a>Vrácená hodnota

<xref:System.String?displayProperty=nameWithType>

Popis stavu protokolu HTTP.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
