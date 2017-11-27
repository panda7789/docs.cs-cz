---
title: "IBindingDisplay::InitializeForProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.InitializeForProcess
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e5ab3bb38d23e5841a347a348a09deb3b5639962
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="03ff5-102">IBindingDisplay::InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="03ff5-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="03ff5-103">Inicializuje [ibindingdisplay –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="03ff5-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03ff5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03ff5-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03ff5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03ff5-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="03ff5-106">[v] Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="03ff5-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03ff5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03ff5-107">Remarks</span></span>  
 <span data-ttu-id="03ff5-108">Ladicí program volání `InitializeForProcess` metoda v okamžiku vytvoření k chybě při inicializaci zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="03ff5-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="03ff5-109">`InitializeForProcess`musí být volána v okamžiku vytvoření před jinou metodu na `IBindingDisplay` je volána.</span><span class="sxs-lookup"><span data-stu-id="03ff5-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03ff5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03ff5-110">Requirements</span></span>  
 <span data-ttu-id="03ff5-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03ff5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03ff5-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="03ff5-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="03ff5-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="03ff5-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="03ff5-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03ff5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03ff5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="03ff5-115">See Also</span></span>  
 [<span data-ttu-id="03ff5-116">Ibindingdisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03ff5-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
