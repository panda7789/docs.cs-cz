---
title: ISymUnmanagedDispose – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e81cea13fb8d25701ccbe163f112904baf47a9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939916"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="e01d7-102">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e01d7-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="e01d7-103">Uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="e01d7-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e01d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e01d7-104">Methods</span></span>  
  
|<span data-ttu-id="e01d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e01d7-105">Method</span></span>|<span data-ttu-id="e01d7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e01d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e01d7-107">Destroy – metoda</span><span class="sxs-lookup"><span data-stu-id="e01d7-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="e01d7-108">Způsobí, že základní objekt a uvolnit všechny vnitřní odkazy na všechna volání další metody, vrátí hodnotu neúspěch.</span><span class="sxs-lookup"><span data-stu-id="e01d7-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e01d7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e01d7-109">Requirements</span></span>  
 <span data-ttu-id="e01d7-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e01d7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01d7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e01d7-111">See also</span></span>

- [<span data-ttu-id="e01d7-112">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="e01d7-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
