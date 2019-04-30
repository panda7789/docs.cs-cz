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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775515"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="09af9-102">ICorDebugProcess::IsTransitionStub – metoda</span><span class="sxs-lookup"><span data-stu-id="09af9-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="09af9-103">Získá hodnotu, která určuje, zda je adresa uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="09af9-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09af9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09af9-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09af9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09af9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="09af9-106">[in] A `CORDB_ADDRESS` hodnotu, která určuje dotyčný adresu.</span><span class="sxs-lookup"><span data-stu-id="09af9-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="09af9-107">[out] Ukazatel na logickou hodnotu, která je `true` Pokud zadaná adresa je uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód; v opačném případě \*`pbTransitionStub` je `false`.</span><span class="sxs-lookup"><span data-stu-id="09af9-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09af9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09af9-108">Remarks</span></span>  
 <span data-ttu-id="09af9-109">`IsTransitionStub` Metoda umožňuje nespravovaným krokování kódem při rozhodování, kdy se vraťte do spravované krokovač krokování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="09af9-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="09af9-110">Můžete také zástupné procedury přechod identity zobrazením informací do přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="09af9-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09af9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09af9-111">Requirements</span></span>  
 <span data-ttu-id="09af9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09af9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09af9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09af9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09af9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09af9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09af9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09af9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
