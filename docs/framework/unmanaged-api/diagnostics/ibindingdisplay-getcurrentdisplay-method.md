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
ms.openlocfilehash: 992626fb3fa085c85d61b9bdd25c985436e96aea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550562"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="6cd56-102">IBindingDisplay::GetCurrentDisplay – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd56-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="6cd56-103">Vrátí informace o zobrazení aktuální vazby.</span><span class="sxs-lookup"><span data-stu-id="6cd56-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd56-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cd56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cd56-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="6cd56-106">[out, retval] Ukazatel na safearray obsahující informace o vazbě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="6cd56-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cd56-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cd56-107">Remarks</span></span>  
 <span data-ttu-id="6cd56-108">[Ibindingdisplay::initializeforprocess –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musí mít dříve byla úspěšná, a program je nutné zastavit pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6cd56-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="6cd56-109">Volající musí uvolnit vráceného `SAFEARRAY` paměti pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="6cd56-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd56-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cd56-110">Requirements</span></span>  
 <span data-ttu-id="6cd56-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd56-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd56-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="6cd56-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="6cd56-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="6cd56-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="6cd56-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd56-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cd56-115">See also</span></span>
- [<span data-ttu-id="6cd56-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd56-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="6cd56-117">InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd56-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
