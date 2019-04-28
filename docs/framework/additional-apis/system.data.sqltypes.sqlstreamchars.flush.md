---
title: Metoda SqlStreamChars.Flush (System.Data.SqlTypes)
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
ms.openlocfilehash: 8cd24a5ca420552f283da61ecd4edcad02965403
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705854"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars.Flush – metoda

Při přepisu v odvozené třídě, vymaže všechny vyrovnávací paměti pro tento datový proud a způsobí, že všechna data ve vyrovnávací paměti k zápisu do základní zařízení. Sestavení, který obsahuje tato metoda má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlStreamChars.Flush` Metoda je privátní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.