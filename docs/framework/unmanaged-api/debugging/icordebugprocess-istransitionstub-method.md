---
title: ICorDebugProcess::IsTransitionStub – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139384"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="9f848-102">ICorDebugProcess::IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="9f848-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="9f848-103">Získá hodnotu, která označuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="9f848-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f848-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f848-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f848-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f848-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9f848-106">pro Hodnota `CORDB_ADDRESS`, která určuje konkrétní adresu.</span><span class="sxs-lookup"><span data-stu-id="9f848-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="9f848-107">mimo Ukazatel na logickou hodnotu, která je `true`, pokud je zadaná adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu; v opačném případě \*`pbTransitionStub` `false`.</span><span class="sxs-lookup"><span data-stu-id="9f848-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f848-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f848-108">Remarks</span></span>  
 <span data-ttu-id="9f848-109">Metodu `IsTransitionStub` lze použít nespravovaným kódem krokování k rozhodnutí, kdy vrátit řízení krokování spravovanému stepper.</span><span class="sxs-lookup"><span data-stu-id="9f848-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="9f848-110">Pomocí informací v přenositelném spustitelném souboru (PE) můžete také převést zástupné procedury pro převod identity.</span><span class="sxs-lookup"><span data-stu-id="9f848-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f848-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f848-111">Requirements</span></span>  
 <span data-ttu-id="9f848-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f848-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f848-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f848-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f848-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9f848-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f848-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f848-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
