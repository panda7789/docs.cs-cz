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
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615056"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="22cae-102">ISymUnmanagedReader::GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="22cae-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="22cae-103">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="22cae-103">Finds a document.</span></span> <span data-ttu-id="22cae-104">Jazyk dokumentu, dodavatel a typ jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="22cae-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22cae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22cae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22cae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="22cae-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="22cae-107">pro Adresa URL, která identifikuje dokument.</span><span class="sxs-lookup"><span data-stu-id="22cae-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="22cae-108">pro Jazyk dokumentu.</span><span class="sxs-lookup"><span data-stu-id="22cae-108">[in] The document language.</span></span> <span data-ttu-id="22cae-109">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="22cae-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="22cae-110">pro Identita dodavatele pro jazyk dokumentu</span><span class="sxs-lookup"><span data-stu-id="22cae-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="22cae-111">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="22cae-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="22cae-112">pro Typ dokumentu</span><span class="sxs-lookup"><span data-stu-id="22cae-112">[in] The type of the document.</span></span> <span data-ttu-id="22cae-113">Tento parametr je volitelný.</span><span class="sxs-lookup"><span data-stu-id="22cae-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="22cae-114">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="22cae-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22cae-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22cae-115">Return Value</span></span>  
 <span data-ttu-id="22cae-116">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="22cae-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22cae-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22cae-117">Requirements</span></span>  
 <span data-ttu-id="22cae-118">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="22cae-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22cae-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="22cae-119">See also</span></span>

- [<span data-ttu-id="22cae-120">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22cae-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
