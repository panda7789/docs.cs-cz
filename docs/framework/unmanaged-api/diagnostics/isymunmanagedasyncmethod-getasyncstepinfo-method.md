---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: e3c0d7b8eeded403ce8391cff00ee18dccc38ed5
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441887"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="ac1dd-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="ac1dd-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="ac1dd-103">Viz [Metoda defineasyncstepinfo –](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ac1dd-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac1dd-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac1dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac1dd-105">Parameters</span></span>  
  
|<span data-ttu-id="ac1dd-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="ac1dd-106">Parameter</span></span>|<span data-ttu-id="ac1dd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1dd-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="ac1dd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac1dd-108">Return Value</span></span>  
 <span data-ttu-id="ac1dd-109">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ac1dd-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac1dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac1dd-110">Requirements</span></span>  
 <span data-ttu-id="ac1dd-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ac1dd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1dd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac1dd-112">See also</span></span>

- [<span data-ttu-id="ac1dd-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac1dd-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
