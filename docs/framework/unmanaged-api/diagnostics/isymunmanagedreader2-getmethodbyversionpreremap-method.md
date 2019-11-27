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
ms.openlocfilehash: 2063856389b122b150a2d2744169a4a567592287
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446447"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="8715b-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="8715b-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="8715b-103">Získá metodu čtečky symbolů s ohledem na token metody a číslo verze Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="8715b-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="8715b-104">Čísla verzí začínají 1 a jsou zvýšena pokaždé, když je metoda změněna v důsledku operace Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="8715b-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8715b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8715b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8715b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8715b-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="8715b-107">pro Token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="8715b-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="8715b-108">pro Verze metody</span><span class="sxs-lookup"><span data-stu-id="8715b-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8715b-109">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8715b-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8715b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8715b-110">Return Value</span></span>  
 <span data-ttu-id="8715b-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8715b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8715b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8715b-112">Requirements</span></span>  
 <span data-ttu-id="8715b-113">**Hlavička:** CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="8715b-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="8715b-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8715b-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8715b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8715b-115">See also</span></span>

- [<span data-ttu-id="8715b-116">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8715b-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
