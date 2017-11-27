---
title: "ISymUnmanagedReader::GetDocuments – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocuments
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27268b7f32f2c9aa667790c6d4516f1b8e015f96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="d566c-102">ISymUnmanagedReader::GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="d566c-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="d566c-103">Vrátí pole všech dokumentů, které jsou definované v úložišti symbol.</span><span class="sxs-lookup"><span data-stu-id="d566c-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d566c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d566c-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d566c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d566c-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="d566c-106">[v] Velikost `pDocs` pole.</span><span class="sxs-lookup"><span data-stu-id="d566c-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="d566c-107">[out] Ukazatel na proměnnou, která přijímá délka pole.</span><span class="sxs-lookup"><span data-stu-id="d566c-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="d566c-108">[out] Ukazatel na proměnnou, která přijímá pole dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d566c-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d566c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d566c-109">Return Value</span></span>  
 <span data-ttu-id="d566c-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d566c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d566c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d566c-111">Requirements</span></span>  
 <span data-ttu-id="d566c-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d566c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d566c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d566c-113">See Also</span></span>  
 [<span data-ttu-id="d566c-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d566c-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
