---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20039318d6e1230ccc0fbd203fc44686806bb2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604467"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="389ed-102">ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="389ed-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="389ed-103">Zobrazit [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="389ed-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="389ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="389ed-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="389ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="389ed-105">Parameters</span></span>  
  
|<span data-ttu-id="389ed-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="389ed-106">Parameter</span></span>|<span data-ttu-id="389ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="389ed-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="389ed-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="389ed-108">Return Value</span></span>  
 <span data-ttu-id="389ed-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="389ed-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="389ed-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="389ed-110">Requirements</span></span>  
 <span data-ttu-id="389ed-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="389ed-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="389ed-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="389ed-112">See also</span></span>
- [<span data-ttu-id="389ed-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="389ed-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
