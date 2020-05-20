---
title: ISymUnmanagedReader::GetMethodByVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 60fbccabd21fb8bee118689a524efa9031bb2124
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614991"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="6ce35-102">ISymUnmanagedReader::GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="6ce35-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="6ce35-103">Získá metodu čtečky symbolů s ohledem na token metody a číslo verze pro úpravy a kopírování.</span><span class="sxs-lookup"><span data-stu-id="6ce35-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="6ce35-104">Čísla verzí začínají 1 a jsou zvýšena pokaždé, když je metoda změněna v důsledku operace Edit-and-Copy.</span><span class="sxs-lookup"><span data-stu-id="6ce35-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ce35-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ce35-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ce35-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="6ce35-107">pro Token metody.</span><span class="sxs-lookup"><span data-stu-id="6ce35-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="6ce35-108">pro Verze metody</span><span class="sxs-lookup"><span data-stu-id="6ce35-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6ce35-109">mimo Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ce35-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ce35-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ce35-110">Return Value</span></span>  
 <span data-ttu-id="6ce35-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="6ce35-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce35-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ce35-112">Requirements</span></span>  
 <span data-ttu-id="6ce35-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6ce35-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce35-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ce35-114">See also</span></span>

- [<span data-ttu-id="6ce35-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ce35-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
