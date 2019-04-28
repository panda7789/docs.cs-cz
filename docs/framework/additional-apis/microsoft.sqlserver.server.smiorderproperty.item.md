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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675309"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="2f65c-102">Vlastnost SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="2f65c-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="2f65c-103">Získá pořadí sloupců pro entitu.</span><span class="sxs-lookup"><span data-stu-id="2f65c-103">Gets the column order for the entity.</span></span> <span data-ttu-id="2f65c-104">Sestavení, který obsahuje tato vlastnost má relaci typu friend s SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="2f65c-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="2f65c-105">Je určena pro použití systémem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f65c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="2f65c-106">U jiných databází pomocí mechanismu hostování poskytuje tuto databázi.</span><span class="sxs-lookup"><span data-stu-id="2f65c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f65c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f65c-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="2f65c-108">Hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2f65c-108">Property value</span></span>

<span data-ttu-id="2f65c-109">Pořadí sloupců.</span><span class="sxs-lookup"><span data-stu-id="2f65c-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f65c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f65c-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="2f65c-111">`SmiOrderProperty.Item` Vlastnost je interní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="2f65c-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2f65c-112">Microsoft nepodporuje použití této vlastnosti v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="2f65c-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f65c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f65c-113">Requirements</span></span>

<span data-ttu-id="2f65c-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="2f65c-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="2f65c-115">**Sestavení:** System.Data (v System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="2f65c-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="2f65c-116">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="2f65c-116">**.NET Framework versions:** Available since 2.0.</span></span>