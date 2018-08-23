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
ms.openlocfilehash: 889456f08c967c807b4d3d09508af000035ebdaf
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755077"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="12700-102">IBindingDisplay::GetCurrentDisplay – metoda</span><span class="sxs-lookup"><span data-stu-id="12700-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="12700-103">Vrátí informace o zobrazení aktuální vazby.</span><span class="sxs-lookup"><span data-stu-id="12700-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12700-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12700-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12700-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12700-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="12700-106">[out, retval] Ukazatel na safearray obsahující informace o vazbě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="12700-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12700-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12700-107">Remarks</span></span>  
 <span data-ttu-id="12700-108">[Ibindingdisplay::initializeforprocess –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musí mít dříve byla úspěšná, a program je nutné zastavit pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="12700-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="12700-109">Volající musí uvolnit vráceného `SAFEARRAY` paměti pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="12700-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12700-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12700-110">Requirements</span></span>  
 <span data-ttu-id="12700-111">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12700-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12700-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="12700-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="12700-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="12700-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="12700-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12700-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12700-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="12700-115">See Also</span></span>  
 [<span data-ttu-id="12700-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12700-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="12700-117">InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="12700-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
