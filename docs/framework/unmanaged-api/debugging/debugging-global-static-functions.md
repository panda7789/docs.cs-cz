---
title: Globální statické funkce ladění
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793784"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="f7bca-102">Globální statické funkce ladění</span><span class="sxs-lookup"><span data-stu-id="f7bca-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="f7bca-103">Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f7bca-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7bca-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f7bca-104">In This Section</span></span>  
 [<span data-ttu-id="f7bca-105">_EFN_GetManagedExcepStack – funkce</span><span class="sxs-lookup"><span data-stu-id="f7bca-105">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="f7bca-106">Pokud je zadána adresa spravovaného objektu výjimky, vrátí verzi řetězce trasování zásobníku obsaženého v rámci.</span><span class="sxs-lookup"><span data-stu-id="f7bca-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="f7bca-107">_EFN_GetManagedObjectFieldInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f7bca-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="f7bca-108">Získá posun od začátku objektu k poli a hodnotu pole pomocí zadaného ukazatele objektu a názvu pole.</span><span class="sxs-lookup"><span data-stu-id="f7bca-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="f7bca-109">_EFN_GetManagedObjectName – funkce</span><span class="sxs-lookup"><span data-stu-id="f7bca-109">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="f7bca-110">Získá název typu pomocí zadaného ukazatele spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="f7bca-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="f7bca-111">_EFN_StackTrace – funkce</span><span class="sxs-lookup"><span data-stu-id="f7bca-111">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="f7bca-112">Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="f7bca-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="f7bca-113">CLRDataCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="f7bca-113">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="f7bca-114">Volá se službami CLR (Common Language Runtime) k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="f7bca-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="f7bca-115">PFN_CLRDataCreateInstance – ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="f7bca-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="f7bca-116">Odkazuje na funkci, která je volána službami CLR Data Access, k vytvoření zadaného objektu rozhraní pro zadaný cílový proces.</span><span class="sxs-lookup"><span data-stu-id="f7bca-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7bca-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f7bca-117">Related Sections</span></span>  
 [<span data-ttu-id="f7bca-118">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7bca-118">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="f7bca-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7bca-119">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="f7bca-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7bca-120">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="f7bca-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7bca-121">Debugging Structures</span></span>](debugging-structures.md)
