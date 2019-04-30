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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 378322c28d59b2a6e7c09f2f2c4bf55bb019d01d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939695"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="12ff5-102">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12ff5-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="12ff5-103">Poskytuje funkce pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="12ff5-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12ff5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12ff5-104">Methods</span></span>  
  
|<span data-ttu-id="12ff5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-105">Method</span></span>|<span data-ttu-id="12ff5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="12ff5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12ff5-107">GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="12ff5-108">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="12ff5-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="12ff5-109">GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="12ff5-110">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="12ff5-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="12ff5-111">InitializeForEnc – metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="12ff5-112">Umožňuje hranice metody vypočítání před prvním volání [isymunmanagedencupdate::updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="12ff5-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="12ff5-113">UpdateMethodLines – metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="12ff5-114">Umožňuje aktualizovat informace o řádku pro metodu, která nebyla překompilovat, ale jejíž řádky přesunuty nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="12ff5-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="12ff5-115">Rozdílové hodnoty pro každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="12ff5-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="12ff5-116">UpdateSymbolStore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="12ff5-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="12ff5-117">Umožňuje kompilátoru chcete vynechat, nechte funkce, které nebyly upraveny z datového proudu databáze (PDB) programu, za předpokladu, že informace o řádku splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="12ff5-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="12ff5-118">Informace o správné řádku se dá určit pomocí staré informace o řádku PDB a jeden rozdílové hodnoty všech řádků ve funkci.</span><span class="sxs-lookup"><span data-stu-id="12ff5-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12ff5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12ff5-119">Requirements</span></span>  
 <span data-ttu-id="12ff5-120">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12ff5-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ff5-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12ff5-121">See also</span></span>

- [<span data-ttu-id="12ff5-122">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="12ff5-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
