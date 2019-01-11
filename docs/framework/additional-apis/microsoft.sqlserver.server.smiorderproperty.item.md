---
title: Vlastnost SmiOrderProperty.Item (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5453167e16e2658b3546b7114201b04d481a0c79
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222999"
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