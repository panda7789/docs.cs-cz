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
ms.openlocfilehash: b9a36e094689696b746fcf7f10c282a1b0d9c570
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777835"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="1dd14-102">ISymUnmanagedWriter::DefineDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd14-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="1dd14-103">Definuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="1dd14-103">Defines a source document.</span></span> <span data-ttu-id="1dd14-104">Identifikátory GUID jsou k dispozici pro známé jazyky, dodavatele a typů dokumentů.</span><span class="sxs-lookup"><span data-stu-id="1dd14-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd14-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dd14-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd14-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dd14-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="1dd14-107">[in] Ukazatel `WCHAR` , který určuje adresu uniform resource locator (URL), který identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1dd14-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="1dd14-108">[in] Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1dd14-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="1dd14-109">[in] Ukazatel na identifikátor GUID, který definuje totožnost dodavatele jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1dd14-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="1dd14-110">[in] Ukazatel na identifikátor GUID, který definuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1dd14-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1dd14-111">[out] Ukazatel na vrácenou [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1dd14-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd14-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1dd14-112">Return Value</span></span>  
 <span data-ttu-id="1dd14-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1dd14-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd14-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dd14-114">Requirements</span></span>  
 <span data-ttu-id="1dd14-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1dd14-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd14-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dd14-116">See also</span></span>

- [<span data-ttu-id="1dd14-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dd14-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
