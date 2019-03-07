---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84aef2b26e008d1a3c6d95d7ec1e130ab0594a11
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484547"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="372d8-102">ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="372d8-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="372d8-103">Zobrazit [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="372d8-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="372d8-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="372d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="372d8-105">Parameters</span></span>  
  
|<span data-ttu-id="372d8-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="372d8-106">Parameter</span></span>|<span data-ttu-id="372d8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="372d8-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="372d8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="372d8-108">Return Value</span></span>  
 <span data-ttu-id="372d8-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="372d8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="372d8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="372d8-110">Requirements</span></span>  
 <span data-ttu-id="372d8-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="372d8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372d8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="372d8-112">See also</span></span>
- [<span data-ttu-id="372d8-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="372d8-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
