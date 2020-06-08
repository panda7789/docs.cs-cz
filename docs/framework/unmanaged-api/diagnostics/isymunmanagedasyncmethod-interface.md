---
title: ISymUnmanagedAsyncMethod – rozhraní
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504449"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="d758d-102">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d758d-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="d758d-103">Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d758d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d758d-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="d758d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d758d-105">Methods</span></span>  
 <span data-ttu-id="d758d-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="d758d-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="d758d-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-107">Method</span></span>|<span data-ttu-id="d758d-108">Description</span><span class="sxs-lookup"><span data-stu-id="d758d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d758d-109">GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="d758d-110">Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="d758d-111">GetAsyncStepInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="d758d-112">Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="d758d-113">GetCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="d758d-114">Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="d758d-115">GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="d758d-116">Viz [Metoda definekickoffmethod –](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="d758d-117">HasCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="d758d-118">Viz [Metoda definecatchhandleriloffset –](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="d758d-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="d758d-119">IsAsyncMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d758d-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="d758d-120">Kontroluje, zda metoda obsahuje asynchronní informace nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="d758d-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="d758d-121">Pokud se tato metoda vrátí `FALSE` , je neplatná pro volání jakékoli jiné metody v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d758d-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="d758d-122">Budou `E_UNEXPECTED` v tomto případě vráceny.</span><span class="sxs-lookup"><span data-stu-id="d758d-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d758d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d758d-123">Requirements</span></span>  
 <span data-ttu-id="d758d-124">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d758d-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d758d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d758d-125">See also</span></span>

- [<span data-ttu-id="d758d-126">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="d758d-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
