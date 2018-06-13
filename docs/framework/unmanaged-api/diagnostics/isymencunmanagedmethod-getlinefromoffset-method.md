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
ms.openlocfilehash: 29990ad6a94f063577236bdbc84d02d4d2b4b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426130"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="1603e-102">ISymENCUnmanagedMethod::GetLineFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1603e-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="1603e-103">Získá související s posunem informace řádku.</span><span class="sxs-lookup"><span data-stu-id="1603e-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="1603e-104">Pokud parametr posunutí (`dwOffset`) není bod sekvence, tato metoda získá řádku informace spojené s posunem od předchozí.</span><span class="sxs-lookup"><span data-stu-id="1603e-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1603e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1603e-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1603e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1603e-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="1603e-107">[v] A `ULONG32` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="1603e-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="1603e-108">[out] Ukazatel na `ULONG32` která přijme řádku.</span><span class="sxs-lookup"><span data-stu-id="1603e-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="1603e-109">[out] Ukazatel na `ULONG32` která přijme sloupci.</span><span class="sxs-lookup"><span data-stu-id="1603e-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="1603e-110">[out] Ukazatel na `ULONG32` která přijme na konci řádku.</span><span class="sxs-lookup"><span data-stu-id="1603e-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="1603e-111">[out] Ukazatel na `ULONG32` která přijme sloupec end.</span><span class="sxs-lookup"><span data-stu-id="1603e-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="1603e-112">[out] Ukazatel na `ULONG32` která přijme bodem přidružené pořadí.</span><span class="sxs-lookup"><span data-stu-id="1603e-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1603e-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1603e-113">Return Value</span></span>  
 <span data-ttu-id="1603e-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1603e-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1603e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1603e-115">Requirements</span></span>  
 <span data-ttu-id="1603e-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1603e-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1603e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1603e-117">See Also</span></span>  
 [<span data-ttu-id="1603e-118">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1603e-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
