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
ms.workload: dotnet
ms.openlocfilehash: a7fde0941959619f4832019806401be0ffddb81e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="770bc-102">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="770bc-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="770bc-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="770bc-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="770bc-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="770bc-104">In This Section</span></span>  
 [<span data-ttu-id="770bc-105">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="770bc-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="770bc-106">Zadaný objekt adresu spravovaného výjimka vrátí řetězec verzi nachází v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="770bc-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="770bc-107">_EFN_GetManagedObjectFieldInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="770bc-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="770bc-108">Získá posun od začátku objekt pole a hodnotu pole pomocí ukazatele zadaného objektu a název pole.</span><span class="sxs-lookup"><span data-stu-id="770bc-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="770bc-109">_EFN_GetManagedObjectName – funkce</span><span class="sxs-lookup"><span data-stu-id="770bc-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="770bc-110">Získá název typu pomocí ukazatele zadaný spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="770bc-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="770bc-111">_EFN_StackTrace – funkce</span><span class="sxs-lookup"><span data-stu-id="770bc-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="770bc-112">Poskytuje textové reprezentace trasování spravované zásobníku a pole `CONTEXT` zaznamenává, jednu pro každý přechod mezi nespravované a spravované kódu.</span><span class="sxs-lookup"><span data-stu-id="770bc-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="770bc-113">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="770bc-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="770bc-114">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="770bc-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="770bc-115">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="770bc-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="770bc-116">Odkazuje na funkci, která je volána daty CLR přístup ke službám k vytvoření objektu zadaného rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="770bc-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="770bc-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="770bc-117">Related Sections</span></span>  
 [<span data-ttu-id="770bc-118">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="770bc-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="770bc-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="770bc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="770bc-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="770bc-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="770bc-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="770bc-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
