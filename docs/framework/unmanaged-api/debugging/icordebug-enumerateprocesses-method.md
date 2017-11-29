---
title: "ICorDebug::EnumerateProcesses – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e48bc47945bc6c77758eeaa8597ad0ce57b72689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="a98fb-102">ICorDebug::EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="a98fb-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="a98fb-103">Získá enumerátor pro procesy, které se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="a98fb-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a98fb-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a98fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a98fb-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="a98fb-106">Ukazatel na adresu ICorDebugProcessEnum objekt, který je enumerátor pro procesy laděné.</span><span class="sxs-lookup"><span data-stu-id="a98fb-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a98fb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a98fb-107">Requirements</span></span>  
 <span data-ttu-id="a98fb-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a98fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a98fb-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a98fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a98fb-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a98fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a98fb-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a98fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98fb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a98fb-112">See Also</span></span>  
 [<span data-ttu-id="a98fb-113">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="a98fb-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
