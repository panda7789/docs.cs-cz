---
title: ISymUnmanagedWriter4 – rozhraní
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202031"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="0162b-102">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0162b-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="0162b-103">Isymunmanagedwriter4 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0162b-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0162b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0162b-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="0162b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0162b-105">Methods</span></span>  
 <span data-ttu-id="0162b-106">Toto rozhraní obsahuje následující dvě metody:</span><span class="sxs-lookup"><span data-stu-id="0162b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0162b-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="0162b-107">Method</span></span>|<span data-ttu-id="0162b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0162b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0162b-109">GetDebugInfoWithPadding – metoda</span><span class="sxs-lookup"><span data-stu-id="0162b-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="0162b-110">Funguje stejně jako [GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty doplněno nulami po ukončujícího znaku null na pevnou velikost, aby se data řetězce `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0162b-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="0162b-111">Odsazení je uveden pouze pokud je délka řetězec cesty, samotný menší než `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0162b-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="0162b-112">Díky tomu je snazší psát nástroje tento rozdíl PE soubory.</span><span class="sxs-lookup"><span data-stu-id="0162b-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0162b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0162b-113">Requirements</span></span>  
 <span data-ttu-id="0162b-114">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0162b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0162b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0162b-115">See also</span></span>

- [<span data-ttu-id="0162b-116">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="0162b-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0162b-117">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0162b-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
