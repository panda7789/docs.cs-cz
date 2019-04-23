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
ms.openlocfilehash: bcd200b7fa431f193dd202c3c2a690aa22ec8e32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135175"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="87434-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="87434-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="87434-103">Získá metodu čtečky symbolů daný token metody a číslo verze edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="87434-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="87434-104">Čísla verzí začínají znakem 1 a jsou zvětšeny pokaždé, když metoda se změnilo v důsledku operace edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="87434-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87434-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87434-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87434-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87434-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="87434-107">[in] Metoda token metadat.</span><span class="sxs-lookup"><span data-stu-id="87434-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="87434-108">[in] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="87434-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="87434-109">[out] Ukazatel na vrácenou [isymunmanagedmethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87434-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87434-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87434-110">Return Value</span></span>  
 <span data-ttu-id="87434-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="87434-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87434-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87434-112">Requirements</span></span>  
 <span data-ttu-id="87434-113">**Záhlaví:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="87434-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="87434-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87434-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87434-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87434-115">See also</span></span>

- [<span data-ttu-id="87434-116">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87434-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
