---
title: Connection. m_WriteList – pole
description: Získat informace o připojení. m_WriteList pole v .NET. Toto pole ArrayList obsahuje objekty HttpWebRequest, které jsou zařazeny do fronty k odeslání prostřednictvím protokolu HTTP.
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
ms.openlocfilehash: a627cb062036e3ab098c2d6e97f9a77ebfa75a33
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989597"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="373c4-104">Pole Connection. m \_ WriteList</span><span class="sxs-lookup"><span data-stu-id="373c4-104">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="373c4-105">`Connection.m_WriteList`je <xref:System.Collections.ArrayList> <xref:System.Net.HttpWebRequest> objekty, které jsou zařazeny do fronty k odeslání prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="373c4-105">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="373c4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="373c4-106">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="373c4-107">`Connection.m_WriteList`Pole je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="373c4-107">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="373c4-108">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="373c4-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="373c4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="373c4-109">Requirements</span></span>

<span data-ttu-id="373c4-110">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="373c4-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="373c4-111">**Sestavení:** Systém (v System.dll)</span><span class="sxs-lookup"><span data-stu-id="373c4-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="373c4-112">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="373c4-112">**.NET Framework versions:** Available since 2.0.</span></span>
