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
ms.openlocfilehash: 02b270677131d0960db67b0ac8db38cba2b5e2df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428054"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="b993f-102">ISymUnmanagedWriter::DefineDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="b993f-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="b993f-103">Definuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="b993f-103">Defines a source document.</span></span> <span data-ttu-id="b993f-104">Pro známé jazyky, dodavatele a typy dokumentů jsou k dispozici identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="b993f-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b993f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b993f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b993f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b993f-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="b993f-107">pro Ukazatel na `WCHAR` definující adresu URL (Uniform Resource Locator), která identifikuje dokument.</span><span class="sxs-lookup"><span data-stu-id="b993f-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="b993f-108">pro Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b993f-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="b993f-109">pro Ukazatel na identifikátor GUID, který definuje identitu dodavatele pro jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b993f-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="b993f-110">pro Ukazatel na identifikátor GUID definující typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b993f-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b993f-111">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b993f-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b993f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b993f-112">Return Value</span></span>  
 <span data-ttu-id="b993f-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b993f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b993f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b993f-114">Requirements</span></span>  
 <span data-ttu-id="b993f-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b993f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b993f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b993f-116">See also</span></span>

- [<span data-ttu-id="b993f-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b993f-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
