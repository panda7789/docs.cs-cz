---
title: Zařazování typů – .NET
description: Přečtěte si, jak .NET zařazování vašich typů do nativní reprezentace.
ms.date: 01/18/2019
ms.openlocfilehash: 91b8f3d6cb53fd7a0adea7ea9669e7459e81445f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706263"
---
# <a name="type-marshaling"></a><span data-ttu-id="ae75f-103">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="ae75f-103">Type marshaling</span></span>

<span data-ttu-id="ae75f-104">**Zařazování** je proces transformace typů, když potřebují mezi spravovaným a nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="ae75f-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="ae75f-105">Zařazování je potřeba, protože typy ve spravovaném a nespravovaném kódu se liší.</span><span class="sxs-lookup"><span data-stu-id="ae75f-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="ae75f-106">Ve spravovaném kódu například máte `String`, zatímco v nespravovaných světových řetězcích může být Unicode ("roztažitelné"), ne Unicode, zakončené znakem null, ASCII atd. Ve výchozím nastavení se podsystém P/Invoke pokusí provést správnou funkci na základě výchozího chování, které je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="ae75f-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="ae75f-107">Nicméně pro případy, kdy potřebujete zvýšené řízení, můžete použít atribut [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) k určení toho, co je očekávaného typu na nespravované straně.</span><span class="sxs-lookup"><span data-stu-id="ae75f-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="ae75f-108">Například pokud chcete, aby byl řetězec odeslán jako řetězec ANSI zakončený hodnotou null, můžete to udělat takto:</span><span class="sxs-lookup"><span data-stu-id="ae75f-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="ae75f-109">Výchozí pravidla pro zařazování běžných typů</span><span class="sxs-lookup"><span data-stu-id="ae75f-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="ae75f-110">Obecně platí, že modul runtime se při zařazování pokusí udělat "správnou věc", aby od vás vyžadovala nejmenší množství práce.</span><span class="sxs-lookup"><span data-stu-id="ae75f-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="ae75f-111">Následující tabulky popisují způsob, jakým jsou jednotlivé typy zařazeny ve výchozím nastavení při použití v parametru nebo poli.</span><span class="sxs-lookup"><span data-stu-id="ae75f-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="ae75f-112">Typ Integer a typy znaků s pevnou šířkou C99/C++ 11 se používá k zajištění, že následující tabulka je správná pro všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="ae75f-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="ae75f-113">Můžete použít jakýkoliv nativní typ, který má stejné požadavky na zarovnání a velikost jako tyto typy.</span><span class="sxs-lookup"><span data-stu-id="ae75f-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="ae75f-114">Tato první tabulka popisuje mapování pro různé typy, pro které je zařazování stejné pro volání nespravovaného kódů a polí.</span><span class="sxs-lookup"><span data-stu-id="ae75f-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="ae75f-115">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-115">.NET Type</span></span> | <span data-ttu-id="ae75f-116">Nativní typ</span><span class="sxs-lookup"><span data-stu-id="ae75f-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="ae75f-117">Buď `char`, nebo `char16_t` v závislosti na `CharSet`i nebo v rámci struktury volání nespravovaného systému.</span><span class="sxs-lookup"><span data-stu-id="ae75f-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="ae75f-118">Podívejte se na [dokumentaci k charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="ae75f-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="ae75f-119">Buď `char*`, nebo `char16_t*` v závislosti na `CharSet`i nebo v rámci struktury volání nespravovaného systému.</span><span class="sxs-lookup"><span data-stu-id="ae75f-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="ae75f-120">Podívejte se na [dokumentaci k charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="ae75f-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="ae75f-121">Typy ukazatelů .NET (např.</span><span class="sxs-lookup"><span data-stu-id="ae75f-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="ae75f-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="ae75f-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="ae75f-123">Typ odvozený z `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="ae75f-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="ae75f-124">Typ odvozený z `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="ae75f-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="ae75f-125">Typ `BOOL` Win32</span><span class="sxs-lookup"><span data-stu-id="ae75f-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="ae75f-126">Struktura `DECIMAL` COM</span><span class="sxs-lookup"><span data-stu-id="ae75f-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="ae75f-127">Delegát .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-127">.NET Delegate</span></span> | <span data-ttu-id="ae75f-128">Nativní ukazatel na funkci</span><span class="sxs-lookup"><span data-stu-id="ae75f-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="ae75f-129">Typ `DATE` Win32</span><span class="sxs-lookup"><span data-stu-id="ae75f-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="ae75f-130">Typ `GUID` Win32</span><span class="sxs-lookup"><span data-stu-id="ae75f-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="ae75f-131">Několik kategorií zařazování má jiné výchozí hodnoty, pokud je zařazování jako parametr nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="ae75f-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="ae75f-132">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-132">.NET Type</span></span> | <span data-ttu-id="ae75f-133">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="ae75f-133">Native Type (Parameter)</span></span> | <span data-ttu-id="ae75f-134">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="ae75f-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="ae75f-135">.NET – pole</span><span class="sxs-lookup"><span data-stu-id="ae75f-135">.NET array</span></span> | <span data-ttu-id="ae75f-136">Ukazatel na začátek pole nativní reprezentace prvků pole.</span><span class="sxs-lookup"><span data-stu-id="ae75f-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="ae75f-137">Není povolené bez atributu `[MarshalAs]`.</span><span class="sxs-lookup"><span data-stu-id="ae75f-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="ae75f-138">Třída s `LayoutKind` `Sequential` nebo `Explicit`</span><span class="sxs-lookup"><span data-stu-id="ae75f-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="ae75f-139">Ukazatel na nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="ae75f-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="ae75f-140">Nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="ae75f-140">The native representation of the class</span></span> |

<span data-ttu-id="ae75f-141">Následující tabulka obsahuje výchozí pravidla zařazování, která jsou pouze pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="ae75f-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="ae75f-142">Na platformách jiných než Windows se tyto typy nedají zařadit.</span><span class="sxs-lookup"><span data-stu-id="ae75f-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="ae75f-143">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-143">.NET Type</span></span> | <span data-ttu-id="ae75f-144">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="ae75f-144">Native Type (Parameter)</span></span> | <span data-ttu-id="ae75f-145">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="ae75f-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="ae75f-146">Rozhraní COM</span><span class="sxs-lookup"><span data-stu-id="ae75f-146">COM interface</span></span> | <span data-ttu-id="ae75f-147">Není povolené bez atributu `[MarshalAs]`.</span><span class="sxs-lookup"><span data-stu-id="ae75f-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="ae75f-148">Není povoleno</span><span class="sxs-lookup"><span data-stu-id="ae75f-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="ae75f-149">Není povoleno</span><span class="sxs-lookup"><span data-stu-id="ae75f-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="ae75f-150">Není povoleno</span><span class="sxs-lookup"><span data-stu-id="ae75f-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="ae75f-151">`int64_t` představující počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="ae75f-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="ae75f-152">`int64_t` představující počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="ae75f-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="ae75f-153">Některé typy lze zařadit pouze jako parametry, nikoli jako pole.</span><span class="sxs-lookup"><span data-stu-id="ae75f-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="ae75f-154">Tyto typy jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="ae75f-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="ae75f-155">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-155">.NET Type</span></span> | <span data-ttu-id="ae75f-156">Nativní typ (pouze parametr)</span><span class="sxs-lookup"><span data-stu-id="ae75f-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="ae75f-157">Buď `char*`, nebo `char16_t*` v závislosti na `CharSet` volání nespravovaného volání.</span><span class="sxs-lookup"><span data-stu-id="ae75f-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="ae75f-158">Podívejte se na [dokumentaci k charset](charset.md).</span><span class="sxs-lookup"><span data-stu-id="ae75f-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="ae75f-159">`va_list` (pouze v systému Windows x86/x64/arm64)</span><span class="sxs-lookup"><span data-stu-id="ae75f-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="ae75f-160">Pokud tyto výchozí hodnoty nedělají přesně podle vašich představ, můžete přizpůsobit způsob, jakým jsou zařazování parametrů.</span><span class="sxs-lookup"><span data-stu-id="ae75f-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="ae75f-161">Článek [zařazování parametrů](customize-parameter-marshaling.md) vás provede postupem přizpůsobení způsobu, jakým jsou zařazování různých typů parametrů.</span><span class="sxs-lookup"><span data-stu-id="ae75f-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="ae75f-162">Výchozí zařazování ve scénářích modelu COM</span><span class="sxs-lookup"><span data-stu-id="ae75f-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="ae75f-163">Při volání metod v objektech COM v rozhraní .NET modul runtime aplikace změní výchozí pravidla zařazování tak, aby odpovídala běžným sémantikám modelu COM.</span><span class="sxs-lookup"><span data-stu-id="ae75f-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="ae75f-164">V následující tabulce jsou uvedena pravidla, která prostředí .NET runtime používají ve scénářích modelu COM:</span><span class="sxs-lookup"><span data-stu-id="ae75f-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="ae75f-165">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="ae75f-165">.NET Type</span></span> | <span data-ttu-id="ae75f-166">Nativní typ (volání metod COM)</span><span class="sxs-lookup"><span data-stu-id="ae75f-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="ae75f-167">Typy delegátů</span><span class="sxs-lookup"><span data-stu-id="ae75f-167">Delegate types</span></span> | <span data-ttu-id="ae75f-168">`_Delegate*` v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae75f-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="ae75f-169">Zakázáno v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae75f-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="ae75f-170">.NET – pole</span><span class="sxs-lookup"><span data-stu-id="ae75f-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="ae75f-171">`SAFEARRAY` `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="ae75f-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="ae75f-172">Zařazování tříd a struktur</span><span class="sxs-lookup"><span data-stu-id="ae75f-172">Marshaling classes and structs</span></span>

<span data-ttu-id="ae75f-173">Dalším aspektem zařazování typů je předání struktury do nespravované metody.</span><span class="sxs-lookup"><span data-stu-id="ae75f-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="ae75f-174">Například některé z nespravovaných metod vyžadují strukturu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="ae75f-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="ae75f-175">V těchto případech je potřeba vytvořit odpovídající strukturu nebo třídu ve spravované části světa a použít ji jako parametr.</span><span class="sxs-lookup"><span data-stu-id="ae75f-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="ae75f-176">Avšak pouze definování třídy není dostatečné, je také nutné instruovat zařazování, jak mapovat pole ve třídě na nespravovanou strukturu.</span><span class="sxs-lookup"><span data-stu-id="ae75f-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="ae75f-177">Tady se atribut `StructLayout` hodí.</span><span class="sxs-lookup"><span data-stu-id="ae75f-177">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="ae75f-178">Předchozí kód ukazuje jednoduchý příklad volání do funkce `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="ae75f-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="ae75f-179">Zajímavý bit je na řádku 4.</span><span class="sxs-lookup"><span data-stu-id="ae75f-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="ae75f-180">Atribut určuje, že pole třídy by měly být postupně mapovány na strukturu na druhé (nespravované) straně.</span><span class="sxs-lookup"><span data-stu-id="ae75f-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="ae75f-181">To znamená, že názvy polí nejsou důležité, pouze jejich pořadí je důležité, protože musí odpovídat nespravované struktuře, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ae75f-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="ae75f-182">Někdy výchozí zařazování pro vaši strukturu neudělá to, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="ae75f-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="ae75f-183">Článek [přizpůsobení strukturování struktur](./customize-struct-marshaling.md) vás seznámí s postupem přizpůsobení struktury vaší struktury.</span><span class="sxs-lookup"><span data-stu-id="ae75f-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
