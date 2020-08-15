---
title: SIMD-akcelerované typy v .NET
description: Tento článek popisuje SIMD-Enable Types in .NET a ukazuje, jak používat hardwarové operace SIMD v jazycích C# a .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 5c1ad01ea15a9c4352cf7f87e5fba3bf74b4679c
ms.sourcegitcommit: 2987e241e2f76c9248d2146bf2761a33e2c7a882
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88228733"
---
# <a name="use-simd-accelerated-numeric-types"></a>Použít číselné typy SIMD-akcelerované

SIMD (jediná instrukce, více dat) poskytuje hardwarovou podporu pro provádění operací s více částmi dat paralelně pomocí jediné instrukce. V rozhraní .NET existuje sada typů SIMD, které jsou pod <xref:System.Numerics> oborem názvů. Operace SIMD se dají paralelně nacházet na úrovni hardwaru. To zvyšuje propustnost vektorových výpočtů, které jsou běžné v matematických, vědeckých a grafických aplikacích.

## <a name="net-simd-accelerated-types"></a>.NET SIMD – akcelerované typy

Typy rozhraní .NET SIMD-akcelerované obsahují tyto typy:

- <xref:System.Numerics.Vector2>Typy, <xref:System.Numerics.Vector3> a <xref:System.Numerics.Vector4> , které reprezentují vektory s hodnotami 2, 3 a 4 <xref:System.Single> .

- Dva typy matrice, <xref:System.Numerics.Matrix3x2> , které představují matici 3x2 a <xref:System.Numerics.Matrix4x4> které představují matici 4x4 <xref:System.Single> hodnot.

- <xref:System.Numerics.Plane>Typ, který představuje rovinu v trojrozměrném prostoru pomocí <xref:System.Single> hodnot.

- <xref:System.Numerics.Quaternion>Typ, který představuje vektor, který slouží ke kódování trojrozměrných fyzických otočení pomocí <xref:System.Single> hodnot.

- <xref:System.Numerics.Vector%601>Typ, který představuje vektor zadaného číselného typu a poskytuje širokou škálu operátorů, které využívají podporu SIMD. Počet <xref:System.Numerics.Vector%601> instancí je vyřešen po dobu života aplikace, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěn kód.

  > [!NOTE]
  > <xref:System.Numerics.Vector%601>Typ není zahrnutý v .NET Framework. Aby bylo možné získat přístup k tomuto typu, je nutné nainstalovat balíček NuGet [System. Numerics. Vectors.](https://www.nuget.org/packages/System.Numerics.Vectors)
  
Typy SIMD-akcelerovany jsou implementovány takovým způsobem, že je lze použít s neSIMDm hardwarem nebo kompilátory JIT. Aby bylo možné využít SIMD instrukcí, musí být vaše 64 aplikace spuštěny modulem runtime, který používá kompilátor **RyuJIT** . Kompilátor **RyuJIT** je součástí .NET Core a v .NET Framework 4,6 a novějším. Podpora SIMD se poskytuje jenom v případě, že cílíte na 64 procesorů.

## <a name="how-to-use-simd"></a>Jak používat SIMD?

Před prováděním vlastních SIMD algoritmů je možné zjistit, zda hostitelský počítač podporuje SIMD pomocí příkazu <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> , který vrací <xref:System.Boolean> . To nezaručuje, že SIMD-Acceleration je povoleno pro konkrétní typ, ale je indikátorem, který je podporován některými typy.

## <a name="simple-vectors"></a>Jednoduché vektory

Nejvíce primitivní SIMD typy v rozhraní .NET jsou <xref:System.Numerics.Vector2> , <xref:System.Numerics.Vector3> a <xref:System.Numerics.Vector4> typy, které představují vektory se 2, 3 a 4 <xref:System.Single> hodnotami. Následující příklad používá <xref:System.Numerics.Vector2> k přidání dvou vektorů.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

Je také možné použít vektory .NET k výpočtu jiných matematických vlastností vektorů, jako jsou `Dot product` , `Transform` `Clamp` a tak dále.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>Matice

<xref:System.Numerics.Matrix3x2>, který představuje matici 3x2 a <xref:System.Numerics.Matrix4x4> který představuje matici 4x4. Dá se použít pro výpočty související s maticí. Následující příklad znázorňuje násobení matice pro korespondentskou matici transponovat pomocí SIMD.

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>Vektorový\<T>

<xref:System.Numerics.Vector%601>Nabízí možnost používat delší vektory. Počet <xref:System.Numerics.Vector%601> instancí je pevný, ale její hodnota <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> závisí na procesoru počítače, na kterém je spuštěný kód.

Následující příklad ukazuje, jak přidat dlouhé pole elementů pomocí <xref:System.Numerics.Vector%601> .

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

## <a name="remarks"></a>Poznámky

SIMD je pravděpodobnější odebrat jeden kritický bod a vystavit další, například propustnost paměti. Obecně platí, že výhoda použití SIMD se liší v závislosti na konkrétním scénáři a v některých případech může dokonce provádět méně než jednodušší kód neSIMD ekvivalentu.
