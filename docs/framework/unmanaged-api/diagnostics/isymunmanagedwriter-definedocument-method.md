---
title: "ISymUnmanagedWriter::DefineDocument – metoda"
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
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 522cc3a63101ec7ebe47e8e23878b9d1b12bca1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="a7aa8-102">ISymUnmanagedWriter::DefineDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="a7aa8-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="a7aa8-103">Definuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-103">Defines a source document.</span></span> <span data-ttu-id="a7aa8-104">Identifikátory GUID jsou uvedené známé jazyky, dodavateli a typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7aa8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7aa8-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7aa8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7aa8-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="a7aa8-107">[v] Ukazatel na `WCHAR` uniform resource locator (URL), který identifikuje dokumentu, který definuje.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="a7aa8-108">[v] Ukazatel na identifikátor GUID, který definuje jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="a7aa8-109">[v] Ukazatel na identifikátor GUID, který definuje identitu dodavatele pro jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="a7aa8-110">[v] Ukazatel na identifikátor GUID, který definuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a7aa8-111">[out] Ukazatel na vrácený [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7aa8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7aa8-112">Return Value</span></span>  
 <span data-ttu-id="a7aa8-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a7aa8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7aa8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7aa8-114">Requirements</span></span>  
 <span data-ttu-id="a7aa8-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7aa8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7aa8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7aa8-116">See Also</span></span>  
 [<span data-ttu-id="a7aa8-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7aa8-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
