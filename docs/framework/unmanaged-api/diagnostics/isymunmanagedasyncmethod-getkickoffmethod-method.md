---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="00bb9-102">ISymUnmanagedAsyncMethod::GetKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="00bb9-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="00bb9-103">V tématu [definekickoffmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="00bb9-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00bb9-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00bb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00bb9-105">Parameters</span></span>  
  
|<span data-ttu-id="00bb9-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="00bb9-106">Parameter</span></span>|<span data-ttu-id="00bb9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00bb9-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="00bb9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00bb9-108">Return Value</span></span>  
 <span data-ttu-id="00bb9-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="00bb9-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bb9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00bb9-110">Requirements</span></span>  
 <span data-ttu-id="00bb9-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00bb9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bb9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="00bb9-112">See Also</span></span>  
 [<span data-ttu-id="00bb9-113">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00bb9-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
