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
ms.openlocfilehash: ab2121605f974fdf3f9053214a4d29d8b0dd72db
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210777"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="cf059-102">ICorDebugProcess::IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="cf059-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="cf059-103">Získá hodnotu, která označuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="cf059-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf059-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf059-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf059-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf059-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cf059-106">pro `CORDB_ADDRESS`Hodnota, která určuje konkrétní adresu.</span><span class="sxs-lookup"><span data-stu-id="cf059-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="cf059-107">mimo Ukazatel na logickou hodnotu, která je `true` v případě, že zadaná adresa je uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu; v opačném případě \* `pbTransitionStub` je `false` .</span><span class="sxs-lookup"><span data-stu-id="cf059-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf059-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf059-108">Remarks</span></span>  
 <span data-ttu-id="cf059-109">`IsTransitionStub`Metoda může být použita nespravovaným kódem krokování k rozhodnutí, kdy vrátit řízení krokování spravovanému stepper.</span><span class="sxs-lookup"><span data-stu-id="cf059-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="cf059-110">Pomocí informací v přenositelném spustitelném souboru (PE) můžete také převést zástupné procedury pro převod identity.</span><span class="sxs-lookup"><span data-stu-id="cf059-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf059-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf059-111">Requirements</span></span>  
 <span data-ttu-id="cf059-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf059-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf059-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf059-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf059-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf059-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf059-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf059-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
