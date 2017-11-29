---
title: "ISymUnmanagedReader::GetDocument – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7fcc18b1441093a3e3a1a0e813ccfb4ba3ad507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="431ff-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="431ff-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="431ff-103">Vyhledá dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431ff-103">Finds a document.</span></span> <span data-ttu-id="431ff-104">Jazyk dokumentu, dodavatele a typ jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="431ff-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="431ff-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="431ff-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="431ff-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="431ff-107">[v] Adresa URL, která identifikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431ff-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="431ff-108">[v] Jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431ff-108">[in] The document language.</span></span> <span data-ttu-id="431ff-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="431ff-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="431ff-110">[v] Identita dodavatele pro jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431ff-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="431ff-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="431ff-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="431ff-112">[v] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431ff-112">[in] The type of the document.</span></span> <span data-ttu-id="431ff-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="431ff-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="431ff-114">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="431ff-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="431ff-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="431ff-115">Return Value</span></span>  
 <span data-ttu-id="431ff-116">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="431ff-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="431ff-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="431ff-117">Requirements</span></span>  
 <span data-ttu-id="431ff-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="431ff-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431ff-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="431ff-119">See Also</span></span>  
 [<span data-ttu-id="431ff-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="431ff-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
