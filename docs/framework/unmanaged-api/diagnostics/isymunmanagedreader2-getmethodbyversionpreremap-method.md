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
ms.openlocfilehash: b12ecfdaf7c90589ce2e96b39f7437444cb91b09
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615420"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="e910b-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="e910b-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="e910b-103">Získá metodu čtečky symbolů s ohledem na token metody a číslo verze Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="e910b-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="e910b-104">Čísla verzí začínají 1 a jsou zvýšena pokaždé, když je metoda změněna v důsledku operace Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="e910b-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e910b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e910b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e910b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e910b-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e910b-107">pro Token metadat metody.</span><span class="sxs-lookup"><span data-stu-id="e910b-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="e910b-108">pro Verze metody</span><span class="sxs-lookup"><span data-stu-id="e910b-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e910b-109">mimo Ukazatel na vrácené rozhraní [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e910b-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e910b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e910b-110">Return Value</span></span>  
 <span data-ttu-id="e910b-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e910b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e910b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e910b-112">Requirements</span></span>  
 <span data-ttu-id="e910b-113">**Hlavička:** CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="e910b-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="e910b-114">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e910b-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e910b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e910b-115">See also</span></span>

- [<span data-ttu-id="e910b-116">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e910b-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
