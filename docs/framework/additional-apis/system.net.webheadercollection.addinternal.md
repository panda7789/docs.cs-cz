---
title: WebHeaderCollection. AddInternal – metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990322"
---
# <a name="webheadercollectionaddinternal-method"></a>WebHeaderCollection. AddInternal – metoda

Přidá novou hlavičku se zadaným názvem a hodnotou do kolekce a obchází kontroly.

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> Tato metoda je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="parameters"></a>Parametry

- `name` <xref:System.String>

  Název záhlaví.

- `value` <xref:System.String>

  Hodnota záhlaví

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
