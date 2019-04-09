---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442584cffe4b4ae44702892587e261d41abf4e8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150420"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="36a60-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="36a60-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="36a60-103">Získá spuštění nejmenší číslo řádku a největší na konci řádku pro metodu v určitého dokumentu.</span><span class="sxs-lookup"><span data-stu-id="36a60-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36a60-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36a60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36a60-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="36a60-106">[in] Ukazatel na dokument.</span><span class="sxs-lookup"><span data-stu-id="36a60-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="36a60-107">[out] Ukazatel `ULONG32` , která obdrží start řádku.</span><span class="sxs-lookup"><span data-stu-id="36a60-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="36a60-108">[out] Ukazatel `ULONG32` , který přijímá na konci řádku.</span><span class="sxs-lookup"><span data-stu-id="36a60-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36a60-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36a60-109">Return Value</span></span>  
 <span data-ttu-id="36a60-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="36a60-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36a60-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36a60-111">Requirements</span></span>  
 <span data-ttu-id="36a60-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36a60-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a60-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36a60-113">See also</span></span>

- [<span data-ttu-id="36a60-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36a60-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
