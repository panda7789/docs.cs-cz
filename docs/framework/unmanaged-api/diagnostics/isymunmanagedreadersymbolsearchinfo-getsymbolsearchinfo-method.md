---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: 2b5a42c89e0e3efed61b1b471c227e0df85a51aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614900"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="2bdd9-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2bdd9-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="2bdd9-103">Získá informace o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="2bdd9-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bdd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bdd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bdd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bdd9-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="2bdd9-106">pro `ULONG32`Který označuje velikost `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="2bdd9-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="2bdd9-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je nutná k uložení vyhledávacích informací.</span><span class="sxs-lookup"><span data-stu-id="2bdd9-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="2bdd9-108">mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2bdd9-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bdd9-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2bdd9-109">Return Value</span></span>  
 <span data-ttu-id="2bdd9-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="2bdd9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bdd9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bdd9-111">Requirements</span></span>  
 <span data-ttu-id="2bdd9-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2bdd9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bdd9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bdd9-113">See also</span></span>

- [<span data-ttu-id="2bdd9-114">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bdd9-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
