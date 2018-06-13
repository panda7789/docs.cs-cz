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
ms.openlocfilehash: 5844f8d63aa5646bfd7860dc0407528fb2eaf329
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753336"
---
# <a name="connectiongroupmconnectionlist-field"></a><span data-ttu-id="265c7-102">ConnectionGroup.m\_ConnectionList pole</span><span class="sxs-lookup"><span data-stu-id="265c7-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="265c7-103">`ConnectionGroup.m_ConnectionList` je <xref:System.Collections.ArrayList> připojení objektů, které slouží se identifikátor URI a sdílení stejné hodnoty pro některé další vlastnosti, jako třeba vypršení platnosti a ověřování.</span><span class="sxs-lookup"><span data-stu-id="265c7-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="265c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="265c7-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="265c7-105">`ConnectionGroup.m_ConnectionList` Pole je privátní a nejsou určeny pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="265c7-105">The `ConnectionGroup.m_ConnectionList` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="265c7-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="265c7-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="265c7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="265c7-107">Requirements</span></span>

<span data-ttu-id="265c7-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="265c7-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="265c7-109">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="265c7-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="265c7-110">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="265c7-110">**.NET Framework versions:** Available since 2.0.</span></span>
