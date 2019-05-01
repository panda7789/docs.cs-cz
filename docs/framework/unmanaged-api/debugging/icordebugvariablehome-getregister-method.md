---
title: ICorDebugVariableHome::GetRegister – metoda
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 290647f0e0dcaeae53362762ed7f8e0c2f05a82c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993639"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="52c71-102">ICorDebugVariableHome::GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="52c71-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="52c71-103">Získá do registru, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="52c71-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52c71-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52c71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52c71-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="52c71-106">[out] Cordebugregister – výčet hodnotu, která označuje do registru pro proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="52c71-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c71-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52c71-107">Return Value</span></span>  
 <span data-ttu-id="52c71-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="52c71-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="52c71-109">Value</span><span class="sxs-lookup"><span data-stu-id="52c71-109">Value</span></span>|<span data-ttu-id="52c71-110">Popis</span><span class="sxs-lookup"><span data-stu-id="52c71-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="52c71-111">Proměnná je do registru indikován `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="52c71-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="52c71-112">Proměnná není v registru nebo registru relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="52c71-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52c71-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52c71-113">Requirements</span></span>  
 <span data-ttu-id="52c71-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52c71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c71-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52c71-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52c71-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52c71-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52c71-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c71-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c71-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52c71-118">See also</span></span>

- [<span data-ttu-id="52c71-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="52c71-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="52c71-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52c71-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
