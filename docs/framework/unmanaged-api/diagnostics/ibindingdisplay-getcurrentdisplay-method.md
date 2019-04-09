---
title: IBindingDisplay::GetCurrentDisplay – metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 472e06c3a00762a7bb012fbcb525d8e0b3a9271a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162247"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="ba44e-102">IBindingDisplay::GetCurrentDisplay – metoda</span><span class="sxs-lookup"><span data-stu-id="ba44e-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="ba44e-103">Vrátí informace o zobrazení aktuální vazby.</span><span class="sxs-lookup"><span data-stu-id="ba44e-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba44e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba44e-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba44e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba44e-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="ba44e-106">[out, retval] Ukazatel na safearray obsahující informace o vazbě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ba44e-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba44e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba44e-107">Remarks</span></span>  
 <span data-ttu-id="ba44e-108">[Ibindingdisplay::initializeforprocess –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musí mít dříve byla úspěšná, a program je nutné zastavit pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ba44e-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="ba44e-109">Volající musí uvolnit vráceného `SAFEARRAY` paměti pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="ba44e-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba44e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba44e-110">Requirements</span></span>  
 <span data-ttu-id="ba44e-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba44e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba44e-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="ba44e-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="ba44e-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="ba44e-113">**Library:** BindingDisplay.idl</span></span>  
  
 **<span data-ttu-id="ba44e-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ba44e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba44e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba44e-115">See also</span></span>

- [<span data-ttu-id="ba44e-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba44e-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="ba44e-117">InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="ba44e-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
