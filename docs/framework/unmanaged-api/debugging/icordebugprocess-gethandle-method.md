---
title: ICorDebugProcess::GetHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60bd7567f541a0bbaa3591d2f2905d13064dec3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423439"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="712b6-102">ICorDebugProcess::GetHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="712b6-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="712b6-103">Získá popisovač pro proces.</span><span class="sxs-lookup"><span data-stu-id="712b6-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="712b6-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="712b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="712b6-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="712b6-106">[out] Ukazatel na `HPROCESS` tedy popisovač proces.</span><span class="sxs-lookup"><span data-stu-id="712b6-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="712b6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="712b6-107">Remarks</span></span>  
 <span data-ttu-id="712b6-108">Vlastníkem načtené popisovač je rozhraní pro ladění.</span><span class="sxs-lookup"><span data-stu-id="712b6-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="712b6-109">Ladicí program by měl duplicitní popisovač před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="712b6-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="712b6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="712b6-110">Requirements</span></span>  
 <span data-ttu-id="712b6-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712b6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712b6-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="712b6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="712b6-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="712b6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="712b6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712b6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
