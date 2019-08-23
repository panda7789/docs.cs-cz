---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d896cc4316c2de6fa1cb0bacc9ff8b1f3713129
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967549"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="17552-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="17552-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="17552-103">Načte informace o spravovaném kódu na konkrétní kódové adrese.</span><span class="sxs-lookup"><span data-stu-id="17552-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17552-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17552-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17552-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="17552-106">pro Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která určuje počáteční adresu spravovaného segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="17552-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="17552-107">mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="17552-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17552-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17552-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17552-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="17552-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17552-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17552-110">Requirements</span></span>  
 <span data-ttu-id="17552-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17552-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17552-112">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="17552-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17552-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17552-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17552-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17552-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17552-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17552-115">See also</span></span>

- [<span data-ttu-id="17552-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17552-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="17552-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="17552-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
