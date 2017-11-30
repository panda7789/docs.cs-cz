---
title: Connection.m_WriteList pole
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.Connection.m_WriteList
api_location: System.dll
api_type: Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 66454f2a165048b234dad680c6b66c6fd04bd2e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="e2004-102">Connection.m\_WriteList pole</span><span class="sxs-lookup"><span data-stu-id="e2004-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="e2004-103">`Connection.m_WriteList`je <xref:System.Collections.ArrayList> z <xref:System.Net.HttpWebRequest> objekty, které jsou zařazeny do fronty v odesílání prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2004-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2004-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2004-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="e2004-105">`Connection.m_WriteList` Pole je privátní a nejsou určeny pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="e2004-105">The `Connection.m_WriteList` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="e2004-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="e2004-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2004-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2004-107">Requirements</span></span>

<span data-ttu-id="e2004-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e2004-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e2004-109">**Sestavení:** systému (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="e2004-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e2004-110">**Verze rozhraní .NET framework:** dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e2004-110">**.NET Framework versions:** Available since 2.0.</span></span>
