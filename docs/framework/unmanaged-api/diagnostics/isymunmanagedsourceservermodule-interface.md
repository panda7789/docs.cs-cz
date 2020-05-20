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
ms.openlocfilehash: d90a55b53ba00540137e44fc190790c4710903e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610792"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="03858-102">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03858-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="03858-103">Poskytuje data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="03858-103">Provides source server data for a module.</span></span> <span data-ttu-id="03858-104">Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="03858-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03858-105">Metody</span><span class="sxs-lookup"><span data-stu-id="03858-105">Methods</span></span>  
  
|<span data-ttu-id="03858-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="03858-106">Method</span></span>|<span data-ttu-id="03858-107">Popis</span><span class="sxs-lookup"><span data-stu-id="03858-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03858-108">GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="03858-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="03858-109">Vrátí data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="03858-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03858-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03858-110">Requirements</span></span>  
 <span data-ttu-id="03858-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="03858-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03858-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="03858-112">See also</span></span>

- [<span data-ttu-id="03858-113">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="03858-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
