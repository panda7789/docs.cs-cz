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
ms.openlocfilehash: dd24289f7e670684effa553f930af9aec92e5730
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469597"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="d37b4-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="d37b4-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="d37b4-103">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d37b4-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d37b4-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d37b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d37b4-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="d37b4-106">[out] Ukazatel na HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d37b4-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d37b4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d37b4-107">Return Value</span></span>  
 <span data-ttu-id="d37b4-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d37b4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d37b4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d37b4-109">Requirements</span></span>  
 <span data-ttu-id="d37b4-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d37b4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37b4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d37b4-111">See also</span></span>
- [<span data-ttu-id="d37b4-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d37b4-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
