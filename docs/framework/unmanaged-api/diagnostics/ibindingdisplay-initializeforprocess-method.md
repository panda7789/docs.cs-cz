---
title: IBindingDisplay::InitializeForProcess – metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: bb796a12868cc3e44394ab493f7838dc48ab4dc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448493"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="943b5-102">IBindingDisplay::InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="943b5-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="943b5-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span><span class="sxs-lookup"><span data-stu-id="943b5-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="943b5-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="943b5-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="943b5-106">[in] The process identifier.</span><span class="sxs-lookup"><span data-stu-id="943b5-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943b5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="943b5-107">Remarks</span></span>  
 <span data-ttu-id="943b5-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span><span class="sxs-lookup"><span data-stu-id="943b5-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="943b5-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span><span class="sxs-lookup"><span data-stu-id="943b5-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="943b5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="943b5-110">Requirements</span></span>  
 <span data-ttu-id="943b5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="943b5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="943b5-112">**Header:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="943b5-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="943b5-113">**Library:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="943b5-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="943b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="943b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943b5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="943b5-115">See also</span></span>

- [<span data-ttu-id="943b5-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="943b5-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
