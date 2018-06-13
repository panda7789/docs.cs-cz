---
title: ICorDebugThread::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 358597edc9fbc5203e5c00a5fb4d04019281060d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418269"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="38694-102">ICorDebugThread::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="38694-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="38694-103">Získá aktuální popisovač pro aktivní součástí této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="38694-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38694-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38694-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38694-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38694-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="38694-106">[out] Ukazatel HTHREAD, který je popisovač active součástí tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="38694-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38694-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38694-107">Remarks</span></span>  
 <span data-ttu-id="38694-108">Popisovač může změnit, protože proces provede a mohou být různé pro různé části vlákno.</span><span class="sxs-lookup"><span data-stu-id="38694-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="38694-109">Tento popisovač je vlastníkem rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="38694-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="38694-110">Ladicí program by měl duplicitní ho před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="38694-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38694-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38694-111">Requirements</span></span>  
 <span data-ttu-id="38694-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38694-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38694-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38694-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38694-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38694-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38694-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38694-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
