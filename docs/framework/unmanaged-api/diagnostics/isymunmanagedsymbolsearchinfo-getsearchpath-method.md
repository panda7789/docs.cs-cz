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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bf526b4868fc683eac92a84828ae36b02bb3ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479525"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="e5cd9-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="e5cd9-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="e5cd9-103">Získá cestu hledání.</span><span class="sxs-lookup"><span data-stu-id="e5cd9-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5cd9-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5cd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5cd9-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="e5cd9-106">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat cesty pro hledání.</span><span class="sxs-lookup"><span data-stu-id="e5cd9-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5cd9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5cd9-107">Return Value</span></span>  
 <span data-ttu-id="e5cd9-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e5cd9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5cd9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5cd9-109">Requirements</span></span>  
 <span data-ttu-id="e5cd9-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5cd9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cd9-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5cd9-111">See also</span></span>
- [<span data-ttu-id="e5cd9-112">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5cd9-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
