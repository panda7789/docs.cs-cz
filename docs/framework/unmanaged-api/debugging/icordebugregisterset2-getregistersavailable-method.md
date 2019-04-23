---
title: ICorDebugRegisterSet2::GetRegistersAvailable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1522d643a69c47eec03770a8f51756dd4250075a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309417"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="b75bf-102">ICorDebugRegisterSet2::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="b75bf-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="b75bf-103">Získá pole bajtů, která poskytuje rastrový obrázek do dostupných registrů.</span><span class="sxs-lookup"><span data-stu-id="b75bf-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b75bf-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75bf-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="b75bf-106">[in] Velikost `availableRegChunks` pole.</span><span class="sxs-lookup"><span data-stu-id="b75bf-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="b75bf-107">[out] Pole bajtů, každý bit odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="b75bf-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="b75bf-108">Pokud je k dispozici registru, odpovídající bit do registru je nastavena.</span><span class="sxs-lookup"><span data-stu-id="b75bf-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b75bf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b75bf-109">Remarks</span></span>  
 <span data-ttu-id="b75bf-110">Hodnoty cordebugregister – výčet zadejte registrů různých mikroprocesory.</span><span class="sxs-lookup"><span data-stu-id="b75bf-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="b75bf-111">Horní pět bitů jednotlivé hodnoty jsou index do `availableRegChunks` pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="b75bf-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="b75bf-112">Nižší tři bity každé hodnoty identifikovat bitová pozice v rámci indexované bajtů.</span><span class="sxs-lookup"><span data-stu-id="b75bf-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="b75bf-113">Zadaný `CorDebugRegister` hodnota, která určuje konkrétní registru do registru pozice v maska je stanoven následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b75bf-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="b75bf-114">Rozbalte potřebné pro přístup ke správné bajt v indexu `availableRegChunks` pole:</span><span class="sxs-lookup"><span data-stu-id="b75bf-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="b75bf-115">`CorDebugRegister` Hodnota >> 3</span><span class="sxs-lookup"><span data-stu-id="b75bf-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="b75bf-116">Extrahujte bitové pozice v indexovaných byte, kde bit nula je nejméně významných bitů:</span><span class="sxs-lookup"><span data-stu-id="b75bf-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="b75bf-117">`CorDebugRegister` Hodnota & 7</span><span class="sxs-lookup"><span data-stu-id="b75bf-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75bf-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b75bf-118">Requirements</span></span>  
 <span data-ttu-id="b75bf-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75bf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75bf-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b75bf-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b75bf-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b75bf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b75bf-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b75bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75bf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b75bf-123">See also</span></span>

- [<span data-ttu-id="b75bf-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b75bf-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="b75bf-125">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b75bf-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
