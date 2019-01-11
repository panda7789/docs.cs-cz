---
title: Metoda SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221905"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>Metoda SqlStreamChars.Write (Char [], Int32, Int32)

Při přepisu v odvozené třídě, zapíše posloupnost znaků do aktuální datový proud a posune aktuální pozici v rámci tohoto datového proudu o počet napsaných znaků. Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`  
Pole znaků k zápisu.

`offset`  
Posun vzhledem k počátku.

`count`  
Počet znaků k zápisu do aktuální datový proud.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlStreamChars.Write` Metoda je privátní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.