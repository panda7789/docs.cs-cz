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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628d6fac45b046d9e8f26ad8777c38450da27a1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427415"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="c2c3d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c2c3d-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="c2c3d-103">Získá informace o vyhledávání symbolu.</span><span class="sxs-lookup"><span data-stu-id="c2c3d-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2c3d-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2c3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2c3d-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="c2c3d-106">[v] A `ULONG32` určující velikost `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="c2c3d-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="c2c3d-107">[out] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat informace o vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c2c3d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="c2c3d-108">[out] Ukazatele, který je nastavený s vráceným [isymunmanagedsymbolsearchinfo –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c2c3d-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2c3d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2c3d-109">Return Value</span></span>  
 <span data-ttu-id="c2c3d-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c2c3d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c3d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2c3d-111">Requirements</span></span>  
 <span data-ttu-id="c2c3d-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c2c3d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c3d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2c3d-113">See Also</span></span>  
 [<span data-ttu-id="c2c3d-114">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2c3d-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
