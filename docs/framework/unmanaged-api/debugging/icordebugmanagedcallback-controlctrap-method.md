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
ms.openlocfilehash: 33a68d11a8d17e46533b4f83bbf87aafe171e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212396"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="06a60-102">ICorDebugManagedCallback::ControlCTrap – metoda</span><span class="sxs-lookup"><span data-stu-id="06a60-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="06a60-103">Upozorní ladicí program, že kombinace kláves CTRL + C je zachycena v procesu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="06a60-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06a60-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06a60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06a60-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="06a60-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém je nachycena kombinace kláves CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="06a60-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06a60-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06a60-107">Return Value</span></span>  
  
|<span data-ttu-id="06a60-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06a60-108">HRESULT</span></span>|<span data-ttu-id="06a60-109">Popis</span><span class="sxs-lookup"><span data-stu-id="06a60-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06a60-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="06a60-110">S_OK</span></span>|<span data-ttu-id="06a60-111">Ladicí program zpracuje soutisk v kombinaci kláves CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="06a60-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="06a60-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="06a60-112">S_FALSE</span></span>|<span data-ttu-id="06a60-113">Ladicí program nebude zpracovávat depeši CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="06a60-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06a60-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06a60-114">Remarks</span></span>  
 <span data-ttu-id="06a60-115">Všechny domény aplikace v rámci procesu jsou pro toto zpětné volání zastaveny.</span><span class="sxs-lookup"><span data-stu-id="06a60-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06a60-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06a60-116">Requirements</span></span>  
 <span data-ttu-id="06a60-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06a60-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06a60-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06a60-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06a60-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06a60-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06a60-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06a60-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a60-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="06a60-121">See also</span></span>

- [<span data-ttu-id="06a60-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06a60-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
