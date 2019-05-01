---
title: Zadejte zařazování – .NET
description: Zjistěte, jak .NET zařazuje vaše typy pro nativní reprezentace.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b4846f2e6cd945a25ec6a747c9038d48fe115559
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973496"
---
# <a name="type-marshalling"></a><span data-ttu-id="162ab-103">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="162ab-103">Type marshalling</span></span>

<span data-ttu-id="162ab-104">**Zařazování** je proces transformace typy, když je budou potřebovat pro různé mezi spravovaný a nativní kód.</span><span class="sxs-lookup"><span data-stu-id="162ab-104">**Marshalling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="162ab-105">Zařazování je potřeba, protože se liší typy v spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="162ab-105">Marshalling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="162ab-106">Ve spravovaném kódu, například můžete mít `String`, zatímco nespravované světě mohou být řetězce Unicode ("širokých"), kódování Unicode, zakončený hodnotou null, ASCII, atd. Ve výchozím nastavení P/Invoke subsystému pokouší provést správné věci na základě výchozí chování, je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="162ab-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="162ab-107">Pro tyto situace, kdy potřebujete další ovládací prvek, ale můžete použít [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atribut k určení, co je očekávaný typ v nespravované oblasti.</span><span class="sxs-lookup"><span data-stu-id="162ab-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="162ab-108">Například pokud chcete řetězec, který má být odeslán jako ANSI řetězec zakončený hodnotou null, lze nastavit takto:</span><span class="sxs-lookup"><span data-stu-id="162ab-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshalling-common-types"></a><span data-ttu-id="162ab-109">Výchozí pravidla pro zařazování běžných typů</span><span class="sxs-lookup"><span data-stu-id="162ab-109">Default rules for marshalling common types</span></span>

<span data-ttu-id="162ab-110">Obecně platí, modul runtime pokusí provést "správné věci" při vyžadování minimální množství práce, které od vás sběrného systému.</span><span class="sxs-lookup"><span data-stu-id="162ab-110">Generally, the runtime tries to do the "right thing" when marshalling to require the least amount of work from you.</span></span> <span data-ttu-id="162ab-111">Následující tabulky popisují, jak je každý typ zařazeno ve výchozím nastavení při použití v parametru nebo pole.</span><span class="sxs-lookup"><span data-stu-id="162ab-111">The following tables describe how each type is marshalled by default when used in a parameter or field.</span></span> <span data-ttu-id="162ab-112">C99 / C ++ 11 celočíselné neproporcionální a typy znaků se používají k ověření, že v následující tabulce je správná pro všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="162ab-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="162ab-113">Můžete použít nativní typ, který má stejné zarovnání a požadavky na velikost jako tyto typy.</span><span class="sxs-lookup"><span data-stu-id="162ab-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="162ab-114">V první tabulce popisuje mapování pro různé typy, pro které zařazování je stejný pro P/Invoke a zařazování pro pole.</span><span class="sxs-lookup"><span data-stu-id="162ab-114">This first table describes the mappings for various types for whom the marshalling is the same for both P/Invoke and field marshalling.</span></span>

