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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214770"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="6f93c-102">ISymENCUnmanagedMethod::GetDocumentsForMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="6f93c-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="6f93c-103">Získá dokumenty, které tato metoda má řádky v.</span><span class="sxs-lookup"><span data-stu-id="6f93c-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f93c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f93c-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f93c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f93c-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="6f93c-106">[in] Délka vyrovnávací paměti na které odkazuje `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="6f93c-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="6f93c-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6f93c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="6f93c-108">[in] Vyrovnávací paměť, která obsahuje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6f93c-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f93c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f93c-109">Return Value</span></span>  
 <span data-ttu-id="6f93c-110">Pokud metoda uspěje; S_OK v opačném případě chybový kód.</span><span class="sxs-lookup"><span data-stu-id="6f93c-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f93c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f93c-111">Requirements</span></span>  
 <span data-ttu-id="6f93c-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f93c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f93c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f93c-113">See also</span></span>

- [<span data-ttu-id="6f93c-114">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f93c-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
