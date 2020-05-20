---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615303"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="a8ce8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="a8ce8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="a8ce8-103">Získá HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ce8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8ce8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ce8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8ce8-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="a8ce8-106">mimo Ukazatel na HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8ce8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8ce8-107">Return Value</span></span>  
 <span data-ttu-id="a8ce8-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a8ce8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ce8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8ce8-109">Requirements</span></span>  
 <span data-ttu-id="a8ce8-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a8ce8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ce8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8ce8-111">See also</span></span>

- [<span data-ttu-id="a8ce8-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8ce8-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
