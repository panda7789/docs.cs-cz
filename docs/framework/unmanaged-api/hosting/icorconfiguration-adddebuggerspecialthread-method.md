---
title: "ICorConfiguration::AddDebuggerSpecialThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.AddDebuggerSpecialThread
api_location: mscoree.dll
api_type: COM
f1_keywords: AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2041a45cb80a08b2322f23e820f89b4bb71f845
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="d3e25-102">ICorConfiguration::AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="d3e25-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="d3e25-103">K ladění služby označuje, že konkrétní vlákno by měl povolit chcete pokračovat v provádění ladicí program se zastavila během ladění scénáře spravované nebo nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3e25-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e25-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3e25-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="d3e25-106">[v] ID podprocesu, který má být povoleno se pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="d3e25-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3e25-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3e25-107">Remarks</span></span>  
 <span data-ttu-id="d3e25-108">Zadaný vlákno nebude možné spustit spravovaného kódu nebo modul runtime zadejte žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d3e25-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="d3e25-109">Příkladem takových vlákna by přístup z více vláken v procesu pro podporu ladicí programy starší verze skriptu.</span><span class="sxs-lookup"><span data-stu-id="d3e25-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3e25-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3e25-110">Requirements</span></span>  
 <span data-ttu-id="d3e25-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e25-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e25-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3e25-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3e25-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3e25-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3e25-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e25-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e25-115">See Also</span></span>  
 [<span data-ttu-id="d3e25-116">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3e25-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
