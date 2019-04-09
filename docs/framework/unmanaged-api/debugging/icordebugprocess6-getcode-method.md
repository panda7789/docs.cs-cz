---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7349a20da35eb0b87894440026a0974d49ae2aa0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097288"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="73dd7-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="73dd7-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="73dd7-103">Získá informace o spravovaném kódu na adrese konkrétního kódu.</span><span class="sxs-lookup"><span data-stu-id="73dd7-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73dd7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73dd7-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73dd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73dd7-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="73dd7-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která určuje počáteční adresu segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="73dd7-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="73dd7-107">[out] Ukazatel na adresu "ICorDebugCode" objekt, který reprezentuje segment, který spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="73dd7-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73dd7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73dd7-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73dd7-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="73dd7-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73dd7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73dd7-110">Requirements</span></span>  
 <span data-ttu-id="73dd7-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73dd7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73dd7-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73dd7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73dd7-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73dd7-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="73dd7-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73dd7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73dd7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73dd7-115">See also</span></span>

- [<span data-ttu-id="73dd7-116">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="73dd7-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="73dd7-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73dd7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
