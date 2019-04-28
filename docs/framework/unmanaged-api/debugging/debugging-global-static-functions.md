---
title: Globální statické funkce ladění
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698522"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="505dc-102">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="505dc-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="505dc-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="505dc-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="505dc-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="505dc-104">In This Section</span></span>  
 [<span data-ttu-id="505dc-105">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="505dc-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="505dc-106">Zadaný objekt na spravované výjimky adresu vrátí řetězec verzi obsažena v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="505dc-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="505dc-107">_EFN_GetManagedObjectFieldInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="505dc-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="505dc-108">Získá posun od začátku objekt pole a hodnota pole pomocí ukazatele zadaného objektu a název pole.</span><span class="sxs-lookup"><span data-stu-id="505dc-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="505dc-109">_EFN_GetManagedObjectName – funkce</span><span class="sxs-lookup"><span data-stu-id="505dc-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="505dc-110">Získá název typu pomocí ukazatele zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="505dc-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="505dc-111">_EFN_StackTrace – funkce</span><span class="sxs-lookup"><span data-stu-id="505dc-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="505dc-112">Poskytuje textové vyjádření spravovaného zásobníku a pole `CONTEXT` záznamy, jeden pro každý přechod mezi nespravované a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="505dc-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="505dc-113">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="505dc-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="505dc-114">Je voláno common language runtime (CLR) data access services k vytvoření objektu zadané rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="505dc-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="505dc-115">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="505dc-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="505dc-116">Odkazuje na funkci, která je volána z dat CLR přístup ke službám vytvořit objekt zadané rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="505dc-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="505dc-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="505dc-117">Related Sections</span></span>  
 [<span data-ttu-id="505dc-118">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="505dc-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="505dc-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="505dc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="505dc-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="505dc-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="505dc-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="505dc-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
