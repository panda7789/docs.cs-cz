---
title: SqlStreamChars. IsNull – vlastnost (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395738"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars. IsNull – vlastnost

Při přepsání v odvozené třídě získá hodnotu, která označuje, zda je datový proud `null`. Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Boolean>\
`true`, pokud je datový proud `null`; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Vlastnost `SqlStreamChars.IsNull` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
