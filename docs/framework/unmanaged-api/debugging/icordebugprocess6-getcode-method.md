---
title: ICorDebugProcess6::GetCode – metoda
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 178d1df7e6c8246b18afed442e944c49051b6597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209263"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="002e9-102">ICorDebugProcess6::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="002e9-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="002e9-103">Načte informace o spravovaném kódu na konkrétní kódové adrese.</span><span class="sxs-lookup"><span data-stu-id="002e9-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="002e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="002e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="002e9-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="002e9-106">pro Hodnota [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , která určuje počáteční adresu spravovaného segmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="002e9-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="002e9-107">mimo Ukazatel na adresu objektu "ICorDebugCode", který představuje segment spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="002e9-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="002e9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="002e9-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="002e9-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="002e9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002e9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="002e9-110">Requirements</span></span>  
 <span data-ttu-id="002e9-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002e9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002e9-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="002e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002e9-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="002e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002e9-114">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002e9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002e9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="002e9-115">See also</span></span>

- [<span data-ttu-id="002e9-116">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="002e9-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="002e9-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="002e9-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
