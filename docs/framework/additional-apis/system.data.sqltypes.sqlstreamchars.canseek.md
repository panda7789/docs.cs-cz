---
title: SqlStreamChars. CanSeek – vlastnost (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395782"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek – vlastnost

Při přepsání v odvozené třídě získá hodnotu, která označuje, zda aktuální pára podporuje operaci hledání. Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Boolean>\
`true`, pokud aktuální pára podporuje operaci hledání; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Vlastnost `SqlStreamChars.CanSeek` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
