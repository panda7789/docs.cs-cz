---
title: ISymUnmanagedReader::GetDocuments – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 629f9a62364729984a7eec86090876c3eaebb881
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464552"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="e295b-102">ISymUnmanagedReader::GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="e295b-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="e295b-103">Vrací pole všech dokumentů, které jsou definovány v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="e295b-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e295b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e295b-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e295b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e295b-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="e295b-106">[in] Velikost `pDocs` pole.</span><span class="sxs-lookup"><span data-stu-id="e295b-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="e295b-107">[out] Ukazovat na proměnnou, která přijímá délka pole.</span><span class="sxs-lookup"><span data-stu-id="e295b-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="e295b-108">[out] Ukazovat na proměnnou, která přijímá pole dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e295b-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e295b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e295b-109">Return Value</span></span>  
 <span data-ttu-id="e295b-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e295b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e295b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e295b-111">Requirements</span></span>  
 <span data-ttu-id="e295b-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e295b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e295b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e295b-113">See also</span></span>
- [<span data-ttu-id="e295b-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e295b-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
