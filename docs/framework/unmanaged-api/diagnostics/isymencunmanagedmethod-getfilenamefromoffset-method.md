---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df1e9d317294127a931bebf100295290a0dd6b23
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471830"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="cdcdb-102">ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="cdcdb-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="cdcdb-103">Získá název souboru pro řádek spojený s posunem.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdcdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdcdb-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdcdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdcdb-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="cdcdb-106">[in] A `ULONG32` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cdcdb-107">[in] A `ULONG32` , který označuje velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cdcdb-108">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="cdcdb-109">[out] Vyrovnávací paměť, která obsahuje názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdcdb-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cdcdb-110">Return Value</span></span>  
 <span data-ttu-id="cdcdb-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cdcdb-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdcdb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdcdb-112">Requirements</span></span>  
 <span data-ttu-id="cdcdb-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cdcdb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdcdb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdcdb-114">See also</span></span>
- [<span data-ttu-id="cdcdb-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdcdb-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
