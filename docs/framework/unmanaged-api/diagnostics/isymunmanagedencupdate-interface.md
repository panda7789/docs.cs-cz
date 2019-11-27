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
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449002"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="33460-102">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33460-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="33460-103">Poskytuje funkce pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="33460-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33460-104">Metody</span><span class="sxs-lookup"><span data-stu-id="33460-104">Methods</span></span>  
  
|<span data-ttu-id="33460-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="33460-105">Method</span></span>|<span data-ttu-id="33460-106">Popis</span><span class="sxs-lookup"><span data-stu-id="33460-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33460-107">GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="33460-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="33460-108">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="33460-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="33460-109">GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="33460-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="33460-110">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="33460-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="33460-111">InitializeForEnc – metoda</span><span class="sxs-lookup"><span data-stu-id="33460-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="33460-112">Umožňuje vypočítat hranice metod před prvním voláním metody [ISymUnmanagedENCUpdate:: updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33460-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="33460-113">UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="33460-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="33460-114">Umožňuje aktualizovat informace o řádku pro metodu, která není znovu zkompilována, ale jejíž řádky byly přesunuty nezávisle.</span><span class="sxs-lookup"><span data-stu-id="33460-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="33460-115">Rozdíl pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="33460-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="33460-116">UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="33460-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="33460-117">Umožňuje kompilátoru vynechat funkce, které se nezměnily z datového proudu PDB (program Database) za předpokladu, že informace o řádku splňují požadavky.</span><span class="sxs-lookup"><span data-stu-id="33460-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="33460-118">Správné informace o řádku lze určit pomocí původní informace na řádku PDB a jedna Delta pro všechny řádky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="33460-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33460-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33460-119">Requirements</span></span>  
 <span data-ttu-id="33460-120">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="33460-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33460-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33460-121">See also</span></span>

- [<span data-ttu-id="33460-122">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="33460-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
