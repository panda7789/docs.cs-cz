---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8efcd62f39a7de397ef93231fd125a17c7e513e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425074"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="d079b-102">ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d079b-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="d079b-103">Získá dokumenty, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="d079b-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d079b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d079b-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d079b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d079b-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="d079b-106">[v] Délka vyrovnávací paměti na kterou odkazuje `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="d079b-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="d079b-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d079b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="d079b-108">[v] Vyrovnávací paměť, která obsahuje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="d079b-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d079b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d079b-109">Return Value</span></span>  
 <span data-ttu-id="d079b-110">S_OK, pokud metoda úspěšně. jinak kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d079b-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d079b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d079b-111">Requirements</span></span>  
 <span data-ttu-id="d079b-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d079b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d079b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d079b-113">See Also</span></span>  
 [<span data-ttu-id="d079b-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d079b-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
