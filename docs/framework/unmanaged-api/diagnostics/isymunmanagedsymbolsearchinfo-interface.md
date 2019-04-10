---
title: ISymUnmanagedSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d573264bb7a3cac02dd41afacaa2bc4a6f9e6dcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207542"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="a828b-102">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a828b-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="a828b-103">Poskytuje metody, které získáte informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="a828b-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="a828b-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a828b-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a828b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a828b-105">Methods</span></span>  
  
|<span data-ttu-id="a828b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a828b-106">Method</span></span>|<span data-ttu-id="a828b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a828b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a828b-108">GetHRESULT – metoda</span><span class="sxs-lookup"><span data-stu-id="a828b-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="a828b-109">Získá hodnota HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a828b-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="a828b-110">GetSearchPath – metoda</span><span class="sxs-lookup"><span data-stu-id="a828b-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="a828b-111">Získá cestu hledání.</span><span class="sxs-lookup"><span data-stu-id="a828b-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="a828b-112">GetSearchPathLength – metoda</span><span class="sxs-lookup"><span data-stu-id="a828b-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="a828b-113">Získá délku cesty hledání.</span><span class="sxs-lookup"><span data-stu-id="a828b-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a828b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a828b-114">Requirements</span></span>  
 <span data-ttu-id="a828b-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a828b-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a828b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a828b-116">See also</span></span>

- [<span data-ttu-id="a828b-117">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="a828b-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
