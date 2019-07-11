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
ms.openlocfilehash: f4b3b80546095b79dc5b551a9c5e92ec15c0dddb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771784"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="eea62-102">ICorDebugVariableHome::GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="eea62-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="eea62-103">Získá do registru, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="eea62-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eea62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eea62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eea62-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="eea62-106">[out] Cordebugregister – výčet hodnotu, která označuje do registru pro proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="eea62-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eea62-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eea62-107">Return Value</span></span>  
 <span data-ttu-id="eea62-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="eea62-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="eea62-109">Value</span><span class="sxs-lookup"><span data-stu-id="eea62-109">Value</span></span>|<span data-ttu-id="eea62-110">Popis</span><span class="sxs-lookup"><span data-stu-id="eea62-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="eea62-111">Proměnná je do registru indikován `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="eea62-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="eea62-112">Proměnná není v registru nebo registru relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="eea62-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eea62-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eea62-113">Requirements</span></span>  
 <span data-ttu-id="eea62-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eea62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea62-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eea62-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eea62-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eea62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eea62-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea62-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea62-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eea62-118">See also</span></span>

- [<span data-ttu-id="eea62-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="eea62-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="eea62-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eea62-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
