---
title: ICorDebugGenericValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209783"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="4b8cb-102">ICorDebugGenericValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b8cb-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="4b8cb-103">Podtřída "ICorDebugValue", která se vztahuje na všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="4b8cb-104">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b8cb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4b8cb-105">Methods</span></span>  
  
|<span data-ttu-id="4b8cb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b8cb-106">Method</span></span>|<span data-ttu-id="4b8cb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4b8cb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b8cb-108">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="4b8cb-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="4b8cb-109">Zkopíruje hodnotu do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="4b8cb-110">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="4b8cb-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="4b8cb-111">Zkopíruje novou hodnotu ze zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b8cb-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b8cb-112">Remarks</span></span>  
 <span data-ttu-id="4b8cb-113">`ICorDebugGenericValue`je dílčí rozhraní, protože se nejedná o nevzdáleněu.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="4b8cb-114">U typů odkazů je hodnota odkaz spíše než obsah odkazu.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="4b8cb-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b8cb-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4b8cb-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8cb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b8cb-117">Requirements</span></span>  
 <span data-ttu-id="4b8cb-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b8cb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8cb-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b8cb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b8cb-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b8cb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8cb-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8cb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8cb-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b8cb-122">See also</span></span>

- [<span data-ttu-id="4b8cb-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b8cb-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
