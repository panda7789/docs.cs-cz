---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 0be7297fbb71302035e71fbbf2c8b5e2a7faa2da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615290"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="05027-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="05027-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="05027-103">Získá délku cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="05027-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05027-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05027-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05027-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05027-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="05027-106">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k uložení cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="05027-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05027-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05027-107">Return Value</span></span>  
 <span data-ttu-id="05027-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="05027-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05027-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05027-109">Requirements</span></span>  
 <span data-ttu-id="05027-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="05027-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05027-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="05027-111">See also</span></span>

- [<span data-ttu-id="05027-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05027-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
