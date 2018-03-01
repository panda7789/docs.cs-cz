---
title: "ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4987aeff8a5006bad93db72a04c4195b40ab1a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="fd5b7-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="fd5b7-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="fd5b7-103">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fd5b7-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd5b7-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd5b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd5b7-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="fd5b7-106">[out] Ukazatel HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fd5b7-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd5b7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd5b7-107">Return Value</span></span>  
 <span data-ttu-id="fd5b7-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fd5b7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd5b7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd5b7-109">Requirements</span></span>  
 <span data-ttu-id="fd5b7-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd5b7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5b7-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd5b7-111">See Also</span></span>  
 [<span data-ttu-id="fd5b7-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd5b7-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
