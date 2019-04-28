---
title: ConnectionGroup.m_ConnectionList pole
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
author: guardrex
ms.author: mairaw
ms.openlocfilehash: c9162e123c1167e3aa1be26ddd37279c088acc89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675296"
---
# <a name="connectiongroupmconnectionlist-field"></a><span data-ttu-id="482a1-102">ConnectionGroup.m\_ConnectionList pole</span><span class="sxs-lookup"><span data-stu-id="482a1-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="482a1-103">`ConnectionGroup.m_ConnectionList` je <xref:System.Collections.ArrayList> připojení objektů, které používají stejný identifikátor URI a sdílené složky na stejné hodnoty pro některé vlastnosti, jako jsou vypršení platnosti a ověřování.</span><span class="sxs-lookup"><span data-stu-id="482a1-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="482a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="482a1-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="482a1-105">`ConnectionGroup.m_ConnectionList` Pole je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="482a1-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="482a1-106">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="482a1-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="482a1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="482a1-107">Requirements</span></span>

<span data-ttu-id="482a1-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="482a1-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="482a1-109">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="482a1-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="482a1-110">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="482a1-110">**.NET Framework versions:** Available since 2.0.</span></span>
