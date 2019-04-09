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
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197862"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="4df87-102">IBindingDisplay::InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="4df87-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="4df87-103">Inicializuje [ibindingdisplay –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="4df87-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4df87-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4df87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df87-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="4df87-106">[in] Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="4df87-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df87-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4df87-107">Remarks</span></span>  
 <span data-ttu-id="4df87-108">Volání ladicího programu `InitializeForProcess` metoda v okamžiku vytvoření inicializace zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="4df87-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> `InitializeForProcess` <span data-ttu-id="4df87-109">musí být volána v okamžiku vytvoření před jakoukoli metodu na `IBindingDisplay` je volána.</span><span class="sxs-lookup"><span data-stu-id="4df87-109">must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df87-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4df87-110">Requirements</span></span>  
 <span data-ttu-id="4df87-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df87-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="4df87-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="4df87-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="4df87-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="4df87-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4df87-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4df87-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4df87-115">See also</span></span>

- [<span data-ttu-id="4df87-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4df87-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
