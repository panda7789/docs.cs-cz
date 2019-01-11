---
title: Vlastnost SqlStreamChars.IsNull (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7bef26119e31658b8495df402bbc07341cd84cf7
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222555"
---
# <a name="sqlstreamcharsisnull-property"></a>Vlastnost SqlStreamChars.IsNull

Při přepisu v odvozené třídě získá hodnotu, která určuje, zda je datový proud `null`. Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Boolean>\
`true` Pokud je datový proud `null`; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SqlStreamChars.IsNull` Vlastnost je privátní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Data.SqlTypes>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.