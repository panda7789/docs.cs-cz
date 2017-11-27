---
title: "VariableLocationType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0338a89acdd9c29370bc8e52ed9a099e9330c2cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="212e2-102">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="212e2-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="212e2-103">Označuje typ nativní umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="212e2-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="212e2-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="212e2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="212e2-105">Members</span></span>  
  
|<span data-ttu-id="212e2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="212e2-106">Member</span></span>|<span data-ttu-id="212e2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="212e2-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="212e2-108">Proměnná je do registru.</span><span class="sxs-lookup"><span data-stu-id="212e2-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="212e2-109">Proměnná je v paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="212e2-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="212e2-110">Proměnná nejsou uložené v registru nebo paměti register relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="212e2-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="212e2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="212e2-111">Remarks</span></span>  
 <span data-ttu-id="212e2-112">Členem `VariableLocationType` výčtu je vrácený [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="212e2-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="212e2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="212e2-113">Requirements</span></span>  
 <span data-ttu-id="212e2-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="212e2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="212e2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="212e2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="212e2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="212e2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="212e2-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="212e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="212e2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="212e2-118">See Also</span></span>  
 [<span data-ttu-id="212e2-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="212e2-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
