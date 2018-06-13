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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a63700abf77d56134ca30620033c398af735599
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426736"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="00571-102">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00571-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="00571-103">Pro modul poskytuje data zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="00571-103">Provides source server data for a module.</span></span> <span data-ttu-id="00571-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00571-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00571-105">Metody</span><span class="sxs-lookup"><span data-stu-id="00571-105">Methods</span></span>  
  
|<span data-ttu-id="00571-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="00571-106">Method</span></span>|<span data-ttu-id="00571-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00571-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00571-108">GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="00571-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="00571-109">Vrátí zdroje dat serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="00571-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00571-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00571-110">Requirements</span></span>  
 <span data-ttu-id="00571-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00571-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00571-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="00571-112">See Also</span></span>  
 [<span data-ttu-id="00571-113">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="00571-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
