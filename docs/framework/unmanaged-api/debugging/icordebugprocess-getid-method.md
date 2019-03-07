---
title: ICorDebugProcess::GetID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9239ccfe8ce08e5b50b762a6fede11ab8a439b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495712"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="60f90-102">ICorDebugProcess::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="60f90-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="60f90-103">Získá ID operačního systému (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="60f90-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f90-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60f90-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="60f90-106">[out] Jedinečné ID procesu.</span><span class="sxs-lookup"><span data-stu-id="60f90-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f90-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60f90-107">Requirements</span></span>  
 <span data-ttu-id="60f90-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f90-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f90-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60f90-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60f90-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60f90-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60f90-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f90-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
