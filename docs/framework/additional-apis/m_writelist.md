---
title: Pole Connection.m_WriteList
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
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155834"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="dcdda-102">Pole Connection.m\_WriteList</span><span class="sxs-lookup"><span data-stu-id="dcdda-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="dcdda-103">`Connection.m_WriteList`je <xref:System.Collections.ArrayList> objekty, <xref:System.Net.HttpWebRequest> které jsou zařazeny do fronty k odeslání přes PROTOKOL HTTP.</span><span class="sxs-lookup"><span data-stu-id="dcdda-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="dcdda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdda-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="dcdda-105">Pole `Connection.m_WriteList` je soukromé a není určeno k použití přímo ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="dcdda-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dcdda-106">Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikaci za žádných okolností.</span><span class="sxs-lookup"><span data-stu-id="dcdda-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcdda-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdda-107">Requirements</span></span>

<span data-ttu-id="dcdda-108">**Obor názvů:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dcdda-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dcdda-109">**Sestava:** Systém (v souboru System.dll)</span><span class="sxs-lookup"><span data-stu-id="dcdda-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="dcdda-110">**Verze rozhraní .NET Framework:** K dispozici od 2.0.</span><span class="sxs-lookup"><span data-stu-id="dcdda-110">**.NET Framework versions:** Available since 2.0.</span></span>
