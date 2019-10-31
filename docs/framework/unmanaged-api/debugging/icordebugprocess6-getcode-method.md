---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: fc7fecc3f523d7992bd57e2f7d485648caa6df8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123471"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="d5d68-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="d5d68-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="d5d68-103">Načte informace o spravovaném kódu na konkrétní kódové adrese.</span><span class="sxs-lookup"><span data-stu-id="d5d68-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5d68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5d68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5d68-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="d5d68-106">pro Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která určuje počáteční adresu spravovaného segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="d5d68-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="d5d68-107">mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d5d68-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5d68-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5d68-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d68-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d5d68-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d68-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5d68-110">Requirements</span></span>  
 <span data-ttu-id="d5d68-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d68-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d68-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5d68-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5d68-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5d68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5d68-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d68-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d68-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5d68-115">See also</span></span>

- [<span data-ttu-id="d5d68-116">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5d68-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d5d68-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d5d68-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
