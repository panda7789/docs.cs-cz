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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aabad159b521207fed976636ae8b9e338f09ac42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466177"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="d70c4-102">IBindingDisplay::InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="d70c4-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="d70c4-103">Inicializuje [ibindingdisplay –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="d70c4-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d70c4-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d70c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d70c4-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="d70c4-106">[in] Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="d70c4-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d70c4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d70c4-107">Remarks</span></span>  
 <span data-ttu-id="d70c4-108">Volání ladicího programu `InitializeForProcess` metoda v okamžiku vytvoření inicializace zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="d70c4-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="d70c4-109">`InitializeForProcess` musí být volána v okamžiku vytvoření před jakoukoli metodu na `IBindingDisplay` je volána.</span><span class="sxs-lookup"><span data-stu-id="d70c4-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70c4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d70c4-110">Requirements</span></span>  
 <span data-ttu-id="d70c4-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d70c4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70c4-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="d70c4-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d70c4-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="d70c4-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d70c4-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70c4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70c4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d70c4-115">See also</span></span>
- [<span data-ttu-id="d70c4-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d70c4-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
