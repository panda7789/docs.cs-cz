---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7c72d0766580f9aa3aa678aacd872b804172a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131427"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="fbd6e-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fbd6e-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="fbd6e-103">Zobrazit [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="fbd6e-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbd6e-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbd6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbd6e-105">Parameters</span></span>  
  
|<span data-ttu-id="fbd6e-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="fbd6e-106">Parameter</span></span>|<span data-ttu-id="fbd6e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fbd6e-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="fbd6e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fbd6e-108">Return Value</span></span>  
 <span data-ttu-id="fbd6e-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fbd6e-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd6e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbd6e-110">Requirements</span></span>  
 <span data-ttu-id="fbd6e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fbd6e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd6e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbd6e-112">See also</span></span>

- [<span data-ttu-id="fbd6e-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbd6e-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
