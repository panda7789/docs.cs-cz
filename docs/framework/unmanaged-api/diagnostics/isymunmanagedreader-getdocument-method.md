---
title: ISymUnmanagedReader::GetDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a173c23ea33532f05e30d072677715e15d04018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093680"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="805f4-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="805f4-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="805f4-103">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="805f4-103">Finds a document.</span></span> <span data-ttu-id="805f4-104">Jazyk dokumentu, dodavatele a typ jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="805f4-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="805f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="805f4-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="805f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="805f4-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="805f4-107">[in] Adresa URL, která identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="805f4-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="805f4-108">[in] Jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="805f4-108">[in] The document language.</span></span> <span data-ttu-id="805f4-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="805f4-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="805f4-110">[in] Identita dodavatele jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="805f4-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="805f4-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="805f4-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="805f4-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="805f4-112">[in] The type of the document.</span></span> <span data-ttu-id="805f4-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="805f4-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="805f4-114">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="805f4-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="805f4-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="805f4-115">Return Value</span></span>  
 <span data-ttu-id="805f4-116">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="805f4-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="805f4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="805f4-117">Requirements</span></span>  
 <span data-ttu-id="805f4-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="805f4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805f4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="805f4-119">See also</span></span>

- [<span data-ttu-id="805f4-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="805f4-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
