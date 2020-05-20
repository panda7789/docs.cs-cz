---
title: ISymUnmanagedAsyncMethod – rozhraní
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: fef1af75587b889afad9cb5b93d0cd722294006b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441809"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="6a234-102">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a234-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="6a234-103">Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a234-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="6a234-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6a234-105">Methods</span></span>  
 <span data-ttu-id="6a234-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="6a234-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="6a234-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-107">Method</span></span>|<span data-ttu-id="6a234-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6a234-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a234-109">GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="6a234-110">Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="6a234-111">GetAsyncStepInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="6a234-112">Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="6a234-113">GetCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="6a234-114">Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="6a234-115">GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="6a234-116">Viz [Metoda definekickoffmethod –](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="6a234-117">HasCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="6a234-118">Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a234-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="6a234-119">IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="6a234-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="6a234-120">Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="6a234-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="6a234-121">Pokud se tato metoda vrátí `FALSE` , je neplatná pro volání jakékoli jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6a234-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="6a234-122">Budou `E_UNEXPECTED` v tomto případě vráceny.</span><span class="sxs-lookup"><span data-stu-id="6a234-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a234-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a234-123">Requirements</span></span>  
 <span data-ttu-id="6a234-124">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a234-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a234-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a234-125">See also</span></span>

- [<span data-ttu-id="6a234-126">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="6a234-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
