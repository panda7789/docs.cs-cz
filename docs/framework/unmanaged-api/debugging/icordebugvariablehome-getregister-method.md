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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396822"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="57f07-102">ICorDebugVariableHome:: getregister – metoda</span><span class="sxs-lookup"><span data-stu-id="57f07-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="57f07-103">Získá registr, který obsahuje proměnnou s typem umístění `VLT_REGISTER` a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="57f07-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57f07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57f07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57f07-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="57f07-106">mimo Hodnota výčtu CorDebugRegister –, která označuje registr pro proměnnou s typem umístění `VLT_REGISTER` a základní registr pro proměnnou s typem umístění `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="57f07-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57f07-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="57f07-107">Return Value</span></span>  
 <span data-ttu-id="57f07-108">Metoda vrací následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="57f07-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="57f07-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="57f07-109">Value</span></span>|<span data-ttu-id="57f07-110">Popis</span><span class="sxs-lookup"><span data-stu-id="57f07-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="57f07-111">Proměnná je v registru označeném `pRegister` argumentem.</span><span class="sxs-lookup"><span data-stu-id="57f07-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="57f07-112">Proměnná není v registru ani v relativním umístění registru.</span><span class="sxs-lookup"><span data-stu-id="57f07-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57f07-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57f07-113">Requirements</span></span>  
 <span data-ttu-id="57f07-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57f07-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57f07-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57f07-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57f07-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57f07-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57f07-117">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57f07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57f07-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="57f07-118">See also</span></span>

- [<span data-ttu-id="57f07-119">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="57f07-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="57f07-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57f07-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
