---
title: "ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9ce105c-6495-49ab-b0e5-903a48ebadb3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5aaad64a5e5888852dc41e7397ca5014d50ea56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodhascatchhandleriloffset-method"></a><span data-ttu-id="2ba09-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2ba09-102">ISymUnmanagedAsyncMethod::HasCatchHandlerILOffset Method</span></span>
<span data-ttu-id="2ba09-103">V tématu [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="2ba09-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ba09-104">Syntax</span></span>  
  
```idl  
HRESULT HasCatchHandlerILOffset(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ba09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ba09-105">Parameters</span></span>  
  
|<span data-ttu-id="2ba09-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="2ba09-106">Parameter</span></span>|<span data-ttu-id="2ba09-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2ba09-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="2ba09-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ba09-108">Return Value</span></span>  
 <span data-ttu-id="2ba09-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2ba09-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ba09-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ba09-110">Requirements</span></span>  
 <span data-ttu-id="2ba09-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2ba09-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba09-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ba09-112">See Also</span></span>  
 [<span data-ttu-id="2ba09-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ba09-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
