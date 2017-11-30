---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b2431662caa41c67746da7e21591c743896c161
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="ed1ab-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="ed1ab-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="ed1ab-103">V tématu [defineasyncstepinfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ed1ab-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed1ab-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed1ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed1ab-105">Parameters</span></span>  
  
|<span data-ttu-id="ed1ab-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="ed1ab-106">Parameter</span></span>|<span data-ttu-id="ed1ab-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ed1ab-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="ed1ab-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed1ab-108">Return Value</span></span>  
 <span data-ttu-id="ed1ab-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ed1ab-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed1ab-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed1ab-110">Requirements</span></span>  
 <span data-ttu-id="ed1ab-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ed1ab-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1ab-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed1ab-112">See Also</span></span>  
 [<span data-ttu-id="ed1ab-113">Isymunmanagedasyncmethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed1ab-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
