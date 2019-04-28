---
title: SqlChars.Stream Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4858d9f8878e5b56a0811edf92a2faa729775156
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675193"
---
# <a name="sqlcharsstream-property"></a>SqlChars.Stream – vlastnost

Získá nebo nastaví datového proudu znaků. Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a>Hodnota vlastnosti

`System.Data.SqlTypes.SqlStreamChars`\
Datového proudu znaků.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlChars.Stream` Vlastnost je interní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.