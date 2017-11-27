---
title: "ICorDebugRegisterSet2::GetRegistersAvailable – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="f3a1a-102">ICorDebugRegisterSet2::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="f3a1a-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="f3a1a-103">Získá pole bajtů, které poskytuje rastrový obrázek k dispozici registrů.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3a1a-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3a1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3a1a-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="f3a1a-106">[v] Velikost `availableRegChunks` pole.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="f3a1a-107">[out] Pole bajtů, každý bit odpovídá registraci.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="f3a1a-108">Pokud do registru je k dispozici, je nastavena odpovídající bit registru.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3a1a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3a1a-109">Remarks</span></span>  
 <span data-ttu-id="f3a1a-110">Zadejte hodnoty CorDebugRegister – výčet registry různé procesory.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="f3a1a-111">Horní pět bits každé hodnoty jsou indexem `availableRegChunks` pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="f3a1a-112">Nižší tři bits každou hodnotu identifikovat bit pozici v rámci indexované bajtů.</span><span class="sxs-lookup"><span data-stu-id="f3a1a-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="f3a1a-113">Vzhledem `CorDebugRegister` hodnotu, která určuje konkrétní registrace, pozice registru v maska je stanoven následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3a1a-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="f3a1a-114">Extrahování potřebné pro přístup k správné bajtů v indexu `availableRegChunks` pole:</span><span class="sxs-lookup"><span data-stu-id="f3a1a-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="f3a1a-115">`CorDebugRegister`Hodnota >> 3</span><span class="sxs-lookup"><span data-stu-id="f3a1a-115">`CorDebugRegister` value >> 3</span></span>  
  
2.  <span data-ttu-id="f3a1a-116">Extrahujte bit pozici v rámci indexované bajtů, kde je bit nula nejméně významný bit:</span><span class="sxs-lookup"><span data-stu-id="f3a1a-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="f3a1a-117">`CorDebugRegister`Hodnota & 7</span><span class="sxs-lookup"><span data-stu-id="f3a1a-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a1a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3a1a-118">Requirements</span></span>  
 <span data-ttu-id="f3a1a-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a1a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a1a-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3a1a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3a1a-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3a1a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a1a-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a1a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a1a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3a1a-123">See Also</span></span>  
 [<span data-ttu-id="f3a1a-124">ICorDebugRegisterSet2 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3a1a-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="f3a1a-125">ICorDebugRegisterSet – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3a1a-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
