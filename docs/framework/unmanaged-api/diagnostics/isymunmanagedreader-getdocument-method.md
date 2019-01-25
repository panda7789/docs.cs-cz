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
ms.openlocfilehash: ecd11b57d1901c4618ee0d27442753559b85c509
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738102"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="a755f-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="a755f-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="a755f-103">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="a755f-103">Finds a document.</span></span> <span data-ttu-id="a755f-104">Jazyk dokumentu, dodavatele a typ jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="a755f-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a755f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a755f-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a755f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a755f-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="a755f-107">[in] Adresa URL, která identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a755f-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="a755f-108">[in] Jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a755f-108">[in] The document language.</span></span> <span data-ttu-id="a755f-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a755f-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="a755f-110">[in] Identita dodavatele jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a755f-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="a755f-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a755f-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="a755f-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a755f-112">[in] The type of the document.</span></span> <span data-ttu-id="a755f-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="a755f-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a755f-114">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a755f-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a755f-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a755f-115">Return Value</span></span>  
 <span data-ttu-id="a755f-116">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a755f-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a755f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a755f-117">Requirements</span></span>  
 <span data-ttu-id="a755f-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a755f-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a755f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a755f-119">See also</span></span>
- [<span data-ttu-id="a755f-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a755f-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
