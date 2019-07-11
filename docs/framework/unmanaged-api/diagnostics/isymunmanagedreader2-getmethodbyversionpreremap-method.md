---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06b8ebf26794baa1d957cc47d1179283611b62d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736680"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="aeeaf-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="aeeaf-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="aeeaf-103">Získá metodu čtečky symbolů daný token metody a číslo verze edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="aeeaf-104">Čísla verzí začínají znakem 1 a jsou zvětšeny pokaždé, když metoda se změnilo v důsledku operace edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeeaf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeeaf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeeaf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aeeaf-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="aeeaf-107">[in] Metoda token metadat.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="aeeaf-108">[in] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="aeeaf-109">[out] Ukazatel na vrácenou [isymunmanagedmethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeeaf-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aeeaf-110">Return Value</span></span>  
 <span data-ttu-id="aeeaf-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeeaf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aeeaf-112">Requirements</span></span>  
 <span data-ttu-id="aeeaf-113">**Záhlaví:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="aeeaf-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="aeeaf-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aeeaf-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeeaf-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aeeaf-115">See also</span></span>

- [<span data-ttu-id="aeeaf-116">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeeaf-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
