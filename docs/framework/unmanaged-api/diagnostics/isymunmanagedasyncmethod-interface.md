---
title: "ISymUnmanagedAsyncMethod – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3ee944940cef0d3162a020c81353fd6b8cfb82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="cd886-102">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd886-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="cd886-103">Toto rozhraní je doplňkovým čtení na [isymunmanagedasyncmethodpropertieswriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd886-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd886-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="cd886-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cd886-105">Methods</span></span>  
 <span data-ttu-id="cd886-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="cd886-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="cd886-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-107">Method</span></span>|<span data-ttu-id="cd886-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cd886-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd886-109">Getasyncstepinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="cd886-110">V tématu [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="cd886-111">Getasyncstepinfocount – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="cd886-112">V tématu [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="cd886-113">Getcatchhandleriloffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="cd886-114">V tématu [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="cd886-115">Getkickoffmethod – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="cd886-116">V tématu [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="cd886-117">Hascatchhandleriloffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="cd886-118">V tématu [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd886-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="cd886-119">Isasyncmethod – metoda</span><span class="sxs-lookup"><span data-stu-id="cd886-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="cd886-120">Zkontroluje, zda metoda má asynchronní informace, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="cd886-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="cd886-121">Pokud tato metoda vrátí hodnotu `FALSE` , pak je volat jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd886-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="cd886-122">Ty budou všechny návratové `E_UNEXPECTED` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="cd886-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd886-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd886-123">Requirements</span></span>  
 <span data-ttu-id="cd886-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cd886-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd886-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd886-125">See Also</span></span>  
 [<span data-ttu-id="cd886-126">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="cd886-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
