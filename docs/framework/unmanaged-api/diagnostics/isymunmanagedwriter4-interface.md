---
title: "ISymUnmanagedWriter4 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="59a76-102">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59a76-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="59a76-103">Isymunmanagedwriter4 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59a76-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59a76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59a76-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="59a76-105">Metody</span><span class="sxs-lookup"><span data-stu-id="59a76-105">Methods</span></span>  
 <span data-ttu-id="59a76-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="59a76-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="59a76-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="59a76-107">Method</span></span>|<span data-ttu-id="59a76-108">Popis</span><span class="sxs-lookup"><span data-stu-id="59a76-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59a76-109">GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="59a76-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="59a76-110">Funguje stejně jako [getdebuginfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněno nulami následující ukončující znak hodnoty null tak, aby data řetězec pevnou velikost `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="59a76-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="59a76-111">Odsazení je poskytnuta pouze v případě délka řetězce cesty, samotné je menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="59a76-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="59a76-112">To usnadňuje vytvoření nástrojů pro tento rozdíl PE soubory.</span><span class="sxs-lookup"><span data-stu-id="59a76-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59a76-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59a76-113">Requirements</span></span>  
 <span data-ttu-id="59a76-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59a76-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59a76-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="59a76-115">See Also</span></span>  
 [<span data-ttu-id="59a76-116">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="59a76-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="59a76-117">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59a76-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
