---
title: CALL_ID – struktura
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448593"
---
# <a name="call_id-structure"></a><span data-ttu-id="f9dda-102">CALL_ID – struktura</span><span class="sxs-lookup"><span data-stu-id="f9dda-102">CALL_ID Structure</span></span>
<span data-ttu-id="f9dda-103">Poskytuje informace ladicímu programu o funkci, která je volána.</span><span class="sxs-lookup"><span data-stu-id="f9dda-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="f9dda-104">Další informace najdete v rozhraní [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f9dda-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dda-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9dda-105">Syntax</span></span>  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="f9dda-106">Členové</span><span class="sxs-lookup"><span data-stu-id="f9dda-106">Members</span></span>  
  
|<span data-ttu-id="f9dda-107">Člen</span><span class="sxs-lookup"><span data-stu-id="f9dda-107">Member</span></span>|<span data-ttu-id="f9dda-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f9dda-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="f9dda-109">Identifikuje počítač, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="f9dda-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="f9dda-110">Identifikuje procesor počítače.</span><span class="sxs-lookup"><span data-stu-id="f9dda-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="f9dda-111">Identifikuje vlákno, které provádí volání.</span><span class="sxs-lookup"><span data-stu-id="f9dda-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="f9dda-112">Určuje adresu zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="f9dda-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="f9dda-113">Určuje adresu volání.</span><span class="sxs-lookup"><span data-stu-id="f9dda-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="f9dda-114">Identifikuje počítač, který spustí volání.</span><span class="sxs-lookup"><span data-stu-id="f9dda-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9dda-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9dda-115">Requirements</span></span>  
 <span data-ttu-id="f9dda-116">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="f9dda-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dda-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9dda-117">See also</span></span>

- [<span data-ttu-id="f9dda-118">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9dda-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="f9dda-119">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f9dda-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
