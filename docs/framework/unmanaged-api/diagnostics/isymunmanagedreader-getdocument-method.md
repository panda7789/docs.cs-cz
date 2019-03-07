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
ms.openlocfilehash: f20f7aabc05bb9e15b040d968c08d10444efd8fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485807"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="f7e9c-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="f7e9c-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="f7e9c-103">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-103">Finds a document.</span></span> <span data-ttu-id="f7e9c-104">Jazyk dokumentu, dodavatele a typ jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e9c-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e9c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7e9c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="f7e9c-107">[in] Adresa URL, která identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="f7e9c-108">[in] Jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-108">[in] The document language.</span></span> <span data-ttu-id="f7e9c-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="f7e9c-110">[in] Identita dodavatele jazyka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="f7e9c-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="f7e9c-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-112">[in] The type of the document.</span></span> <span data-ttu-id="f7e9c-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f7e9c-114">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7e9c-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7e9c-115">Return Value</span></span>  
 <span data-ttu-id="f7e9c-116">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f7e9c-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e9c-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7e9c-117">Requirements</span></span>  
 <span data-ttu-id="f7e9c-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f7e9c-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e9c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7e9c-119">See also</span></span>
- [<span data-ttu-id="f7e9c-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e9c-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
