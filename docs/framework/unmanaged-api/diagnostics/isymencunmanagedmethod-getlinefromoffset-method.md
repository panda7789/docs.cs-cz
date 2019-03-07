---
title: ISymENCUnmanagedMethod::GetLineFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90d993bc6b947d309ce1a0fb10ad231a429be567
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471911"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="1b94c-102">ISymENCUnmanagedMethod::GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1b94c-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="1b94c-103">Získá informace o řádku, které jsou spojené s posunem.</span><span class="sxs-lookup"><span data-stu-id="1b94c-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="1b94c-104">Pokud parametr offset (`dwOffset`) není bod sekvence, tato metoda získá informace o řádku spojené s předchozím posunu.</span><span class="sxs-lookup"><span data-stu-id="1b94c-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b94c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b94c-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b94c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b94c-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="1b94c-107">[in] A `ULONG32` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="1b94c-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="1b94c-108">[out] Ukazatel `ULONG32` , která obdrží řádku.</span><span class="sxs-lookup"><span data-stu-id="1b94c-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="1b94c-109">[out] Ukazatel `ULONG32` , která obdrží sloupci.</span><span class="sxs-lookup"><span data-stu-id="1b94c-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="1b94c-110">[out] Ukazatel `ULONG32` , který přijímá na konci řádku.</span><span class="sxs-lookup"><span data-stu-id="1b94c-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="1b94c-111">[out] Ukazatel `ULONG32` , která obdrží koncový sloupec.</span><span class="sxs-lookup"><span data-stu-id="1b94c-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="1b94c-112">[out] Ukazatel `ULONG32` , která obdrží bodu sekvence. přidružené.</span><span class="sxs-lookup"><span data-stu-id="1b94c-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b94c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b94c-113">Return Value</span></span>  
 <span data-ttu-id="1b94c-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1b94c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b94c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b94c-115">Requirements</span></span>  
 <span data-ttu-id="1b94c-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1b94c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b94c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b94c-117">See also</span></span>
- [<span data-ttu-id="1b94c-118">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b94c-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
