---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f4b760f2782cf75cf0ab0879eb77e185a93b8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="4ec31-102">ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4ec31-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="4ec31-103">Získá název souboru pro přidružené posun řádku.</span><span class="sxs-lookup"><span data-stu-id="4ec31-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ec31-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ec31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ec31-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="4ec31-106">[v] A `ULONG32` obsahující posun.</span><span class="sxs-lookup"><span data-stu-id="4ec31-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4ec31-107">[v] A `ULONG32` určující velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4ec31-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4ec31-108">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="4ec31-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="4ec31-109">[out] Vyrovnávací paměť, která obsahuje názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="4ec31-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ec31-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ec31-110">Return Value</span></span>  
 <span data-ttu-id="4ec31-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4ec31-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec31-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ec31-112">Requirements</span></span>  
 <span data-ttu-id="4ec31-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4ec31-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec31-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ec31-114">See Also</span></span>  
 [<span data-ttu-id="4ec31-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ec31-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
