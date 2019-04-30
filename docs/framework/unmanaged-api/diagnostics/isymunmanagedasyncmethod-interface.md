---
title: ISymUnmanagedAsyncMethod – rozhraní
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd524446cd9fd5cf9c067ab5778a654ed000ffb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940176"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="56297-102">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56297-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="56297-103">Toto rozhraní je doplněk čtení k [isymunmanagedasyncmethodpropertieswriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="56297-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56297-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56297-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="56297-105">Metody</span><span class="sxs-lookup"><span data-stu-id="56297-105">Methods</span></span>  
 <span data-ttu-id="56297-106">Toto rozhraní obsahuje následující dvě metody:</span><span class="sxs-lookup"><span data-stu-id="56297-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="56297-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="56297-107">Method</span></span>|<span data-ttu-id="56297-108">Popis</span><span class="sxs-lookup"><span data-stu-id="56297-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56297-109">GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="56297-110">Zobrazit [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="56297-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="56297-111">GetAsyncStepInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="56297-112">Zobrazit [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="56297-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="56297-113">GetCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="56297-114">Zobrazit [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="56297-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="56297-115">GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="56297-116">Zobrazit [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="56297-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="56297-117">HasCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="56297-118">Zobrazit [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="56297-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="56297-119">IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="56297-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="56297-120">Kontroluje, jestli metoda má asynchronní informace, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="56297-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="56297-121">Pokud tato metoda vrátí `FALSE` je volat jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56297-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="56297-122">Budou všechny návratové `E_UNEXPECTED` v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="56297-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56297-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56297-123">Requirements</span></span>  
 <span data-ttu-id="56297-124">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56297-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56297-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56297-125">See also</span></span>

- [<span data-ttu-id="56297-126">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="56297-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
