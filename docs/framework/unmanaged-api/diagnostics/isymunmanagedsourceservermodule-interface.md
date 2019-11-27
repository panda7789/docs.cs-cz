---
title: ISymUnmanagedSourceServerModule – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
ms.openlocfilehash: 9eac87d7627f502b13d805b8c5656e01ac578e7f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446206"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="8b5b5-102">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b5b5-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="8b5b5-103">Poskytuje data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="8b5b5-103">Provides source server data for a module.</span></span> <span data-ttu-id="8b5b5-104">Získejte toto rozhraní voláním `QueryInterface` na objektu, který implementuje rozhraní [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8b5b5-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b5b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8b5b5-105">Methods</span></span>  
  
|<span data-ttu-id="8b5b5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b5b5-106">Method</span></span>|<span data-ttu-id="8b5b5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8b5b5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b5b5-108">GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="8b5b5-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="8b5b5-109">Vrátí data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="8b5b5-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b5b5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b5b5-110">Requirements</span></span>  
 <span data-ttu-id="8b5b5-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8b5b5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b5b5-112">See also</span></span>

- [<span data-ttu-id="8b5b5-113">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8b5b5-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
