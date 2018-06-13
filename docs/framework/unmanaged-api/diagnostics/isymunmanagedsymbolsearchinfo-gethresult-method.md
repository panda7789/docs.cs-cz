---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 775f5a2129a635c79a48d5218d5eb91ee83ee779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427880"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="ad017-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="ad017-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="ad017-103">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ad017-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad017-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad017-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad017-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad017-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="ad017-106">[out] Ukazatel HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ad017-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad017-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad017-107">Return Value</span></span>  
 <span data-ttu-id="ad017-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ad017-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad017-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad017-109">Requirements</span></span>  
 <span data-ttu-id="ad017-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ad017-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad017-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad017-111">See Also</span></span>  
 [<span data-ttu-id="ad017-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad017-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
