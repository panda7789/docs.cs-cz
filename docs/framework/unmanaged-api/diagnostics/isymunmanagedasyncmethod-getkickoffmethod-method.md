---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174938"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="7e67a-102">ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7e67a-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="7e67a-103">Zobrazit [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e67a-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e67a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e67a-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e67a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e67a-105">Parameters</span></span>  
  
|<span data-ttu-id="7e67a-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="7e67a-106">Parameter</span></span>|<span data-ttu-id="7e67a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7e67a-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7e67a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7e67a-108">Return Value</span></span>  
 <span data-ttu-id="7e67a-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7e67a-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e67a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e67a-110">Requirements</span></span>  
 <span data-ttu-id="7e67a-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7e67a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e67a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e67a-112">See also</span></span>

- [<span data-ttu-id="7e67a-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e67a-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
