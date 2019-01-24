---
title: Výčet CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d712a46a8ddb79846e56077e9ed6283ea4d40ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523880"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="a9082-102">Výčet CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="a9082-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="a9082-103">Popisuje, jak exportované funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a9082-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9082-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9082-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="a9082-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a9082-105">Members</span></span>  
  
|<span data-ttu-id="a9082-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a9082-106">Member</span></span>|<span data-ttu-id="a9082-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a9082-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="a9082-108">Pokud spravovaný kód vyvolá tuto metodu, bude mít umístěné explicitní události nebo zarážek později.</span><span class="sxs-lookup"><span data-stu-id="a9082-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="a9082-109">--nebo--</span><span class="sxs-lookup"><span data-stu-id="a9082-109">--or--</span></span><br /><br /> <span data-ttu-id="a9082-110">Jsme právě přijít o některé spravovaný kód, který tato metoda se volá, protože neexistuje žádný snadný způsob, jak zastavit na něj.</span><span class="sxs-lookup"><span data-stu-id="a9082-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="a9082-111">--nebo--</span><span class="sxs-lookup"><span data-stu-id="a9082-111">--or--</span></span><br /><br /> <span data-ttu-id="a9082-112">Spravovaný kód může nikdy vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="a9082-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="a9082-113">Tato metoda vyvolá spravovaný kód prostřednictvím návratový instrukce.</span><span class="sxs-lookup"><span data-stu-id="a9082-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="a9082-114">Krokování by měl přejít na další spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a9082-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="a9082-115">Tato metoda vyvolá spravovaného kódu pomocí volání funkce tail.</span><span class="sxs-lookup"><span data-stu-id="a9082-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="a9082-116">Krokování jednou a krokování přes všechny pokyny volání by měl přejít na spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a9082-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9082-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9082-117">Remarks</span></span>  
 <span data-ttu-id="a9082-118">Tento výčet je používán [icordebugprocess6::getexportstepinfo –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodu k dispozici informace o procházení spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a9082-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9082-119">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="a9082-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9082-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9082-120">Requirements</span></span>  
 <span data-ttu-id="a9082-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9082-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9082-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9082-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9082-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9082-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9082-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9082-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9082-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9082-125">See also</span></span>
- [<span data-ttu-id="a9082-126">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="a9082-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="a9082-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="a9082-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
