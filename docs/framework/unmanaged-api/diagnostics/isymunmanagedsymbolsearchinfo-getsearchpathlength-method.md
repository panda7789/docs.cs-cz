---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 58a788d8ef96a52c0b1bc361a97013f27c2809da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="4534e-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="4534e-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="4534e-103">Získá délku cesty vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="4534e-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4534e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4534e-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4534e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4534e-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="4534e-106">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat délka cesty vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="4534e-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4534e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4534e-107">Return Value</span></span>  
 <span data-ttu-id="4534e-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4534e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4534e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4534e-109">Requirements</span></span>  
 <span data-ttu-id="4534e-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4534e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4534e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4534e-111">See Also</span></span>  
 [<span data-ttu-id="4534e-112">Isymunmanagedsymbolsearchinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4534e-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
