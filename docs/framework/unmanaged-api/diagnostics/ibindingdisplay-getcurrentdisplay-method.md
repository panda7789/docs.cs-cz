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
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442186"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="bddac-102">IBindingDisplay::GetCurrentDisplay – metoda</span><span class="sxs-lookup"><span data-stu-id="bddac-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="bddac-103">Vrátí aktuální informace o zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="bddac-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bddac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bddac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bddac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bddac-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="bddac-106">[out, retval] Ukazatel na pole SAFEARRAY obsahující informace o zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="bddac-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bddac-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bddac-107">Remarks</span></span>  
 <span data-ttu-id="bddac-108">Metoda [IBindingDisplay:: InitializeForProcess –](ibindingdisplay-initializeforprocess-method.md) musí být dřív úspěšná a program musí být zastavený pomocí ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="bddac-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="bddac-109">Volající musí navrátit vrácenou `SAFEARRAY` paměť pomocí [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="bddac-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bddac-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bddac-110">Requirements</span></span>  
 <span data-ttu-id="bddac-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bddac-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bddac-112">**Hlavička:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="bddac-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="bddac-113">**Knihovna:** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="bddac-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="bddac-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bddac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddac-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bddac-115">See also</span></span>

- [<span data-ttu-id="bddac-116">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bddac-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="bddac-117">InitializeForProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="bddac-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
