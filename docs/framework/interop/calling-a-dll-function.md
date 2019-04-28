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
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643566"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="b4de1-102">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="b4de1-102">Calling a DLL Function</span></span>
<span data-ttu-id="b4de1-103">I když volání nespravovaných funkcí DLL je téměř shodná volání jiného spravovaného kódu, existují rozdíly, kterým funkcí knihovny DLL připadat složité zpočátku.</span><span class="sxs-lookup"><span data-stu-id="b4de1-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="b4de1-104">Tato část představuje témata, která popisují některé z neobvyklé problémy související s voláním.</span><span class="sxs-lookup"><span data-stu-id="b4de1-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="b4de1-105">Struktury, které jsou vráceny z platformy vyvolat volání musí být datové typy, které zabírají stejné množství spravovaného a nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="b4de1-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="b4de1-106">Tyto typy jsou označovány jako *přenositelné typy* protože nevyžadují převod (viz [přenositelné a Non-přenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="b4de1-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="b4de1-107">Volat funkci, která má nepřenositelné struktury jako její typ vrácené hodnoty, můžete definovat typu blittable pomocné rutiny stejné velikosti jako typ nepřenositelné a převést data po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="b4de1-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4de1-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b4de1-108">In This Section</span></span>  
 [<span data-ttu-id="b4de1-109">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="b4de1-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="b4de1-110">Identifikuje problémy s předáním datových struktur s předdefinovanou rozložení.</span><span class="sxs-lookup"><span data-stu-id="b4de1-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="b4de1-111">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="b4de1-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="b4de1-112">Poskytuje základní informace o funkcích zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b4de1-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="b4de1-113">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="b4de1-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="b4de1-114">Popisuje způsob implementace funkcí zpětného volání ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="b4de1-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b4de1-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b4de1-115">Related Sections</span></span>  
 [<span data-ttu-id="b4de1-116">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="b4de1-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="b4de1-117">Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="b4de1-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="b4de1-118">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="b4de1-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="b4de1-119">Popisuje, jak deklarovat parametry metody a předání argumentů funkcí exportovaných knihovnou nespravovaných knihoven.</span><span class="sxs-lookup"><span data-stu-id="b4de1-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
