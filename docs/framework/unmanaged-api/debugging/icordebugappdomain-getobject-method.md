---
title: ICorDebugAppDomain::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134703"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="b0b9d-102">ICorDebugAppDomain::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="b0b9d-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="b0b9d-103">Načte ukazatel rozhraní do aplikační domény modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b0b9d-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0b9d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0b9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0b9d-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="b0b9d-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugValue, který představuje doménu aplikace CLR.</span><span class="sxs-lookup"><span data-stu-id="b0b9d-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0b9d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0b9d-107">Return Value</span></span>  
 <span data-ttu-id="b0b9d-108">Pokud objekt spravovaného <xref:System.AppDomain?displayProperty=nameWithType> nebyl vytvořen pro tuto doménu aplikace, metoda vrátí `S_FALSE` a umístí `NULL` do `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="b0b9d-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0b9d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0b9d-109">Remarks</span></span>  
 <span data-ttu-id="b0b9d-110">Každá doména aplikace v procesu může mít spravovaný objekt <xref:System.AppDomain?displayProperty=nameWithType> v modulu runtime, který ho představuje.</span><span class="sxs-lookup"><span data-stu-id="b0b9d-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="b0b9d-111">Tato funkce získá objekt rozhraní ICorDebugValue, který odpovídá tomuto spravovanému objektu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0b9d-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b9d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0b9d-112">Requirements</span></span>  
 <span data-ttu-id="b0b9d-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b9d-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0b9d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0b9d-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0b9d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0b9d-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
