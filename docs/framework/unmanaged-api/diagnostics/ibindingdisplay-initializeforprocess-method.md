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
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442147"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="319c0-102">IBindingDisplay::InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="319c0-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="319c0-103">Inicializuje objekt [IBindingDisplay](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="319c0-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="319c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="319c0-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="319c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="319c0-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="319c0-106">pro Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="319c0-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="319c0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="319c0-107">Remarks</span></span>  
 <span data-ttu-id="319c0-108">Ladicí program volá `InitializeForProcess` metodu v okamžiku vytvoření pro inicializaci zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="319c0-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="319c0-109">`InitializeForProcess`musí být voláno v době vytváření před voláním jakékoli jiné metody `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="319c0-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="319c0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="319c0-110">Requirements</span></span>  
 <span data-ttu-id="319c0-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="319c0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="319c0-112">**Hlavička:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="319c0-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="319c0-113">**Knihovna:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="319c0-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="319c0-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="319c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319c0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="319c0-115">See also</span></span>

- [<span data-ttu-id="319c0-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="319c0-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
