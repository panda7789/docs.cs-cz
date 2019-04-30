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
ms.openlocfilehash: a59067f72005e87152680e4f990fc74e4acdaa9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948912"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="99a5b-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="99a5b-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="99a5b-103">Získá aktuální kompilátoru nastavením příznaků, které common language runtime (CLR) používá k výběru správné předkompilované (to znamená, nativní) image se v tomto procesu načten.</span><span class="sxs-lookup"><span data-stu-id="99a5b-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99a5b-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99a5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99a5b-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="99a5b-106">[out] Ukazatel na bitová kombinace hodnot [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) hodnot výčtu, která se používají k výběru správné předkompilované bitové kopie, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="99a5b-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99a5b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99a5b-107">Remarks</span></span>  
 <span data-ttu-id="99a5b-108">Použít [icordebugprocess2::setdesiredngencompilerflags –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) metody nastavte příznaky, které modul CLR bude používat k výběru správné předem kompilovaných bitové kopie k načtení.</span><span class="sxs-lookup"><span data-stu-id="99a5b-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a5b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99a5b-109">Requirements</span></span>  
 <span data-ttu-id="99a5b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99a5b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99a5b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99a5b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99a5b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99a5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99a5b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a5b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
