---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: 5d3ee0d42773b70c8301260e5b4d6af1c7ceb938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139851"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="de558-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="de558-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="de558-103">Viz [Metoda defineasyncstepinfo –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="de558-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de558-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de558-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de558-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de558-105">Parameters</span></span>  
  
|<span data-ttu-id="de558-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="de558-106">Parameter</span></span>|<span data-ttu-id="de558-107">Popis</span><span class="sxs-lookup"><span data-stu-id="de558-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="de558-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de558-108">Return Value</span></span>  
 <span data-ttu-id="de558-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="de558-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de558-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de558-110">Requirements</span></span>  
 <span data-ttu-id="de558-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="de558-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de558-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de558-112">See also</span></span>

- [<span data-ttu-id="de558-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de558-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
