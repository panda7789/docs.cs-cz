---
title: 'ICorDebugVariableHome:: GetOffset – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 3af8c925b80b9fd4ed0a46d2bd50fe37a6f3154a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125100"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="ecf9a-102">ICorDebugVariableHome:: GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ecf9a-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="ecf9a-103">Získá posun od základního registru pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="ecf9a-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecf9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecf9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecf9a-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="ecf9a-106">mimo Posun základního registru.</span><span class="sxs-lookup"><span data-stu-id="ecf9a-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecf9a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecf9a-107">Return Value</span></span>  
 <span data-ttu-id="ecf9a-108">Metoda vrací následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ecf9a-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="ecf9a-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ecf9a-109">Value</span></span>|<span data-ttu-id="ecf9a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ecf9a-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ecf9a-111">Proměnná je v umístění relativní paměti pro registraci.</span><span class="sxs-lookup"><span data-stu-id="ecf9a-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ecf9a-112">Proměnná není v umístění relativní paměti registru.</span><span class="sxs-lookup"><span data-stu-id="ecf9a-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecf9a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecf9a-113">Requirements</span></span>  
 <span data-ttu-id="ecf9a-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf9a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf9a-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecf9a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecf9a-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecf9a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecf9a-117">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf9a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf9a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecf9a-118">See also</span></span>

- [<span data-ttu-id="ecf9a-119">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecf9a-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
