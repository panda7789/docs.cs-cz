---
title: SqlStreamChars. Length – vlastnost (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395610"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. Length – vlastnost

Při přepsání v odvozené třídě získá délku aktuálního datového proudu. Sestavení, které obsahuje tuto vlastnost, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

## <a name="syntax"></a>Syntaxe

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

<xref:System.Int64>\
Délka datového proudu.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Vlastnost `SqlStreamChars.Length` je soukromá a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této vlastnosti v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
