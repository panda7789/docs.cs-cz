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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769508"
---
# <a name="callid-structure"></a><span data-ttu-id="9928c-102">CALL_ID – struktura</span><span class="sxs-lookup"><span data-stu-id="9928c-102">CALL_ID Structure</span></span>
<span data-ttu-id="9928c-103">Poskytuje informace o ladicím programu o funkci, která je volána.</span><span class="sxs-lookup"><span data-stu-id="9928c-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="9928c-104">Zobrazit [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) rozhraní pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9928c-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9928c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9928c-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9928c-106">Členové</span><span class="sxs-lookup"><span data-stu-id="9928c-106">Members</span></span>  
  
|<span data-ttu-id="9928c-107">Člen</span><span class="sxs-lookup"><span data-stu-id="9928c-107">Member</span></span>|<span data-ttu-id="9928c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9928c-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="9928c-109">Identifikuje počítač, který provádí volání.</span><span class="sxs-lookup"><span data-stu-id="9928c-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="9928c-110">Určuje procesor počítače.</span><span class="sxs-lookup"><span data-stu-id="9928c-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="9928c-111">Identifikuje vlákna, která provádí volání.</span><span class="sxs-lookup"><span data-stu-id="9928c-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="9928c-112">Určuje adresu zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="9928c-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="9928c-113">Určuje adresu volání.</span><span class="sxs-lookup"><span data-stu-id="9928c-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="9928c-114">Identifikuje počítač, který provede volání.</span><span class="sxs-lookup"><span data-stu-id="9928c-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9928c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9928c-115">Requirements</span></span>  
 <span data-ttu-id="9928c-116">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9928c-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9928c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9928c-117">See also</span></span>

- [<span data-ttu-id="9928c-118">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9928c-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="9928c-119">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="9928c-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
