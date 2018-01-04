---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="784da-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="784da-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="784da-103">Nastaví počáteční metody, která zahájí asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="784da-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="784da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="784da-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="784da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="784da-105">Parameters</span></span>  
  
|<span data-ttu-id="784da-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="784da-106">Parameter</span></span>|<span data-ttu-id="784da-107">Popis</span><span class="sxs-lookup"><span data-stu-id="784da-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="784da-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="784da-108">Return Value</span></span>  
 <span data-ttu-id="784da-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="784da-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="784da-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="784da-110">Requirements</span></span>  
 <span data-ttu-id="784da-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="784da-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784da-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="784da-112">See Also</span></span>  
 [<span data-ttu-id="784da-113">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="784da-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
