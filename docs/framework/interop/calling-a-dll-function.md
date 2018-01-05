---
title: "Volání funkce DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8755173b9c64a6457b94e689204c6a5aabc971cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="97037-102">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="97037-102">Calling a DLL Function</span></span>
<span data-ttu-id="97037-103">Přestože volání nespravovaných funkcí knihovny DLL je téměř shodná volání jiných spravovaného kódu, jsou rozdíly, které můžou vypadat matoucí funkcí knihovny DLL na první.</span><span class="sxs-lookup"><span data-stu-id="97037-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="97037-104">Tato část obsahuje témata, která popisují některá z neobvyklého problémy související s volání.</span><span class="sxs-lookup"><span data-stu-id="97037-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="97037-105">Struktury, které jsou vráceny z platformy vyvolat volání musí být typy dat, které mají stejnou reprezentaci v spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="97037-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="97037-106">Tyto typy jsou označovány jako *přenositelné typy* protože nevyžadují převodu (viz [přenositelné a Non-přenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="97037-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="97037-107">K volání funkce, která má strukturu nepřenositelné jako její návratový typ, můžete definovat typu blittable pomocná stejnou velikost jako typ nepřenositelné a převést data po funkce vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="97037-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97037-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="97037-108">In This Section</span></span>  
 [<span data-ttu-id="97037-109">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="97037-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="97037-110">Identifikuje problémy předat datové struktury předdefinované rozložení.</span><span class="sxs-lookup"><span data-stu-id="97037-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="97037-111">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="97037-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="97037-112">Poskytuje základní informace o funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="97037-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="97037-113">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="97037-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="97037-114">Popisuje způsob implementace funkcí zpětného volání ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="97037-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="97037-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="97037-115">Related Sections</span></span>  
 [<span data-ttu-id="97037-116">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="97037-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="97037-117">Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="97037-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="97037-118">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="97037-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="97037-119">Popisuje, jak deklarace parametry metody a předání argumentů funkce exportované sadou nespravované knihovny.</span><span class="sxs-lookup"><span data-stu-id="97037-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
