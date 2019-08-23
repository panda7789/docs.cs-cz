---
title: Přenositelné a nepřenositelné typy
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2cdaa312c037714a34e25e62ad318c9bc745ea7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953181"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="ee702-102">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="ee702-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="ee702-103">Většina datových typů má společné vyjádření ve spravované i nespravované paměti a nevyžaduje speciální zpracování v zařazovací službě Interop.</span><span class="sxs-lookup"><span data-stu-id="ee702-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="ee702-104">Tyto typy se nazývají přenositelné *typy* , protože nevyžadují převod, pokud jsou předávány mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="ee702-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="ee702-105">Struktury, které jsou vraceny voláními vyvolání platformy musí být typu přenositelné.</span><span class="sxs-lookup"><span data-stu-id="ee702-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="ee702-106">Vyvolání platformy nepodporuje struktury, které nejsou přenositelné jako návratové typy.</span><span class="sxs-lookup"><span data-stu-id="ee702-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="ee702-107">Následující typy z <xref:System> oboru názvů jsou přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="ee702-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
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
  
 <span data-ttu-id="ee702-108">Následující komplexní typy jsou také přenositelné typy:</span><span class="sxs-lookup"><span data-stu-id="ee702-108">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="ee702-109">Jednorozměrná pole typů s více typy, jako je například pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ee702-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="ee702-110">Typ, který obsahuje proměnné pole typu, však není přímo přenositelný.</span><span class="sxs-lookup"><span data-stu-id="ee702-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="ee702-111">Formátované typy hodnot, které obsahují pouze přenositelné typy (a třídy, pokud jsou zařazeny jako formátované typy).</span><span class="sxs-lookup"><span data-stu-id="ee702-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="ee702-112">Další informace o formátovaných hodnotových typech naleznete v tématu [Výchozí zařazování pro typy hodnot](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="ee702-112">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="ee702-113">Odkazy na objekty nejsou nanositelné.</span><span class="sxs-lookup"><span data-stu-id="ee702-113">Object references are not blittable.</span></span> <span data-ttu-id="ee702-114">To zahrnuje pole odkazů na objekty, které jsou přímo přenositelně.</span><span class="sxs-lookup"><span data-stu-id="ee702-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="ee702-115">Můžete například definovat strukturu, která je přenositelná, ale nelze definovat typ přenositeli, který obsahuje pole odkazů na tyto struktury.</span><span class="sxs-lookup"><span data-stu-id="ee702-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="ee702-116">V rámci optimalizace se při zařazování připnuté pole typů a tříd, které obsahují [](../../../docs/framework/interop/copying-and-pinning.md) pouze Nepřenositelný člen, se místo kopírování.</span><span class="sxs-lookup"><span data-stu-id="ee702-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="ee702-117">Tyto typy mohou být zařazeny jako vstupně-výstupní parametry, pokud jsou volající a volaný ve stejném typu apartment.</span><span class="sxs-lookup"><span data-stu-id="ee702-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="ee702-118">Tyto typy jsou však ve skutečnosti zařazeny jako v parametrech a je nutné použít <xref:System.Runtime.InteropServices.InAttribute> atributy a <xref:System.Runtime.InteropServices.OutAttribute> , pokud chcete zařadit argument jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="ee702-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="ee702-119">Některé spravované datové typy vyžadují jiné reprezentace v nespravovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="ee702-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="ee702-120">Tyto nepřenosné datové typy musí být převedeny do formuláře, který lze zařadit.</span><span class="sxs-lookup"><span data-stu-id="ee702-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="ee702-121">Například spravované řetězce jsou nepřenositelné typy, protože musí být převedeny na řetězcové objekty předtím, než mohou být zařazeny do objektů typu String.</span><span class="sxs-lookup"><span data-stu-id="ee702-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="ee702-122">V následující tabulce jsou uvedeny nepřenositelné typy z <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ee702-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="ee702-123">[Delegáti](default-marshaling-behavior.md#default-marshaling-for-delegates), což jsou datové struktury, které odkazují na statickou metodu nebo na instanci třídy, jsou také nepřímo přenositelná.</span><span class="sxs-lookup"><span data-stu-id="ee702-123">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="ee702-124">Netypový typ</span><span class="sxs-lookup"><span data-stu-id="ee702-124">Non-blittable type</span></span>|<span data-ttu-id="ee702-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ee702-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="ee702-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="ee702-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="ee702-127">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ee702-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="ee702-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee702-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="ee702-129">Převede na hodnotu 1, 2 nebo 4 bajty s `true` hodnotou 1 nebo-1.</span><span class="sxs-lookup"><span data-stu-id="ee702-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="ee702-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee702-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="ee702-131">Převede na znak Unicode nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="ee702-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="ee702-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee702-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="ee702-133">Převede na rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="ee702-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="ee702-134">System. Object</span><span class="sxs-lookup"><span data-stu-id="ee702-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="ee702-135">Převede na typ variant nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee702-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="ee702-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="ee702-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="ee702-137">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ee702-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="ee702-138">System. String</span><span class="sxs-lookup"><span data-stu-id="ee702-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="ee702-139">Převede na řetězec ukončující v odkazu s hodnotou null nebo na BSTR.</span><span class="sxs-lookup"><span data-stu-id="ee702-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="ee702-140">[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ee702-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="ee702-141">Převede se na strukturu s pevným rozložením paměti.</span><span class="sxs-lookup"><span data-stu-id="ee702-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="ee702-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="ee702-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="ee702-143">Převede na pole ve stylu jazyka C nebo `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ee702-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="ee702-144">Typy tříd a objektů jsou podporovány pouze zprostředkovatelem komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="ee702-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="ee702-145">Pro odpovídající typy v Visual Basic, C#a C++, viz [Přehled knihovny tříd](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee702-145">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee702-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee702-146">See also</span></span>

- [<span data-ttu-id="ee702-147">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="ee702-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
