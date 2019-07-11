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
ms.openlocfilehash: e4948a853434b14845983addb0e6fa4012279084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776869"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="ef9ee-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="ef9ee-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="ef9ee-103">Získá spuštění nejmenší číslo řádku a největší na konci řádku pro metodu v určitého dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef9ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef9ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef9ee-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ef9ee-106">[in] Ukazatel na dokument.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="ef9ee-107">[out] Ukazatel `ULONG32` , která obdrží start řádku.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="ef9ee-108">[out] Ukazatel `ULONG32` , který přijímá na konci řádku.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef9ee-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef9ee-109">Return Value</span></span>  
 <span data-ttu-id="ef9ee-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ef9ee-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef9ee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef9ee-111">Requirements</span></span>  
 <span data-ttu-id="ef9ee-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef9ee-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9ee-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef9ee-113">See also</span></span>

- [<span data-ttu-id="ef9ee-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef9ee-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
