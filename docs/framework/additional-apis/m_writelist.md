---
title: Connection.m_WriteList pole
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d138e0490e849ff26f540077ec7d23ae42737606
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300912"
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="45cd8-102">Connection.m\_WriteList pole</span><span class="sxs-lookup"><span data-stu-id="45cd8-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="45cd8-103">`Connection.m_WriteList` je <xref:System.Collections.ArrayList> z <xref:System.Net.HttpWebRequest> objekty, které jsou zařazeny do odešlou přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="45cd8-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="45cd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45cd8-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="45cd8-105">`Connection.m_WriteList` Pole je privátní a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="45cd8-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="45cd8-106">Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="45cd8-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="45cd8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45cd8-107">Requirements</span></span>

<span data-ttu-id="45cd8-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="45cd8-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="45cd8-109">**Sestavení:** Systém (System.dll)</span><span class="sxs-lookup"><span data-stu-id="45cd8-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="45cd8-110">**Verze rozhraní .NET framework:** Dostupné od verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="45cd8-110">**.NET Framework versions:** Available since 2.0.</span></span>
