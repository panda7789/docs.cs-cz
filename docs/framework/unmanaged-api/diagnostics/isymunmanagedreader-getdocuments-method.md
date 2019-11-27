---
title: ISymUnmanagedReader::GetDocuments – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: c26c0a5f8c597613266e2e6d1998edfca8f17b82
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448338"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="832f9-102">ISymUnmanagedReader::GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="832f9-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="832f9-103">Vrátí pole všech dokumentů definovaných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="832f9-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="832f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="832f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="832f9-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="832f9-106">pro Velikost pole `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="832f9-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="832f9-107">mimo Ukazatel na proměnnou, která přijímá délku pole.</span><span class="sxs-lookup"><span data-stu-id="832f9-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="832f9-108">mimo Ukazatel na proměnnou, která přijímá pole dokumentu.</span><span class="sxs-lookup"><span data-stu-id="832f9-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="832f9-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="832f9-109">Return Value</span></span>  
 <span data-ttu-id="832f9-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="832f9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="832f9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="832f9-111">Requirements</span></span>  
 <span data-ttu-id="832f9-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="832f9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832f9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="832f9-113">See also</span></span>

- [<span data-ttu-id="832f9-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="832f9-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
