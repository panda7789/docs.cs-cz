---
title: ISymUnmanagedWriter4 – rozhraní
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: a656777461c50b5a1593917278eb54abda982dc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134570"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="0aa96-102">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa96-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="0aa96-103">Rozhraní Isymunmanagedwriter4 –</span><span class="sxs-lookup"><span data-stu-id="0aa96-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aa96-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="0aa96-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0aa96-105">Methods</span></span>  
 <span data-ttu-id="0aa96-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="0aa96-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0aa96-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="0aa96-107">Method</span></span>|<span data-ttu-id="0aa96-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0aa96-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0aa96-109">GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="0aa96-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="0aa96-110">Funguje stejně jako [Metoda GetDebugInfo –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněn nulami za ukončovacím znakem null, aby data řetězce měla pevnou velikost `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0aa96-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="0aa96-111">Odsazení je zadáno pouze v případě, že délka řetězce cesty je menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0aa96-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="0aa96-112">To usnadňuje psaní nástrojů, které rozdílují soubory PE.</span><span class="sxs-lookup"><span data-stu-id="0aa96-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0aa96-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0aa96-113">Requirements</span></span>  
 <span data-ttu-id="0aa96-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0aa96-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa96-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aa96-115">See also</span></span>

- [<span data-ttu-id="0aa96-116">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0aa96-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0aa96-117">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa96-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
