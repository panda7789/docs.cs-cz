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
ms.openlocfilehash: 00c9939b25f395010f6ea5832b405c3e9928a223
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792028"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="35018-102">ICorDebugRegisterSet2::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="35018-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="35018-103">Získá pole bajtů, které poskytuje rastrový obrázek dostupných registrů.</span><span class="sxs-lookup"><span data-stu-id="35018-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35018-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35018-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35018-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35018-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="35018-106">pro Velikost pole `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="35018-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="35018-107">mimo Pole bajtů, každý bit, který odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="35018-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="35018-108">Pokud je k dispozici registr, je nastaven odpovídající bit registru.</span><span class="sxs-lookup"><span data-stu-id="35018-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35018-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35018-109">Remarks</span></span>  
 <span data-ttu-id="35018-110">Hodnoty výčtu CorDebugRegister – určují Registry různých mikroprocesorů.</span><span class="sxs-lookup"><span data-stu-id="35018-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="35018-111">Horních pět bitů každé hodnoty je index v `availableRegChunks` poli bajtů.</span><span class="sxs-lookup"><span data-stu-id="35018-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="35018-112">Dolní tři bity každé hodnoty identifikují bitovou pozici v rámci indexovaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="35018-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="35018-113">Vzhledem k hodnotě `CorDebugRegister`, která určuje konkrétní registr, je pozice registru v masce určena následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="35018-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="35018-114">Extrahujte index potřebný pro přístup ke správnému bajtu v `availableRegChunks` poli:</span><span class="sxs-lookup"><span data-stu-id="35018-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="35018-115">hodnota `CorDebugRegister` > > 3</span><span class="sxs-lookup"><span data-stu-id="35018-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="35018-116">Extrahuje bitovou pozici v indexovaném bajtu, kde hodnota bitu nula je nejméně významnou bitovou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="35018-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="35018-117">hodnota `CorDebugRegister` & 7</span><span class="sxs-lookup"><span data-stu-id="35018-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35018-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35018-118">Requirements</span></span>  
 <span data-ttu-id="35018-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35018-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35018-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35018-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35018-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35018-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35018-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35018-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35018-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35018-123">See also</span></span>

- [<span data-ttu-id="35018-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35018-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="35018-125">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35018-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
