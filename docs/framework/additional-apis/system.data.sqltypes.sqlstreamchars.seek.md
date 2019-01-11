---
title: Metoda SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1710c802324920e324b18ddea843f0a532fa0d17
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222984"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>Metoda SqlStreamChars.Seek (Int64, SeekOrigin)

Při přepisu v odvozené třídě, nastaví pozici v rámci aktuální datový proud. Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametry

`offset`\
Posun bajtů vzhledem k `origin`.

`origin`\
Jedna z hodnot výčtu, které určuje referenční bod, ze kterého chcete získat nové pozice.

## <a name="returns"></a>Vrací

<xref:System.Int32>\
Novou pozici v rámci aktuální datový proud.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlStreamChars.Seek` Metoda je privátní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.