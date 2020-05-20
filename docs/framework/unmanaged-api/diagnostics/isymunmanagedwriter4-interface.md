---
title: ISymUnmanagedWriter4 – rozhraní
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609466"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="ef6ba-102">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef6ba-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="ef6ba-103">Rozhraní Isymunmanagedwriter4 –</span><span class="sxs-lookup"><span data-stu-id="ef6ba-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef6ba-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="ef6ba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ef6ba-105">Methods</span></span>  
 <span data-ttu-id="ef6ba-106">Toto rozhraní obsahuje následující metody:</span><span class="sxs-lookup"><span data-stu-id="ef6ba-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ef6ba-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="ef6ba-107">Method</span></span>|<span data-ttu-id="ef6ba-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ef6ba-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef6ba-109">GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="ef6ba-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="ef6ba-110">Funguje stejně jako [Metoda GetDebugInfo –](isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty je doplněn nulami za ukončovacím znakem null, aby data řetězce měla pevnou velikost `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="ef6ba-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="ef6ba-111">Odsazení je zadáno pouze v případě, že délka řetězce cesty je menší než `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="ef6ba-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="ef6ba-112">To usnadňuje psaní nástrojů, které rozdílují soubory PE.</span><span class="sxs-lookup"><span data-stu-id="ef6ba-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef6ba-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef6ba-113">Requirements</span></span>  
 <span data-ttu-id="ef6ba-114">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ef6ba-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6ba-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef6ba-115">See also</span></span>

- [<span data-ttu-id="ef6ba-116">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ef6ba-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ef6ba-117">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef6ba-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
