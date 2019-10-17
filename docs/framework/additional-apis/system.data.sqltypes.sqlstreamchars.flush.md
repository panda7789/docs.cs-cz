---
title: SqlStreamChars. Flush – metoda (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395616"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush – metoda

Při přepsání v odvozené třídě vymaže všechny vyrovnávací paměti pro tento datový proud a způsobí, že všechna data uložená do vyrovnávací paměti budou zapsána do základního zařízení. Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `SqlStreamChars.Flush` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
