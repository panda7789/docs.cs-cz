---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c87ef1b3ce185c2a92813f231abe6a9ef14ac055
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="cdd68-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="cdd68-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="cdd68-103">Získá počet informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="cdd68-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdd68-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdd68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdd68-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="cdd68-106">[limit]] ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti musí obsahovat informace o vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="cdd68-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdd68-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cdd68-107">Return Value</span></span>  
 <span data-ttu-id="cdd68-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cdd68-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdd68-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdd68-109">Requirements</span></span>  
 <span data-ttu-id="cdd68-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cdd68-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd68-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdd68-111">See Also</span></span>  
 [<span data-ttu-id="cdd68-112">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdd68-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
