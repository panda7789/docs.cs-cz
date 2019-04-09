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
ms.openlocfilehash: 3ba81c208c4b49342c6a055e09ba898871db1851
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157602"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="7f0f8-102">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f0f8-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="7f0f8-103">Pro modul poskytuje data zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="7f0f8-103">Provides source server data for a module.</span></span> <span data-ttu-id="7f0f8-104">Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7f0f8-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f0f8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7f0f8-105">Methods</span></span>  
  
|<span data-ttu-id="7f0f8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7f0f8-106">Method</span></span>|<span data-ttu-id="7f0f8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7f0f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f0f8-108">GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="7f0f8-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="7f0f8-109">Vrací data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="7f0f8-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f0f8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f0f8-110">Requirements</span></span>  
 <span data-ttu-id="7f0f8-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f0f8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f0f8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f0f8-112">See also</span></span>

- [<span data-ttu-id="7f0f8-113">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7f0f8-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
