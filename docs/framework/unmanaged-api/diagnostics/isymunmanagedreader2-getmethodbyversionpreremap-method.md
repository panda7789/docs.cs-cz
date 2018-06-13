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
ms.openlocfilehash: efa34d262157faed2e05cd6e7517c259cd279146
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428573"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="ffaa0-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="ffaa0-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="ffaa0-103">Získá metody čtečky symbol, zadaný token metoda a čísla verze upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="ffaa0-104">Čísla verzí začínají znakem 1 a je zvýšen pokaždé, když metoda mění v důsledku operace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffaa0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffaa0-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffaa0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffaa0-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="ffaa0-107">[v] Metoda token metadat.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="ffaa0-108">[v] Metoda verze.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ffaa0-109">[out] Ukazatel na vrácený [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffaa0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ffaa0-110">Return Value</span></span>  
 <span data-ttu-id="ffaa0-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffaa0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffaa0-112">Requirements</span></span>  
 <span data-ttu-id="ffaa0-113">**Záhlaví:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="ffaa0-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="ffaa0-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ffaa0-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffaa0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffaa0-115">See Also</span></span>  
 [<span data-ttu-id="ffaa0-116">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffaa0-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
