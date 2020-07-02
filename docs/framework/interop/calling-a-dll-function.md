---
title: Volání funkce DLL
description: Přečtěte si problémy o volání funkce knihovny DLL, která může být matoucí. Proces volání funkce se liší v závislosti na tom, zda je návratový typ přenositelný.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620895"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="550d2-104">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="550d2-104">Calling a DLL Function</span></span>
<span data-ttu-id="550d2-105">I když volání nespravovaných knihoven DLL je téměř totožné s voláním jiného spravovaného kódu, existují rozdíly v tom, že funkce knihovny DLL se jeví jako nematoucí jako první.</span><span class="sxs-lookup"><span data-stu-id="550d2-105">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="550d2-106">V této části najdete témata, která popisují některé neobvyklé problémy související s voláním.</span><span class="sxs-lookup"><span data-stu-id="550d2-106">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="550d2-107">Struktury, které jsou vraceny voláními vyvolání platformy, musí být datové typy, které mají stejnou reprezentaci ve spravovaném a nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="550d2-107">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="550d2-108">Tyto typy se nazývají přenositelné *typy* , protože nevyžadují konverzi (viz [přenositelné a nepřímo přenositelné typy](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="550d2-108">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="550d2-109">Chcete-li volat funkci, která má jako návratový typ nepřímou strukturu, můžete definovat typ přenositelného pomocníka stejné velikosti jako nepřenosný typ a převést data poté, co funkce vrátí.</span><span class="sxs-lookup"><span data-stu-id="550d2-109">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="550d2-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="550d2-110">In This Section</span></span>  
 [<span data-ttu-id="550d2-111">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="550d2-111">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="550d2-112">Určuje problémy předávání datových struktur s předdefinovaným rozložením.</span><span class="sxs-lookup"><span data-stu-id="550d2-112">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="550d2-113">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="550d2-113">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="550d2-114">Poskytuje základní informace o funkcích zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="550d2-114">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="550d2-115">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="550d2-115">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="550d2-116">Popisuje, jak implementovat funkce zpětného volání ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="550d2-116">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="550d2-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="550d2-117">Related Sections</span></span>  
 [<span data-ttu-id="550d2-118">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="550d2-118">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="550d2-119">Popisuje, jak volat nespravované funkce knihovny DLL pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="550d2-119">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="550d2-120">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="550d2-120">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="550d2-121">Popisuje, jak deklarovat parametry metody a předávat argumenty funkcím exportovaným nespravovanými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="550d2-121">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
