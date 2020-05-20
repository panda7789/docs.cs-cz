---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: d9431a533a32fd15931072cfbabd10bbc0e6d4ad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610675"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="88371-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="88371-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="88371-103">Získá cestu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="88371-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88371-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88371-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88371-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88371-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="88371-106">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k uložení cesty pro hledání, ve znacích.</span><span class="sxs-lookup"><span data-stu-id="88371-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88371-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="88371-107">Return Value</span></span>  
 <span data-ttu-id="88371-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="88371-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88371-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88371-109">Requirements</span></span>  
 <span data-ttu-id="88371-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="88371-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88371-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="88371-111">See also</span></span>

- [<span data-ttu-id="88371-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88371-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
