---
title: 'ICorDebugVariableHome:: getregister – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125064"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="28391-102">ICorDebugVariableHome:: getregister – metoda</span><span class="sxs-lookup"><span data-stu-id="28391-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="28391-103">Získá registr, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="28391-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28391-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28391-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28391-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28391-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="28391-106">mimo Hodnota výčtu CorDebugRegister –, která označuje registr pro proměnnou s typem umístění `VLT_REGISTER`a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="28391-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28391-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="28391-107">Return Value</span></span>  
 <span data-ttu-id="28391-108">Metoda vrací následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="28391-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="28391-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="28391-109">Value</span></span>|<span data-ttu-id="28391-110">Popis</span><span class="sxs-lookup"><span data-stu-id="28391-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="28391-111">Proměnná je v registru označeném argumentem `pRegister`.</span><span class="sxs-lookup"><span data-stu-id="28391-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="28391-112">Proměnná není v registru ani v relativním umístění registru.</span><span class="sxs-lookup"><span data-stu-id="28391-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28391-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28391-113">Requirements</span></span>  
 <span data-ttu-id="28391-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28391-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28391-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28391-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28391-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28391-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28391-117">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28391-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28391-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28391-118">See also</span></span>

- [<span data-ttu-id="28391-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="28391-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="28391-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28391-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
