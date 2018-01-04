---
title: "ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="aca20-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="aca20-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="aca20-103">V tématu [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="aca20-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aca20-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aca20-105">Parameters</span></span>  
  
|<span data-ttu-id="aca20-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="aca20-106">Parameter</span></span>|<span data-ttu-id="aca20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aca20-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="aca20-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aca20-108">Return Value</span></span>  
 <span data-ttu-id="aca20-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="aca20-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca20-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aca20-110">Requirements</span></span>  
 <span data-ttu-id="aca20-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aca20-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca20-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="aca20-112">See Also</span></span>  
 [<span data-ttu-id="aca20-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aca20-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
