---
title: Metoda SqlStreamChars.Read (Char [], Int32, Int32) (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: df92acfd4050eb16d3a101b20b9b44560273f4d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675231"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>Metoda SqlStreamChars.Read (Char [], Int32, Int32)

Při přepisu v odvozené třídě, načte další sadu znaků ze vstupního datového proudu. Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`\
Pole znaků ke čtení.

`offset`\
Posun vzhledem k počátku.

`count`\
Počet znaků ke čtení z aktuální datový proud.

## <a name="returns"></a>Vrací

<xref:System.Int32>\
Celkový počet znaků do vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlStreamChars.Read` Metoda je privátní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.