| <span data-ttu-id="162ab-115">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-115">.NET Type</span></span> | <span data-ttu-id="162ab-116">Nativní typ</span><span class="sxs-lookup"><span data-stu-id="162ab-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="162ab-117">Buď `char` nebo `char16_t` v závislosti na tom `CharSet` P/Invoke nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="162ab-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="162ab-118">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="162ab-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="162ab-119">Buď `char*` nebo `char16_t*` v závislosti na tom `CharSet` P/Invoke nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="162ab-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="162ab-120">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="162ab-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="162ab-121">Typy ukazatelů rozhraní .NET (např.)</span><span class="sxs-lookup"><span data-stu-id="162ab-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="162ab-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="162ab-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="162ab-123">Typ odvozený od `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="162ab-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="162ab-124">Typ odvozený od `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="162ab-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="162ab-125">Win32 `BOOL` typu</span><span class="sxs-lookup"><span data-stu-id="162ab-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="162ab-126">COM `DECIMAL` – struktura</span><span class="sxs-lookup"><span data-stu-id="162ab-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="162ab-127">Delegát .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-127">.NET Delegate</span></span> | <span data-ttu-id="162ab-128">Ukazatel na nativní funkci</span><span class="sxs-lookup"><span data-stu-id="162ab-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="162ab-129">Win32 `DATE` typu</span><span class="sxs-lookup"><span data-stu-id="162ab-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="162ab-130">Win32 `GUID` typu</span><span class="sxs-lookup"><span data-stu-id="162ab-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="162ab-131">Několik kategorií zařazování používají různé výchozí hodnoty, pokud jste zařazování jako parametr nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="162ab-131">A few categories of marshalling have different defaults if you're marshalling as a parameter or structure.</span></span>

| <span data-ttu-id="162ab-132">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-132">.NET Type</span></span> | <span data-ttu-id="162ab-133">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="162ab-133">Native Type (Parameter)</span></span> | <span data-ttu-id="162ab-134">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="162ab-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="162ab-135">Pole .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-135">.NET array</span></span> | <span data-ttu-id="162ab-136">Ukazatel na začátku pole nativní reprezentace prvků pole.</span><span class="sxs-lookup"><span data-stu-id="162ab-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="162ab-137">Není povoleno bez `[MarshalAs]` atribut</span><span class="sxs-lookup"><span data-stu-id="162ab-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="162ab-138">Třída s atributem `LayoutKind` z `Sequential` nebo `Explicit`</span><span class="sxs-lookup"><span data-stu-id="162ab-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="162ab-139">Ukazatel na nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="162ab-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="162ab-140">Nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="162ab-140">The native representation of the class</span></span> |

<span data-ttu-id="162ab-141">Následující tabulka obsahuje výchozí zařazování pro pravidla, která jsou jen pro Windows.</span><span class="sxs-lookup"><span data-stu-id="162ab-141">The following table includes the default marshalling rules that are Windows-only.</span></span> <span data-ttu-id="162ab-142">Na platformách než Windows nelze zařadit těchto typů.</span><span class="sxs-lookup"><span data-stu-id="162ab-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="162ab-143">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-143">.NET Type</span></span> | <span data-ttu-id="162ab-144">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="162ab-144">Native Type (Parameter)</span></span> | <span data-ttu-id="162ab-145">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="162ab-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="162ab-146">Rozhraní modelu COM</span><span class="sxs-lookup"><span data-stu-id="162ab-146">COM interface</span></span> | <span data-ttu-id="162ab-147">Není povoleno bez `[MarshalAs]` atribut</span><span class="sxs-lookup"><span data-stu-id="162ab-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="162ab-148">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="162ab-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="162ab-149">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="162ab-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="162ab-150">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="162ab-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="162ab-151">`int64_t` představuje počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="162ab-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="162ab-152">`int64_t` představuje počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="162ab-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="162ab-153">Některé typy může být zařazeno pouze jako parametry a ne jako pole.</span><span class="sxs-lookup"><span data-stu-id="162ab-153">Some types can only be marshalled as parameters and not as fields.</span></span> <span data-ttu-id="162ab-154">Tyto typy jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="162ab-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="162ab-155">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="162ab-155">.NET Type</span></span> | <span data-ttu-id="162ab-156">Nativní typ (pouze parametr)</span><span class="sxs-lookup"><span data-stu-id="162ab-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="162ab-157">Buď `char*` nebo `char16_t*` v závislosti na tom `CharSet` P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="162ab-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="162ab-158">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="162ab-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="162ab-159">`va_list` (pro Windows x86/x64/arm64 jenom)</span><span class="sxs-lookup"><span data-stu-id="162ab-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="162ab-160">Pokud tyto výchozí hodnoty neprovádějte přesně to, co chcete, můžete přizpůsobit, jak zařazeno parametry.</span><span class="sxs-lookup"><span data-stu-id="162ab-160">If these defaults don't do exactly what you want, you can customize how parameters are marshalled.</span></span> <span data-ttu-id="162ab-161">[Zařazování parametru](customize-parameter-marshalling.md) článek vás provede přizpůsobení jak různé typy parametrů zařazeno procházení.</span><span class="sxs-lookup"><span data-stu-id="162ab-161">The [parameter marshalling](customize-parameter-marshalling.md) article walks you through how to customize how different parameter types are marshalled.</span></span>

## <a name="marshalling-classes-and-structs"></a><span data-ttu-id="162ab-162">Zařazování tříd a struktur</span><span class="sxs-lookup"><span data-stu-id="162ab-162">Marshalling classes and structs</span></span>

<span data-ttu-id="162ab-163">Dalším aspektem typu zařazování je jak předat strukturu pro nespravované metody.</span><span class="sxs-lookup"><span data-stu-id="162ab-163">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="162ab-164">Například některé metody nespravovaného vyžadují strukturu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="162ab-164">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="162ab-165">V těchto případech je potřeba vytvořit odpovídající struktury nebo třídy součástí spravované mohli používat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="162ab-165">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="162ab-166">Však stačí definování třídy nestačí, budete potřebovat dáte pokyn, aby zařazování odvozovalo způsob mapování polí ve třídě do nespravované struktury.</span><span class="sxs-lookup"><span data-stu-id="162ab-166">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="162ab-167">Tady `StructLayout` atribut je užitečné.</span><span class="sxs-lookup"><span data-stu-id="162ab-167">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="162ab-168">Předchozí kód ukazuje jednoduchý příklad volání do `GetSystemTime()` funkce.</span><span class="sxs-lookup"><span data-stu-id="162ab-168">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="162ab-169">Zajímavé bit je na řádku 4.</span><span class="sxs-lookup"><span data-stu-id="162ab-169">The interesting bit is on line 4.</span></span> <span data-ttu-id="162ab-170">Atribut určuje, že pole třídy musí být mapována postupně do struktury na druhé straně (nespravovaného).</span><span class="sxs-lookup"><span data-stu-id="162ab-170">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="162ab-171">To znamená, že názvy polí není důležité, že jenom jejich pořadí je důležité, protože je potřeba tak, aby odpovídaly nespravované struktury, je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="162ab-171">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="162ab-172">Výchozí zařazování pro struktury někdy neumí, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="162ab-172">Sometimes the default marshalling for your structure doesn't do what you need.</span></span> <span data-ttu-id="162ab-173">[Přizpůsobení zařazování pro struktury](./customize-struct-marshalling.md) článku se naučíte, jak přizpůsobit, jak je zařadit strukturu.</span><span class="sxs-lookup"><span data-stu-id="162ab-173">The [Customizing structure marshalling](./customize-struct-marshalling.md) article teaches you how to customize how your structure is marshaled.</span></span>
