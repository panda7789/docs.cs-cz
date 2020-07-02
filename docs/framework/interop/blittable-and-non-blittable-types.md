---
title: Přenositelné a nepřenositelné typy
description: Přečtěte si o nepřenositelné a nepřenositelné typy. Přenositelné datové typy jsou obvykle zastoupeny ve spravované a nespravované paměti a nevyžadují speciální zpracování.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 68f4197a2710b6825c83bbc51daaf8f6b5a2c81f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621532"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="de7c5-104">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="de7c5-104">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="de7c5-105">Většina datových typů má společné vyjádření ve spravované i nespravované paměti a nevyžaduje speciální zpracování v zařazovací službě Interop.</span><span class="sxs-lookup"><span data-stu-id="de7c5-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="de7c5-106">Tyto typy se nazývají přenositelné *typy* , protože nevyžadují převod, pokud jsou předávány mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="de7c5-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="de7c5-107">Struktury, které jsou vraceny voláními vyvolání platformy musí být typu přenositelné.</span><span class="sxs-lookup"><span data-stu-id="de7c5-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="de7c5-108">Vyvolání platformy nepodporuje struktury, které nejsou přenositelné jako návratové typy.</span><span class="sxs-lookup"><span data-stu-id="de7c5-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="de7c5-109">Následující typy z <xref:System> oboru názvů jsou přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="de7c5-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
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
  
 <span data-ttu-id="de7c5-110">Následující komplexní typy jsou také přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="de7c5-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="de7c5-111">Jednorozměrná pole typů s více typy, jako je například pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="de7c5-111">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="de7c5-112">Typ, který obsahuje proměnné pole typu, však není přímo přenositelný.</span><span class="sxs-lookup"><span data-stu-id="de7c5-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="de7c5-113">Formátované typy hodnot, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátované typy).</span><span class="sxs-lookup"><span data-stu-id="de7c5-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="de7c5-114">Další informace o formátovaných hodnotových typech naleznete v tématu [Výchozí zařazování pro typy hodnot](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="de7c5-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="de7c5-115">Odkazy na objekty nejsou nanositelné.</span><span class="sxs-lookup"><span data-stu-id="de7c5-115">Object references are not blittable.</span></span> <span data-ttu-id="de7c5-116">To zahrnuje pole odkazů na objekty, které jsou přímo přenositelně.</span><span class="sxs-lookup"><span data-stu-id="de7c5-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="de7c5-117">Můžete například definovat strukturu, která je přenositelná, ale nelze definovat typ přenositeli, který obsahuje pole odkazů na tyto struktury.</span><span class="sxs-lookup"><span data-stu-id="de7c5-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="de7c5-118">V rámci optimalizace se při zařazování [připnuté](copying-and-pinning.md) pole typů a tříd, které obsahují pouze Nepřenositelný člen, se místo kopírování.</span><span class="sxs-lookup"><span data-stu-id="de7c5-118">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="de7c5-119">Tyto typy mohou být zařazeny jako vstupně-výstupní parametry, pokud jsou volající a volaný ve stejném typu apartment.</span><span class="sxs-lookup"><span data-stu-id="de7c5-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="de7c5-120">Tyto typy jsou však ve skutečnosti zařazeny jako v parametrech a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> atributy a, <xref:System.Runtime.InteropServices.OutAttribute> Pokud chcete zařadit argument jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="de7c5-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="de7c5-121">Některé spravované datové typy vyžadují jiné reprezentace v nespravovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="de7c5-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="de7c5-122">Tyto nepřenosné datové typy musí být převedeny do formuláře, který lze zařadit.</span><span class="sxs-lookup"><span data-stu-id="de7c5-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="de7c5-123">Například spravované řetězce jsou nepřenositelné typy, protože musí být převedeny na řetězcové objekty předtím, než mohou být zařazeny do objektů typu String.</span><span class="sxs-lookup"><span data-stu-id="de7c5-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="de7c5-124">V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="de7c5-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="de7c5-125">[Delegáti](default-marshaling-behavior.md#default-marshaling-for-delegates), což jsou datové struktury, které odkazují na statickou metodu nebo na instanci třídy, jsou také nepřímo přenositelná.</span><span class="sxs-lookup"><span data-stu-id="de7c5-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="de7c5-126">Netypový typ</span><span class="sxs-lookup"><span data-stu-id="de7c5-126">Non-blittable type</span></span>|<span data-ttu-id="de7c5-127">Popis</span><span class="sxs-lookup"><span data-stu-id="de7c5-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="de7c5-128">System. Array</span><span class="sxs-lookup"><span data-stu-id="de7c5-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="de7c5-129">Převede na pole ve stylu jazyka C nebo `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="de7c5-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="de7c5-130">[System. Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de7c5-130">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="de7c5-131">Převede na hodnotu 1, 2 nebo 4 bajty s hodnotou `true` 1 nebo-1.</span><span class="sxs-lookup"><span data-stu-id="de7c5-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="de7c5-132">[System. Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de7c5-132">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="de7c5-133">Převede na znak Unicode nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="de7c5-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="de7c5-134">[System. Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de7c5-134">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="de7c5-135">Převede na rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="de7c5-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="de7c5-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="de7c5-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="de7c5-137">Převede na typ variant nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="de7c5-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="de7c5-138">System. Mdarray</span><span class="sxs-lookup"><span data-stu-id="de7c5-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="de7c5-139">Převede na pole ve stylu jazyka C nebo `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="de7c5-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="de7c5-140">System. String</span><span class="sxs-lookup"><span data-stu-id="de7c5-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="de7c5-141">Převede na řetězec ukončující v odkazu s hodnotou null nebo na BSTR.</span><span class="sxs-lookup"><span data-stu-id="de7c5-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="de7c5-142">[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de7c5-142">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="de7c5-143">Převede se na strukturu s pevným rozložením paměti.</span><span class="sxs-lookup"><span data-stu-id="de7c5-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="de7c5-144">System. Szarray</span><span class="sxs-lookup"><span data-stu-id="de7c5-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="de7c5-145">Převede na pole ve stylu jazyka C nebo `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="de7c5-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="de7c5-146">Typy tříd a objektů jsou podporovány pouze zprostředkovatelem komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="de7c5-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="de7c5-147">Odpovídající typy v Visual Basic, C# a C++ naleznete v tématu [Přehled knihovny tříd](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de7c5-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7c5-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de7c5-148">See also</span></span>

- [<span data-ttu-id="de7c5-149">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="de7c5-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
