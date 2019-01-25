---
title: ISymUnmanagedWriter::DefineDocument – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1c214918b4a41ac989a3804c9146c4a54c5909f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738206"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="c6018-102">ISymUnmanagedWriter::DefineDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="c6018-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="c6018-103">Definuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="c6018-103">Defines a source document.</span></span> <span data-ttu-id="c6018-104">Identifikátory GUID jsou k dispozici pro známé jazyky, dodavatele a typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="c6018-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6018-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6018-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6018-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6018-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="c6018-107">[in] Ukazatel `WCHAR` , který určuje adresu uniform resource locator (URL), který identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c6018-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="c6018-108">[in] Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c6018-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="c6018-109">[in] Ukazatel na identifikátor GUID, který definuje totožnost dodavatele jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c6018-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="c6018-110">[in] Ukazatel na identifikátor GUID, který definuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c6018-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c6018-111">[out] Ukazatel na vrácenou [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6018-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6018-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6018-112">Return Value</span></span>  
 <span data-ttu-id="c6018-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c6018-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6018-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6018-114">Requirements</span></span>  
 <span data-ttu-id="c6018-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c6018-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6018-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6018-116">See also</span></span>
- [<span data-ttu-id="c6018-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6018-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
