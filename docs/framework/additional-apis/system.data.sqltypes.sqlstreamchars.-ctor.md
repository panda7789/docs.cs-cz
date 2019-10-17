---
title: Konstruktor SqlStreamChars (System. data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars..ctor
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 34c5dcfe458ca57aa3bd5388e8b4c66c3c497df6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395647"
---
# <a name="sqlstreamchars-constructor"></a>SqlStreamChars – konstruktor

Inicializuje novou instanci třídy `SqlStreamChars`. Sestavení, které obsahuje tento konstruktor, má relaci typu Friend s SQLAccess. dll. Je určena pro použití v SQL Server. U ostatních databází použijte mechanizmus hostování, který poskytuje tato databáze.

```csharp
protected SqlStreamChars ();
```

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Konstruktor `SqlStreamChars` je chráněn a není určen pro použití přímo v kódu.
>
> Microsoft nepodporuje použití tohoto konstruktoru v produkční aplikaci za žádných okolností.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Data.SqlTypes>

**Sestavení:** System. data (v System. data. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
