---
title: ICorConfiguration::AddDebuggerSpecialThread – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1b19c1499f7e8a126933b4d0635a0ab73e72a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218586"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="512c2-102">ICorConfiguration::AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="512c2-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="512c2-103">Ladění služeb označuje, že konkrétní vlákno by měla být povolena má pokračovat provedením zatímco ladicí program zastavuje během scénáře ladění spravované nebo nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="512c2-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="512c2-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="512c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="512c2-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="512c2-106">[in] ID vlákna, která by měla bude moct pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="512c2-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="512c2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="512c2-107">Remarks</span></span>  
 <span data-ttu-id="512c2-108">Zadané vlákno nebude moci spouštět spravovaný kód nebo zadejte modul runtime žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="512c2-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="512c2-109">Příkladem takových vlákno může být vlákno v procesu pro podporu ladicí programy starší verzi skriptu.</span><span class="sxs-lookup"><span data-stu-id="512c2-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="512c2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="512c2-110">Requirements</span></span>  
 <span data-ttu-id="512c2-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512c2-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="512c2-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="512c2-113">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="512c2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="512c2-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512c2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="512c2-115">See also</span></span>

- [<span data-ttu-id="512c2-116">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="512c2-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
