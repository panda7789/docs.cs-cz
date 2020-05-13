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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378210"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="56242-102">ICorDebugRegisterSet2::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="56242-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="56242-103">Získá pole bajtů, které poskytuje rastrový obrázek dostupných registrů.</span><span class="sxs-lookup"><span data-stu-id="56242-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56242-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56242-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56242-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="56242-106">pro Velikost `availableRegChunks` pole.</span><span class="sxs-lookup"><span data-stu-id="56242-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="56242-107">mimo Pole bajtů, každý bit, který odpovídá registru.</span><span class="sxs-lookup"><span data-stu-id="56242-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="56242-108">Pokud je k dispozici registr, je nastaven odpovídající bit registru.</span><span class="sxs-lookup"><span data-stu-id="56242-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56242-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56242-109">Remarks</span></span>  
 <span data-ttu-id="56242-110">Hodnoty výčtu CorDebugRegister – určují Registry různých mikroprocesorů.</span><span class="sxs-lookup"><span data-stu-id="56242-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="56242-111">Horních pět bitů každé hodnoty je index `availableRegChunks` pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="56242-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="56242-112">Dolní tři bity každé hodnoty identifikují bitovou pozici v rámci indexovaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="56242-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="56242-113">Vzhledem k `CorDebugRegister` hodnotě, která určuje konkrétní registr, je pozice registru v masce určena následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="56242-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="56242-114">Extrahujte index potřebný pro přístup ke správnému bajtu v `availableRegChunks` poli:</span><span class="sxs-lookup"><span data-stu-id="56242-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="56242-115">`CorDebugRegister`hodnota >> 3</span><span class="sxs-lookup"><span data-stu-id="56242-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="56242-116">Extrahuje bitovou pozici v indexovaném bajtu, kde hodnota bitu nula je nejméně významnou bitovou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="56242-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="56242-117">`CorDebugRegister`hodnota & 7</span><span class="sxs-lookup"><span data-stu-id="56242-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56242-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56242-118">Requirements</span></span>  
 <span data-ttu-id="56242-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56242-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56242-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="56242-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56242-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="56242-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56242-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56242-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56242-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="56242-123">See also</span></span>

- [<span data-ttu-id="56242-124">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56242-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="56242-125">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56242-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
