---
title: "Globální statické funkce ladění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad5d3ef689a251ea4b154afc5d1bfb387388ddb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="bdff6-102">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="bdff6-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="bdff6-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="bdff6-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdff6-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bdff6-104">In This Section</span></span>  
 [<span data-ttu-id="bdff6-105">_Efn_getmanagedexcepstack – funkce</span><span class="sxs-lookup"><span data-stu-id="bdff6-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="bdff6-106">Zadaný objekt adresu spravovaného výjimka vrátí řetězec verzi nachází v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bdff6-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="bdff6-107">_Efn_getmanagedobjectfieldinfo – funkce</span><span class="sxs-lookup"><span data-stu-id="bdff6-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="bdff6-108">Získá posun od začátku objekt pole a hodnotu pole pomocí ukazatele zadaného objektu a název pole.</span><span class="sxs-lookup"><span data-stu-id="bdff6-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="bdff6-109">_Efn_getmanagedobjectname – funkce</span><span class="sxs-lookup"><span data-stu-id="bdff6-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="bdff6-110">Získá název typu pomocí ukazatele zadaný spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="bdff6-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="bdff6-111">_Efn_stacktrace – funkce</span><span class="sxs-lookup"><span data-stu-id="bdff6-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="bdff6-112">Poskytuje textové reprezentace trasování spravované zásobníku a pole `CONTEXT` zaznamenává, jednu pro každý přechod mezi nespravované a spravované kódu.</span><span class="sxs-lookup"><span data-stu-id="bdff6-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="bdff6-113">Clrdatacreateinstance – funkce</span><span class="sxs-lookup"><span data-stu-id="bdff6-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="bdff6-114">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="bdff6-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="bdff6-115">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="bdff6-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="bdff6-116">Odkazuje na funkci, která je volána daty CLR přístup ke službám k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="bdff6-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bdff6-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bdff6-117">Related Sections</span></span>  
 [<span data-ttu-id="bdff6-118">Ladění tříd typu coclass</span><span class="sxs-lookup"><span data-stu-id="bdff6-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="bdff6-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdff6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="bdff6-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="bdff6-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="bdff6-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="bdff6-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
