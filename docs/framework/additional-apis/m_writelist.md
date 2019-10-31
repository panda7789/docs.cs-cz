---
title: Connection. m_WriteList – pole
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9760e301e25bc6e69ab22b563894cb079a8d58bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120030"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="30bcb-102">Connection. m\_pole WriteList</span><span class="sxs-lookup"><span data-stu-id="30bcb-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="30bcb-103">`Connection.m_WriteList` je <xref:System.Collections.ArrayList> objektů <xref:System.Net.HttpWebRequest>, které jsou zařazeny do fronty, aby byly odesílány prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="30bcb-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="30bcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30bcb-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="30bcb-105">Pole `Connection.m_WriteList` je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="30bcb-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="30bcb-106">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="30bcb-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="30bcb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30bcb-107">Requirements</span></span>

<span data-ttu-id="30bcb-108">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="30bcb-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="30bcb-109">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="30bcb-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="30bcb-110">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="30bcb-110">**.NET Framework versions:** Available since 2.0.</span></span>
