---
title: "ISymUnmanagedSourceServerModule – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule
helpviewer_keywords: ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f183c3ea69de15387f729a67328bf5ea57931750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="8bf2e-102">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bf2e-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="8bf2e-103">Pro modul poskytuje data zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="8bf2e-103">Provides source server data for a module.</span></span> <span data-ttu-id="8bf2e-104">Získat toto rozhraní vyvoláním `QueryInterface` na objekt, který implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8bf2e-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bf2e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8bf2e-105">Methods</span></span>  
  
|<span data-ttu-id="8bf2e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8bf2e-106">Method</span></span>|<span data-ttu-id="8bf2e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8bf2e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bf2e-108">GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="8bf2e-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="8bf2e-109">Vrátí zdroje dat serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="8bf2e-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bf2e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bf2e-110">Requirements</span></span>  
 <span data-ttu-id="8bf2e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8bf2e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf2e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bf2e-112">See Also</span></span>  
 [<span data-ttu-id="8bf2e-113">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8bf2e-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
