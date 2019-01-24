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
ms.openlocfilehash: 15f85a6f5ab418692d747cc9ad415c637d7b96e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614362"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="4d55e-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="4d55e-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="4d55e-103">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4d55e-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d55e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d55e-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d55e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d55e-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="4d55e-106">[out] Ukazatel na HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4d55e-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d55e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4d55e-107">Return Value</span></span>  
 <span data-ttu-id="4d55e-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4d55e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d55e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d55e-109">Requirements</span></span>  
 <span data-ttu-id="4d55e-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d55e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d55e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d55e-111">See also</span></span>
- [<span data-ttu-id="4d55e-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d55e-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
