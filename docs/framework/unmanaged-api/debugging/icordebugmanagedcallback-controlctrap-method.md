---
title: ICorDebugManagedCallback::ControlCTrap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 63f7bf8c09480b9ce2cfb8eb8dc66e4a6133ef8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777488"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="1ae9a-102">ICorDebugManagedCallback::ControlCTrap – metoda</span><span class="sxs-lookup"><span data-stu-id="1ae9a-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="1ae9a-103">Upozorní ladicí program, že kombinace kláves CTRL + C je zachycena v procesu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="1ae9a-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ae9a-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ae9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ae9a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="1ae9a-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém je nachycena kombinace kláves CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="1ae9a-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ae9a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ae9a-107">Return Value</span></span>  
  
|<span data-ttu-id="1ae9a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ae9a-108">HRESULT</span></span>|<span data-ttu-id="1ae9a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1ae9a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ae9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ae9a-110">S_OK</span></span>|<span data-ttu-id="1ae9a-111">Ladicí program zpracuje soutisk v kombinaci kláves CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="1ae9a-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="1ae9a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1ae9a-112">S_FALSE</span></span>|<span data-ttu-id="1ae9a-113">Ladicí program nebude zpracovávat depeši CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="1ae9a-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ae9a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ae9a-114">Remarks</span></span>  
 <span data-ttu-id="1ae9a-115">Všechny domény aplikace v rámci procesu jsou pro toto zpětné volání zastaveny.</span><span class="sxs-lookup"><span data-stu-id="1ae9a-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae9a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ae9a-116">Requirements</span></span>  
 <span data-ttu-id="1ae9a-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae9a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae9a-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ae9a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ae9a-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1ae9a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ae9a-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae9a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae9a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ae9a-121">See also</span></span>

- [<span data-ttu-id="1ae9a-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ae9a-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
