---
title: SqlStreamChars. Close – metoda (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395638"
---
# <a name="sqlstreamcharsclose-method"></a>SqlStreamChars. Close – metoda

Zavře aktuální datový proud a uvolní všechny systémové prostředky přidružené ke streamu. Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
public virtual void Close ();
```

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `SqlStreamChars.Close` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
