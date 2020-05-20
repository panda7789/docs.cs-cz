---
title: ISymUnmanagedReaderSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: 3f6cea68a4379f8769ccbdbc6911cc5c425d3369
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614874"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="20623-102">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20623-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="20623-103">Poskytuje metody, které získávají informace o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="20623-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="20623-104">Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="20623-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20623-105">Metody</span><span class="sxs-lookup"><span data-stu-id="20623-105">Methods</span></span>  
  
|<span data-ttu-id="20623-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="20623-106">Method</span></span>|<span data-ttu-id="20623-107">Popis</span><span class="sxs-lookup"><span data-stu-id="20623-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20623-108">GetSymbolSearchInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="20623-108">GetSymbolSearchInfo Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="20623-109">Získá informace o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="20623-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="20623-110">GetSymbolSearchInfoCount – metoda</span><span class="sxs-lookup"><span data-stu-id="20623-110">GetSymbolSearchInfoCount Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="20623-111">Získá počet informací o hledání symbolů.</span><span class="sxs-lookup"><span data-stu-id="20623-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20623-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20623-112">Requirements</span></span>  
 <span data-ttu-id="20623-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="20623-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20623-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="20623-114">See also</span></span>

- [<span data-ttu-id="20623-115">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="20623-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
