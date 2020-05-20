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
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615225"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="bed65-102">ISymUnmanagedWriter::DefineDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="bed65-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="bed65-103">Definuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="bed65-103">Defines a source document.</span></span> <span data-ttu-id="bed65-104">Pro známé jazyky, dodavatele a typy dokumentů jsou k dispozici identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="bed65-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed65-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bed65-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed65-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bed65-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="bed65-107">pro Ukazatel na `WCHAR` , který definuje adresu URL (Uniform Resource Locator), která identifikuje dokument.</span><span class="sxs-lookup"><span data-stu-id="bed65-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="bed65-108">pro Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bed65-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="bed65-109">pro Ukazatel na identifikátor GUID, který definuje identitu dodavatele pro jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bed65-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="bed65-110">pro Ukazatel na identifikátor GUID definující typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bed65-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bed65-111">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bed65-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bed65-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bed65-112">Return Value</span></span>  
 <span data-ttu-id="bed65-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="bed65-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed65-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bed65-114">Requirements</span></span>  
 <span data-ttu-id="bed65-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bed65-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed65-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bed65-116">See also</span></span>

- [<span data-ttu-id="bed65-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bed65-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
