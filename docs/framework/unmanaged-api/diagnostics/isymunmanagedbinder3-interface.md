---
title: ISymUnmanagedBinder3 – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: e4a415b21e3980e7603319d7acbb3831462fac9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449294"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="937b1-102">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="937b1-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="937b1-103">Extends the symbol binder interface.</span><span class="sxs-lookup"><span data-stu-id="937b1-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="937b1-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="937b1-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="937b1-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span><span class="sxs-lookup"><span data-stu-id="937b1-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="937b1-106">Metody</span><span class="sxs-lookup"><span data-stu-id="937b1-106">Methods</span></span>  
  
|<span data-ttu-id="937b1-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="937b1-107">Method</span></span>|<span data-ttu-id="937b1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="937b1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="937b1-109">GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="937b1-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="937b1-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span><span class="sxs-lookup"><span data-stu-id="937b1-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="937b1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="937b1-111">Requirements</span></span>  
 <span data-ttu-id="937b1-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="937b1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937b1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="937b1-113">See also</span></span>

- [<span data-ttu-id="937b1-114">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="937b1-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="937b1-115">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="937b1-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="937b1-116">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="937b1-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
