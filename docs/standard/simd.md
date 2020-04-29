---
title: SIMD-akcelerované typy v .NET
description: Tento článek popisuje SIMD-Enable Types in .NET a ukazuje, jak používat hardwarové operace SIMD v jazycích C# a .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507780"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="4ae2d-103">Použít číselné typy SIMD-akcelerované</span><span class="sxs-lookup"><span data-stu-id="4ae2d-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="4ae2d-104">SIMD (jediná instrukce, více dat) poskytuje hardwarovou podporu pro provádění operací s více částmi dat paralelně pomocí jediné instrukce.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="4ae2d-105">V rozhraní .NET existuje sada typů SIMD, které jsou <xref:System.Numerics> pod oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="4ae2d-106">Operace SIMD se dají paralelně nacházet na úrovni hardwaru.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="4ae2d-107">To zvyšuje propustnost vektorových výpočtů, které jsou běžné v matematických, vědeckých a grafických aplikacích.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="4ae2d-108">.NET SIMD – akcelerované typy</span><span class="sxs-lookup"><span data-stu-id="4ae2d-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="4ae2d-109">Typy rozhraní .NET SIMD-akcelerované obsahují tyto typy:</span><span class="sxs-lookup"><span data-stu-id="4ae2d-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="4ae2d-110">Typy, a <xref:System.Numerics.Vector4> , které reprezentují vektory s hodnotami 2, 3 a 4 <xref:System.Single> <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3></span><span class="sxs-lookup"><span data-stu-id="4ae2d-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="4ae2d-111">Dva typy matrice <xref:System.Numerics.Matrix3x2>,, které představují matici 3x2 a <xref:System.Numerics.Matrix4x4>které představují matici 4x4 <xref:System.Single> hodnot.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="4ae2d-112"><xref:System.Numerics.Plane> Typ, který představuje rovinu v trojrozměrném prostoru pomocí <xref:System.Single> hodnot.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="4ae2d-113"><xref:System.Numerics.Quaternion> Typ, který představuje vektor, který slouží ke kódování trojrozměrných fyzických otočení pomocí <xref:System.Single> hodnot.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="4ae2d-114"><xref:System.Numerics.Vector%601> Typ, který představuje vektor zadaného číselného typu a poskytuje širokou škálu operátorů, které využívají podporu SIMD.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="4ae2d-115">Počet <xref:System.Numerics.Vector%601> instancí je vyřešen po dobu života aplikace, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="4ae2d-116"><xref:System.Numerics.Vector%601> Typ není zahrnutý v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="4ae2d-117">Aby bylo možné získat přístup k tomuto typu, je nutné nainstalovat balíček NuGet [System. Numerics. Vectors.](https://www.nuget.org/packages/System.Numerics.Vectors)</span><span class="sxs-lookup"><span data-stu-id="4ae2d-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="4ae2d-118">Typy SIMD-akcelerovany jsou implementovány takovým způsobem, že je lze použít s neSIMDm hardwarem nebo kompilátory JIT.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="4ae2d-119">Aby bylo možné využít SIMD instrukcí, musí být vaše 64 aplikace spuštěny modulem runtime, který používá kompilátor **RyuJIT** .</span><span class="sxs-lookup"><span data-stu-id="4ae2d-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="4ae2d-120">Kompilátor **RyuJIT** je součástí .NET Core a v .NET Framework 4,6 a novějším.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="4ae2d-121">Podpora SIMD se poskytuje jenom v případě, že cílíte na 64 procesorů.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="4ae2d-122">Jak používat SIMD?</span><span class="sxs-lookup"><span data-stu-id="4ae2d-122">How to use SIMD?</span></span>

<span data-ttu-id="4ae2d-123">Před prováděním vlastních SIMD algoritmů je možné zjistit, zda hostitelský počítač podporuje SIMD pomocí příkazu <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, který vrací. <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="4ae2d-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="4ae2d-124">To nezaručuje, že SIMD-Acceleration je povoleno pro konkrétní typ, ale je indikátorem, který je podporován některými typy.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="4ae2d-125">Jednoduché vektory</span><span class="sxs-lookup"><span data-stu-id="4ae2d-125">Simple Vectors</span></span>

<span data-ttu-id="4ae2d-126">Nejvíce primitivní SIMD typy v rozhraní .NET <xref:System.Numerics.Vector2>jsou, <xref:System.Numerics.Vector3>a <xref:System.Numerics.Vector4> typy, které představují vektory se 2, 3 a 4 <xref:System.Single> hodnotami.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="4ae2d-127">Následující příklad používá <xref:System.Numerics.Vector2> k přidání dvou vektorů.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

<span data-ttu-id="4ae2d-128">Je také možné použít vektory .NET k výpočtu jiných matematických vlastností vektorů `Dot product`, jako jsou, `Transform` `Clamp` a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="4ae2d-129">Matrix</span><span class="sxs-lookup"><span data-stu-id="4ae2d-129">Matrix</span></span>

<span data-ttu-id="4ae2d-130"><xref:System.Numerics.Matrix3x2>, který představuje matici 3x2 a <xref:System.Numerics.Matrix4x4>který představuje matici 4x4.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="4ae2d-131">Dá se použít pro výpočty související s maticí.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="4ae2d-132">Následující příklad znázorňuje násobení matice pro korespondentskou matici transponovat pomocí SIMD.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="4ae2d-133">Vektor\<T></span><span class="sxs-lookup"><span data-stu-id="4ae2d-133">Vector\<T></span></span>

<span data-ttu-id="4ae2d-134"><xref:System.Numerics.Vector%601> Nabízí možnost používat delší vektory.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="4ae2d-135">Počet <xref:System.Numerics.Vector%601> instancí je pevný, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěný kód.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="4ae2d-136">Následující příklad ukazuje, jak přidat dlouhé pole elementů pomocí <xref:System.Numerics.Vector%601>.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a><span data-ttu-id="4ae2d-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ae2d-137">Remarks</span></span>

<span data-ttu-id="4ae2d-138">SIMD je pravděpodobnější odebrat jeden kritický bod a vystavit další, například propustnost paměti.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="4ae2d-139">Obecně platí, že výhoda použití SIMD se liší v závislosti na konkrétním scénáři a v některých případech může dokonce provádět méně než jednodušší kód neSIMD ekvivalentu.</span><span class="sxs-lookup"><span data-stu-id="4ae2d-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
