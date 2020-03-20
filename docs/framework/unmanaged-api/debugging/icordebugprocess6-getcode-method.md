---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178560"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="37fb0-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="37fb0-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="37fb0-103">Získá informace o spravovaném kódu na konkrétní adresu kódu.</span><span class="sxs-lookup"><span data-stu-id="37fb0-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37fb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37fb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37fb0-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="37fb0-106">[v] Hodnota [CORDB_ADDRESS,](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) která určuje počáteční adresu segmentu spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="37fb0-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="37fb0-107">[out] Ukazatel na adresu objektu "ICorDebugCode", který představuje segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="37fb0-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37fb0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37fb0-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37fb0-109">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="37fb0-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fb0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37fb0-110">Requirements</span></span>  
 <span data-ttu-id="37fb0-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fb0-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37fb0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37fb0-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37fb0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37fb0-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fb0-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fb0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="37fb0-115">See also</span></span>

- [<span data-ttu-id="37fb0-116">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="37fb0-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="37fb0-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37fb0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
