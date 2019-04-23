---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7349a20da35eb0b87894440026a0974d49ae2aa0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097288"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="16642-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="16642-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="16642-103">Získá informace o spravovaném kódu na adrese konkrétního kódu.</span><span class="sxs-lookup"><span data-stu-id="16642-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16642-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16642-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16642-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16642-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="16642-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která určuje počáteční adresu segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="16642-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="16642-107">[out] Ukazatel na adresu "ICorDebugCode" objekt, který reprezentuje segment, který spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="16642-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16642-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16642-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16642-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16642-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16642-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16642-110">Requirements</span></span>  
 <span data-ttu-id="16642-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16642-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16642-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16642-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16642-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16642-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16642-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16642-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16642-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16642-115">See also</span></span>

- [<span data-ttu-id="16642-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16642-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="16642-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="16642-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
