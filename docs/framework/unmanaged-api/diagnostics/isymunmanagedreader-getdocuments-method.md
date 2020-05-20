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
ms.openlocfilehash: b8a3a74888a3caae03da6f88a003bd277939ae59
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615043"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="f6b57-102">ISymUnmanagedReader::GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="f6b57-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="f6b57-103">Vrátí pole všech dokumentů definovaných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="f6b57-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6b57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6b57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6b57-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="f6b57-106">pro Velikost `pDocs` pole.</span><span class="sxs-lookup"><span data-stu-id="f6b57-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="f6b57-107">mimo Ukazatel na proměnnou, která přijímá délku pole.</span><span class="sxs-lookup"><span data-stu-id="f6b57-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="f6b57-108">mimo Ukazatel na proměnnou, která přijímá pole dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f6b57-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6b57-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6b57-109">Return Value</span></span>  
 <span data-ttu-id="f6b57-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f6b57-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b57-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6b57-111">Requirements</span></span>  
 <span data-ttu-id="f6b57-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f6b57-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b57-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6b57-113">See also</span></span>

- [<span data-ttu-id="f6b57-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6b57-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
