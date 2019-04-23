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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162247"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="6006a-102">IBindingDisplay::GetCurrentDisplay – metoda</span><span class="sxs-lookup"><span data-stu-id="6006a-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="6006a-103">Vrátí informace o zobrazení aktuální vazby.</span><span class="sxs-lookup"><span data-stu-id="6006a-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6006a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6006a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6006a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6006a-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="6006a-106">[out, retval] Ukazatel na safearray obsahující informace o vazbě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="6006a-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6006a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6006a-107">Remarks</span></span>  
 <span data-ttu-id="6006a-108">[Ibindingdisplay::initializeforprocess –](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) metoda musí mít dříve byla úspěšná, a program je nutné zastavit pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6006a-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="6006a-109">Volající musí uvolnit vráceného `SAFEARRAY` paměti pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="6006a-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6006a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6006a-110">Requirements</span></span>  
 <span data-ttu-id="6006a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6006a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6006a-112">**Záhlaví:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="6006a-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="6006a-113">**Knihovna:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="6006a-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="6006a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6006a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6006a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6006a-115">See also</span></span>

- [<span data-ttu-id="6006a-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6006a-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="6006a-117">InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="6006a-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
