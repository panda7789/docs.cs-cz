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
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609440"
---
# <a name="user_thread-structure"></a><span data-ttu-id="db96d-102">USER_THREAD – struktura</span><span class="sxs-lookup"><span data-stu-id="db96d-102">USER_THREAD Structure</span></span>
<span data-ttu-id="db96d-103">Poskytuje informace ladicímu programu o vlákně.</span><span class="sxs-lookup"><span data-stu-id="db96d-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="db96d-104">Další informace naleznete v tématu metoda [INotifySource2 –:: setnotifyfilter –](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="db96d-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db96d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db96d-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="db96d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="db96d-106">Members</span></span>  
  
|<span data-ttu-id="db96d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="db96d-107">Member</span></span>|<span data-ttu-id="db96d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="db96d-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="db96d-109">Adresa vyrovnávací paměti vlákna.</span><span class="sxs-lookup"><span data-stu-id="db96d-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="db96d-110">Délka vyrovnávací paměti vlákna (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="db96d-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="db96d-111">ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="db96d-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db96d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db96d-112">Requirements</span></span>  
 <span data-ttu-id="db96d-113">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="db96d-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db96d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="db96d-114">See also</span></span>

- [<span data-ttu-id="db96d-115">SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="db96d-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="db96d-116">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="db96d-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
