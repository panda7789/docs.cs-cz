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
ms.openlocfilehash: db119a94cb7df29697836ffda240c29a86922d60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940306"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="06f5e-102">ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="06f5e-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="06f5e-103">Získá dokumenty, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="06f5e-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06f5e-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06f5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06f5e-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="06f5e-106">[in] Délka vyrovnávací paměti na které odkazuje `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="06f5e-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="06f5e-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat dokumenty.</span><span class="sxs-lookup"><span data-stu-id="06f5e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="06f5e-108">[in] Vyrovnávací paměť, která obsahuje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="06f5e-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06f5e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06f5e-109">Return Value</span></span>  
 <span data-ttu-id="06f5e-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="06f5e-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f5e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06f5e-111">Requirements</span></span>  
 <span data-ttu-id="06f5e-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06f5e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f5e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06f5e-113">See also</span></span>

- [<span data-ttu-id="06f5e-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06f5e-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
