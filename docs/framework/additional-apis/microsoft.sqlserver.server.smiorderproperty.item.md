---
title: Vlastnost SmiOrderProperty.Item (Microsoft.SqlServer.Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 499522a11cac744c14ac32cf3bfe485a46b19d93
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634320"
---
# <a name="smiorderpropertyitem-property"></a>Vlastnost SmiOrderProperty.Item

Získá pořadí sloupců pro entitu. Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll. Je určena pro použití systémem SQL Server. U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.

## <a name="syntax"></a>Syntaxe

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>Hodnota vlastnosti

Pořadí sloupců.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `SmiOrderProperty.Item` Vlastnost je interní a není určena pro použití přímo v kódu.
>
> Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:Microsoft.SqlServer.Server>

**Sestavení:** System.Data (v System.Data.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 2.0.