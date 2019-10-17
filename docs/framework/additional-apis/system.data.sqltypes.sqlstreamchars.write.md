---
title: SqlStreamChars. Write – metoda (Char [], Int32, Int32) (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395575"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars. Write – metoda (Char [], Int32, Int32)

Při přepsání v odvozené třídě zapíše posloupnost znaků do aktuálního datového proudu a Posune aktuální pozici v rámci tohoto datového proudu o počet zapsaných znaků. Sestavení, které obsahuje tuto metodu, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`  
Pole znaků, které se má zapsat

`offset`  
Posun vzhledem ke zdroji.

`count`  
Počet znaků, které mají být zapsány do aktuálního datového proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `SqlStreamChars.Write` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft nepodporuje použití této metody zápisu do produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
