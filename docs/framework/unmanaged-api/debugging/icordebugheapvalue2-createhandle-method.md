---
title: ICorDebugHeapValue2::CreateHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5c5a12df5689f113857045ba4bcda696bda8f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756729"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="1bdae-102">ICorDebugHeapValue2::CreateHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="1bdae-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="1bdae-103">Vytvoří popisovač haldy hodnoty reprezentovaný tímto objektem icordebugheapvalue2 – zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="1bdae-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bdae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bdae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bdae-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="1bdae-106">[in] Hodnota cordebughandletype – výčet, který určuje typ popisovače, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="1bdae-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="1bdae-107">[out] Ukazatel na adresu icordebughandlevalue – objekt, který reprezentuje nový popisovač pro tuto hodnotu haldy.</span><span class="sxs-lookup"><span data-stu-id="1bdae-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bdae-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bdae-108">Remarks</span></span>  
 <span data-ttu-id="1bdae-109">Popisovač se vytvoří v aplikační doméně, která souvisí s hodnotou haldy a už nebudou platné, pokud získá uvolněné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1bdae-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="1bdae-110">Více volání této funkce pro stejnou hodnotu haldy vytvoří více popisovačů.</span><span class="sxs-lookup"><span data-stu-id="1bdae-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="1bdae-111">Protože popisovače vliv na výkon systému uvolňování paměti, ladicí program by měl omezit relativně malý počet popisovačů (přibližně 256), které jsou aktivní v čase.</span><span class="sxs-lookup"><span data-stu-id="1bdae-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bdae-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bdae-112">Requirements</span></span>  
 <span data-ttu-id="1bdae-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdae-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bdae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bdae-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bdae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bdae-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
