---
title: "ICoreClrDebugTarget::FreeMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreDebugTarget.FreeMemory
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7b199d3a3406a1a1dd21a560424ef342b03ce6c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="15878-102">ICoreClrDebugTarget::FreeMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="15878-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="15878-103">Uvolní paměti přidělené [icoreclrdebugtarget::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) a [icoreclrdebugtarget::enumruntimes –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="15878-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15878-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15878-104">Syntax</span></span>  
  
```  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15878-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15878-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="15878-106">[v] Ukazatel na pole, které se vrátí, a to buď [icoreclrdebugtarget::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) nebo [icoreclrdebugtarget::enumruntimes –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="15878-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15878-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15878-107">Requirements</span></span>  
 <span data-ttu-id="15878-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15878-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15878-109">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="15878-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="15878-110">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="15878-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="15878-111">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="15878-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15878-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="15878-112">See Also</span></span>  
 [<span data-ttu-id="15878-113">ICoreClrDebugTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15878-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
