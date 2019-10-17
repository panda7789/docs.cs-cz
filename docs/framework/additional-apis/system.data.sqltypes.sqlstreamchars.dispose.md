---
title: SqlStreamChars. Dispose (Boolean) – metoda (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395757"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars. Dispose (Boolean) – metoda

Při přepsání v odvozené třídě uvolní prostředky používané datovým proudem. Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>Parametry

`disposing`\
`true` pro vydání spravovaných i nespravovaných prostředků; `false` pro vydání pouze nespravovaných prostředků.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `SqlStreamChars.Dispose` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
