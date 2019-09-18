---
title: Přenositelné a nepřenositelné typy
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739f0efdb50f8eba4875a42d5173f741b6ee94b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051888"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="48147-102">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="48147-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="48147-103">Většina datových typů má společné vyjádření ve spravované i nespravované paměti a nevyžaduje speciální zpracování v zařazovací službě Interop.</span><span class="sxs-lookup"><span data-stu-id="48147-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="48147-104">Tyto typy se nazývají přenositelné *typy* , protože nevyžadují převod, pokud jsou předávány mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="48147-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="48147-105">Struktury, které jsou vraceny voláními vyvolání platformy musí být typu přenositelné.</span><span class="sxs-lookup"><span data-stu-id="48147-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="48147-106">Vyvolání platformy nepodporuje struktury, které nejsou přenositelné jako návratové typy.</span><span class="sxs-lookup"><span data-stu-id="48147-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="48147-107">Následující typy z <xref:System> oboru názvů jsou přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="48147-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="48147-108">Následující komplexní typy jsou také přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="48147-108">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="48147-109">Jednorozměrná pole typů s více typy, jako je například pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="48147-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="48147-110">Typ, který obsahuje proměnné pole typu, však není přímo přenositelný.</span><span class="sxs-lookup"><span data-stu-id="48147-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="48147-111">Formátované typy hodnot, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátované typy).</span><span class="sxs-lookup"><span data-stu-id="48147-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="48147-112">Další informace o formátovaných hodnotových typech naleznete v tématu [Výchozí zařazování pro typy hodnot](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="48147-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="48147-113">Odkazy na objekty nejsou nanositelné.</span><span class="sxs-lookup"><span data-stu-id="48147-113">Object references are not blittable.</span></span> <span data-ttu-id="48147-114">To zahrnuje pole odkazů na objekty, které jsou přímo přenositelně.</span><span class="sxs-lookup"><span data-stu-id="48147-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="48147-115">Můžete například definovat strukturu, která je přenositelná, ale nelze definovat typ přenositeli, který obsahuje pole odkazů na tyto struktury.</span><span class="sxs-lookup"><span data-stu-id="48147-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="48147-116">V rámci optimalizace se při zařazování [připnuté](copying-and-pinning.md) pole typů a tříd, které obsahují pouze Nepřenositelný člen, se místo kopírování.</span><span class="sxs-lookup"><span data-stu-id="48147-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="48147-117">Tyto typy mohou být zařazeny jako vstupně-výstupní parametry, pokud jsou volající a volaný ve stejném typu apartment.</span><span class="sxs-lookup"><span data-stu-id="48147-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="48147-118">Tyto typy jsou však ve skutečnosti zařazeny jako v parametrech a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> atributy a <xref:System.Runtime.InteropServices.OutAttribute> , pokud chcete zařadit argument jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="48147-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="48147-119">Některé spravované datové typy vyžadují jiné reprezentace v nespravovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="48147-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="48147-120">Tyto nepřenosné datové typy musí být převedeny do formuláře, který lze zařadit.</span><span class="sxs-lookup"><span data-stu-id="48147-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="48147-121">Například spravované řetězce jsou nepřenositelné typy, protože musí být převedeny na řetězcové objekty předtím, než mohou být zařazeny do objektů typu String.</span><span class="sxs-lookup"><span data-stu-id="48147-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="48147-122">V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="48147-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="48147-123">[Delegáti](default-marshaling-behavior.md#default-marshaling-for-delegates), což jsou datové struktury, které odkazují na statickou metodu nebo na instanci třídy, jsou také nepřímo přenositelná.</span><span class="sxs-lookup"><span data-stu-id="48147-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="48147-124">Netypový typ</span><span class="sxs-lookup"><span data-stu-id="48147-124">Non-blittable type</span></span>|<span data-ttu-id="48147-125">Popis</span><span class="sxs-lookup"><span data-stu-id="48147-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="48147-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="48147-126">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="48147-127">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="48147-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="48147-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48147-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="48147-129">Převede na hodnotu 1, 2 nebo 4 bajty s `true` hodnotou 1 nebo-1.</span><span class="sxs-lookup"><span data-stu-id="48147-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="48147-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48147-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="48147-131">Převede na znak Unicode nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="48147-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="48147-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48147-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="48147-133">Převede na rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="48147-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="48147-134">System. Object</span><span class="sxs-lookup"><span data-stu-id="48147-134">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="48147-135">Převede na typ variant nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48147-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="48147-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="48147-136">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="48147-137">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="48147-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="48147-138">System. String</span><span class="sxs-lookup"><span data-stu-id="48147-138">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="48147-139">Převede na řetězec ukončující v odkazu s hodnotou null nebo na BSTR.</span><span class="sxs-lookup"><span data-stu-id="48147-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="48147-140">[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48147-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="48147-141">Převede se na strukturu s pevným rozložením paměti.</span><span class="sxs-lookup"><span data-stu-id="48147-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="48147-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="48147-142">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="48147-143">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="48147-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="48147-144">Typy tříd a objektů jsou podporovány pouze zprostředkovatelem komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="48147-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="48147-145">Pro odpovídající typy v Visual Basic, C#a C++, viz [Přehled knihovny tříd](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="48147-145">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48147-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48147-146">See also</span></span>

- [<span data-ttu-id="48147-147">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="48147-147">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
