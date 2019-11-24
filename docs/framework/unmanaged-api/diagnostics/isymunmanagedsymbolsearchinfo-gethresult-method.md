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
ms.openlocfilehash: 21f6cf18ee7d883e1792b597e08724946f53eda9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446186"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="e2d22-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="e2d22-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="e2d22-103">Gets the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e2d22-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2d22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2d22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2d22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2d22-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="e2d22-106">[out] A pointer to the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e2d22-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2d22-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2d22-107">Return Value</span></span>  
 <span data-ttu-id="e2d22-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="e2d22-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2d22-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2d22-109">Requirements</span></span>  
 <span data-ttu-id="e2d22-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2d22-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d22-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2d22-111">See also</span></span>

- [<span data-ttu-id="e2d22-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2d22-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
