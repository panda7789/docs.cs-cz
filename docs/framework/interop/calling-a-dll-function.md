---
title: Volání funkce DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051875"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="30974-102">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="30974-102">Calling a DLL Function</span></span>
<span data-ttu-id="30974-103">I když volání nespravovaných knihoven DLL je téměř totožné s voláním jiného spravovaného kódu, existují rozdíly v tom, že funkce knihovny DLL se jeví jako nematoucí jako první.</span><span class="sxs-lookup"><span data-stu-id="30974-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="30974-104">V této části najdete témata, která popisují některé neobvyklé problémy související s voláním.</span><span class="sxs-lookup"><span data-stu-id="30974-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="30974-105">Struktury, které jsou vraceny voláními vyvolání platformy, musí být datové typy, které mají stejnou reprezentaci ve spravovaném a nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30974-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="30974-106">Tyto typy se nazývají přenositelné *typy* , protože nevyžadují konverzi (viz [přenositelné a nepřímo přenositelné typy](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="30974-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="30974-107">Chcete-li volat funkci, která má jako návratový typ nepřímou strukturu, můžete definovat typ přenositelného pomocníka stejné velikosti jako nepřenosný typ a převést data poté, co funkce vrátí.</span><span class="sxs-lookup"><span data-stu-id="30974-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30974-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="30974-108">In This Section</span></span>  
 [<span data-ttu-id="30974-109">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="30974-109">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="30974-110">Určuje problémy předávání datových struktur s předdefinovaným rozložením.</span><span class="sxs-lookup"><span data-stu-id="30974-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="30974-111">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="30974-111">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="30974-112">Poskytuje základní informace o funkcích zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="30974-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="30974-113">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="30974-113">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="30974-114">Popisuje, jak implementovat funkce zpětného volání ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30974-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30974-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="30974-115">Related Sections</span></span>  
 [<span data-ttu-id="30974-116">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="30974-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="30974-117">Popisuje, jak volat nespravované funkce knihovny DLL pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="30974-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="30974-118">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="30974-118">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="30974-119">Popisuje, jak deklarovat parametry metody a předávat argumenty funkcím exportovaným nespravovanými knihovnami.</span><span class="sxs-lookup"><span data-stu-id="30974-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
