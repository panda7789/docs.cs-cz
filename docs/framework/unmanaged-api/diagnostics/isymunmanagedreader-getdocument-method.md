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
ms.openlocfilehash: 1fcb885b6e19457065c2ca9971f068b42f97147d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448342"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="014b6-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="014b6-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="014b6-103">Finds a document.</span><span class="sxs-lookup"><span data-stu-id="014b6-103">Finds a document.</span></span> <span data-ttu-id="014b6-104">The document language, vendor, and type are optional.</span><span class="sxs-lookup"><span data-stu-id="014b6-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="014b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="014b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="014b6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="014b6-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="014b6-107">[in] The URL that identifies the document.</span><span class="sxs-lookup"><span data-stu-id="014b6-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="014b6-108">[in] The document language.</span><span class="sxs-lookup"><span data-stu-id="014b6-108">[in] The document language.</span></span> <span data-ttu-id="014b6-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="014b6-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="014b6-110">[in] The identity of the vendor for the document language.</span><span class="sxs-lookup"><span data-stu-id="014b6-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="014b6-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="014b6-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="014b6-112">[in] The type of the document.</span><span class="sxs-lookup"><span data-stu-id="014b6-112">[in] The type of the document.</span></span> <span data-ttu-id="014b6-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="014b6-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="014b6-114">[out] A pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="014b6-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="014b6-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="014b6-115">Return Value</span></span>  
 <span data-ttu-id="014b6-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="014b6-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="014b6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="014b6-117">Requirements</span></span>  
 <span data-ttu-id="014b6-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="014b6-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014b6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="014b6-119">See also</span></span>

- [<span data-ttu-id="014b6-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="014b6-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
