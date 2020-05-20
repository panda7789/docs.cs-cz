---
title: ISymUnmanagedENCUpdate – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: aa4fe2185ead7edfa47d4194799c930193e04076
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614523"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="131e5-102">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="131e5-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="131e5-103">Poskytuje funkce pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="131e5-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="131e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="131e5-104">Methods</span></span>  
  
|<span data-ttu-id="131e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-105">Method</span></span>|<span data-ttu-id="131e5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="131e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="131e5-107">GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="131e5-108">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="131e5-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="131e5-109">GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="131e5-110">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="131e5-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="131e5-111">InitializeForEnc – metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="131e5-112">Umožňuje vypočítat hranice metod před prvním voláním metody [ISymUnmanagedENCUpdate:: updatesymbolstore2 –](isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="131e5-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="131e5-113">UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="131e5-114">Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle.</span><span class="sxs-lookup"><span data-stu-id="131e5-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="131e5-115">Rozdíl pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="131e5-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="131e5-116">UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="131e5-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="131e5-117">Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database) za předpokladu, že informace o řádku splňují požadavky.</span><span class="sxs-lookup"><span data-stu-id="131e5-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="131e5-118">Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="131e5-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="131e5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="131e5-119">Requirements</span></span>  
 <span data-ttu-id="131e5-120">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="131e5-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131e5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="131e5-121">See also</span></span>

- [<span data-ttu-id="131e5-122">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="131e5-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
