---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b59d85227f21bb230333456eda9130416563111
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180527"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="48236-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="48236-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="48236-103">Získá počet informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="48236-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48236-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48236-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48236-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48236-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="48236-106">[out]] ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat informace o vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="48236-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48236-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48236-107">Return Value</span></span>  
 <span data-ttu-id="48236-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="48236-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48236-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48236-109">Requirements</span></span>  
 <span data-ttu-id="48236-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48236-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48236-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48236-111">See also</span></span>

- [<span data-ttu-id="48236-112">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48236-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
