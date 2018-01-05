---
title: "ICorDebugVariableHome::GetRegister – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54f1c737b0c6ce6281a71419cbd8c88277702f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="70dfb-102">ICorDebugVariableHome::GetRegister – metoda</span><span class="sxs-lookup"><span data-stu-id="70dfb-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="70dfb-103">Získá registrace, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="70dfb-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70dfb-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70dfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70dfb-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="70dfb-106">[out] CorDebugRegister – výčet hodnotu, která určuje registrace pro proměnné s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="70dfb-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70dfb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70dfb-107">Return Value</span></span>  
 <span data-ttu-id="70dfb-108">Metoda vrátí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="70dfb-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="70dfb-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70dfb-109">Value</span></span>|<span data-ttu-id="70dfb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="70dfb-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="70dfb-111">Proměnná je v seznamu uvedené `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="70dfb-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="70dfb-112">Proměnná se nenachází v registru nebo register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="70dfb-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70dfb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70dfb-113">Requirements</span></span>  
 <span data-ttu-id="70dfb-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70dfb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70dfb-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70dfb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70dfb-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70dfb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70dfb-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70dfb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dfb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="70dfb-118">See Also</span></span>  
 [<span data-ttu-id="70dfb-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="70dfb-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="70dfb-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70dfb-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
