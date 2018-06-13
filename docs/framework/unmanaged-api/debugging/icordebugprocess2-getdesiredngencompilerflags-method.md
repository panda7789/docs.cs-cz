---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77ffb53e3a2b3802d3fcc1319397c8f51c5b127c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416108"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="14333-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="14333-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="14333-103">Získá aktuální kompilátoru příznak nastavení, které modul CLR (CLR) používá k výběru správné předkompilovaných (tedy nativní) obrázek, který má být načtena do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="14333-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14333-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14333-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14333-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14333-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="14333-106">[out] Ukazatel na bitovou kombinaci [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu, které jsou použity k výběru správné předkompilovaných bitové kopie má být načten.</span><span class="sxs-lookup"><span data-stu-id="14333-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14333-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14333-107">Remarks</span></span>  
 <span data-ttu-id="14333-108">Použít [icordebugprocess2::setdesiredngencompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) metodu a nastavit příznaky, které modul CLR bude používat k výběr správné bitové kopie předem kompilovaném načíst.</span><span class="sxs-lookup"><span data-stu-id="14333-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14333-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14333-109">Requirements</span></span>  
 <span data-ttu-id="14333-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14333-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14333-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14333-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14333-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14333-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14333-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14333-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
