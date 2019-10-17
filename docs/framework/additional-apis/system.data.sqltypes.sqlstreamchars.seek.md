---
title: SqlStreamChars. Seek – Metoda (Int64, SeekOrigin) (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395600"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. Seek – Metoda (Int64, SeekOrigin)

Při přepsání v odvozené třídě nastaví pozici v rámci aktuálního datového proudu. Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametry

`offset`\
Posun bajtů vzhledem k `origin`.

`origin`\
Jedna z hodnot výčtu, která určuje referenční bod, z něhož má být získána nová pozice.

## <a name="returns"></a>Vrací

<xref:System.Int32>\
Nová pozice v aktuálním datovém proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `SqlStreamChars.Seek` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
