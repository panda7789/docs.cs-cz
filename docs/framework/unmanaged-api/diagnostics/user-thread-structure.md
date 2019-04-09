---
title: USER_THREAD – struktura
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11551221732e454e48111d48d60ca9b72f7f9b66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127152"
---
# <a name="userthread-structure"></a><span data-ttu-id="e11f5-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="e11f5-102">USER_THREAD Structure</span></span>
<span data-ttu-id="e11f5-103">Poskytuje informace o vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e11f5-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="e11f5-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e11f5-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e11f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e11f5-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="e11f5-106">Členové</span><span class="sxs-lookup"><span data-stu-id="e11f5-106">Members</span></span>  
  
|<span data-ttu-id="e11f5-107">Člen</span><span class="sxs-lookup"><span data-stu-id="e11f5-107">Member</span></span>|<span data-ttu-id="e11f5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e11f5-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="e11f5-109">Adresa vyrovnávací paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="e11f5-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="e11f5-110">Délka vyrovnávací paměti vlákna, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e11f5-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="e11f5-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="e11f5-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e11f5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e11f5-112">Requirements</span></span>  
 <span data-ttu-id="e11f5-113">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e11f5-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11f5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e11f5-114">See also</span></span>

- [<span data-ttu-id="e11f5-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="e11f5-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="e11f5-116">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e11f5-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
