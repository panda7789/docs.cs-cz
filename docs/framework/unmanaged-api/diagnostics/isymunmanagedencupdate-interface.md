---
title: "ISymUnmanagedENCUpdate – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="d2251-102">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2251-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="d2251-103">Poskytuje funkce pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d2251-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2251-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d2251-104">Methods</span></span>  
  
|<span data-ttu-id="d2251-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-105">Method</span></span>|<span data-ttu-id="d2251-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d2251-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2251-107">Getlocalvariablecount – metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="d2251-108">Získá počet lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="d2251-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="d2251-109">Getlocalvariables – metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="d2251-110">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="d2251-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="d2251-111">Initializeforenc – metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="d2251-112">Umožňuje metoda hranice počítaný před prvním volání [isymunmanagedencupdate::updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="d2251-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="d2251-113">Updatemethodlines – metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="d2251-114">Umožňuje aktualizaci řádku informace pro metodu, která nebyla překompilovat, ale jejichž řádky byl přesunut nezávisle.</span><span class="sxs-lookup"><span data-stu-id="d2251-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="d2251-115">Rozdílové každý příkaz je povolen.</span><span class="sxs-lookup"><span data-stu-id="d2251-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="d2251-116">Updatesymbolstore2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d2251-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="d2251-117">Umožňuje kompilátoru vynechat funkce, které nebyly upraveny z datového proudu program databáze (PDB), za předpokladu, že informace o řádku splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="d2251-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="d2251-118">Informace o správné řádku se dá určit pomocí staré informace řádku PDB a jeden rozdílové u všech spojnic ve funkci.</span><span class="sxs-lookup"><span data-stu-id="d2251-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2251-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2251-119">Requirements</span></span>  
 <span data-ttu-id="d2251-120">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2251-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2251-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2251-121">See Also</span></span>  
 [<span data-ttu-id="d2251-122">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="d2251-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
