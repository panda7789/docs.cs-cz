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
ms.openlocfilehash: 2d5b07acb9dc374fdd8872ed982a92171da28603
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137236"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="266b1-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="266b1-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="266b1-103">Získá aktuální nastavení příznaku kompilátoru, které modul CLR (Common Language Runtime) používá k výběru správného předkompilovaného (nativně) image, která se má načíst do tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="266b1-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="266b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="266b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="266b1-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="266b1-106">mimo Ukazatel na bitovou kombinaci hodnot výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) , které se používají k výběru správné předkompilované image, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="266b1-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="266b1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="266b1-107">Remarks</span></span>  
 <span data-ttu-id="266b1-108">Použijte metodu [ICorDebugProcess2:: SetDesiredNGENCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) k nastavení příznaků, které bude modul CLR používat k výběru správné předkompilované bitové kopie, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="266b1-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="266b1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="266b1-109">Requirements</span></span>  
 <span data-ttu-id="266b1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="266b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="266b1-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="266b1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="266b1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="266b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="266b1-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="266b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
