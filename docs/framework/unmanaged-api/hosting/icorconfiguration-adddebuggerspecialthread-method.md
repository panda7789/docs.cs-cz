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
ms.openlocfilehash: 8b6593ad995872f0e0014b1e8bcd8a4b576bbeaf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762422"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="20224-102">ICorConfiguration::AddDebuggerSpecialThread – metoda</span><span class="sxs-lookup"><span data-stu-id="20224-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="20224-103">Označuje ladicí služby, že by mělo být povoleno pokračování v provádění určitého vlákna, zatímco ladicí program aplikace zastavil během spravovaných nebo nespravovaných scénářů ladění.</span><span class="sxs-lookup"><span data-stu-id="20224-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20224-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20224-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20224-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20224-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="20224-106">pro ID vlákna, které by mělo být povoleno pokračovat v provádění.</span><span class="sxs-lookup"><span data-stu-id="20224-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20224-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20224-107">Remarks</span></span>  
 <span data-ttu-id="20224-108">V zadaném vlákně nebude povoleno spustit spravovaný kód nebo zadat modul runtime jakýmkoli způsobem.</span><span class="sxs-lookup"><span data-stu-id="20224-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="20224-109">Příkladem takového vlákna by bylo vlákno v rámci procesu, které podporuje ladicí programy starších skriptů.</span><span class="sxs-lookup"><span data-stu-id="20224-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20224-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20224-110">Requirements</span></span>  
 <span data-ttu-id="20224-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20224-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20224-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20224-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20224-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20224-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20224-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20224-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20224-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="20224-115">See also</span></span>

- [<span data-ttu-id="20224-116">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20224-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
