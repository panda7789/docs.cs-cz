---
title: Zadejte zařazování – .NET
description: Zjistěte, jak .NET zařazuje vaše typy pro nativní reprezentace.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2cb8898b52b4b4afba1184a886e16c9f7f68f03a
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041782"
---
# <a name="type-marshaling"></a><span data-ttu-id="9ab75-103">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="9ab75-103">Type marshaling</span></span>

<span data-ttu-id="9ab75-104">**Zařazování** je proces transformace typy, když je budou potřebovat pro různé mezi spravovaný a nativní kód.</span><span class="sxs-lookup"><span data-stu-id="9ab75-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="9ab75-105">Zařazování je potřeba, protože se liší typy v spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="9ab75-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="9ab75-106">Ve spravovaném kódu, například můžete mít `String`, zatímco nespravované světě mohou být řetězce Unicode ("širokých"), kódování Unicode, zakončený hodnotou null, ASCII, atd. Ve výchozím nastavení P/Invoke subsystému pokouší provést správné věci na základě výchozí chování, je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="9ab75-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="9ab75-107">Pro tyto situace, kdy potřebujete další ovládací prvek, ale můžete použít [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) atribut k určení, co je očekávaný typ v nespravované oblasti.</span><span class="sxs-lookup"><span data-stu-id="9ab75-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="9ab75-108">Například pokud chcete řetězec, který má být odeslán jako ANSI řetězec zakončený hodnotou null, lze nastavit takto:</span><span class="sxs-lookup"><span data-stu-id="9ab75-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="9ab75-109">Výchozí pravidla pro zařazování běžných typů</span><span class="sxs-lookup"><span data-stu-id="9ab75-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="9ab75-110">Obecně platí, modul runtime pokusí provést "správné věci" při zařazování tak, aby vyžadovala minimální množství práce, které od vás.</span><span class="sxs-lookup"><span data-stu-id="9ab75-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="9ab75-111">Následující tabulky popisují, jak je zařadit každý typ, ve výchozím nastavení při použití v parametru nebo pole.</span><span class="sxs-lookup"><span data-stu-id="9ab75-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="9ab75-112">C99 / C ++ 11 celočíselné neproporcionální a typy znaků se používají k ověření, že v následující tabulce je správná pro všechny platformy.</span><span class="sxs-lookup"><span data-stu-id="9ab75-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="9ab75-113">Můžete použít nativní typ, který má stejné zarovnání a požadavky na velikost jako tyto typy.</span><span class="sxs-lookup"><span data-stu-id="9ab75-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="9ab75-114">V první tabulce popisuje mapování pro různé typy, pro které zařazování je stejný pro P/Invoke a zařazování pole.</span><span class="sxs-lookup"><span data-stu-id="9ab75-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="9ab75-115">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-115">.NET Type</span></span> | <span data-ttu-id="9ab75-116">Nativní typ</span><span class="sxs-lookup"><span data-stu-id="9ab75-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="9ab75-117">Buď `char` nebo `char16_t` v závislosti na tom `CharSet` P/Invoke nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9ab75-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="9ab75-118">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="9ab75-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="9ab75-119">Buď `char*` nebo `char16_t*` v závislosti na tom `CharSet` P/Invoke nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9ab75-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="9ab75-120">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="9ab75-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="9ab75-121">Typy ukazatelů rozhraní .NET (např.)</span><span class="sxs-lookup"><span data-stu-id="9ab75-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="9ab75-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="9ab75-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="9ab75-123">Typ odvozený od `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="9ab75-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="9ab75-124">Typ odvozený od `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="9ab75-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="9ab75-125">Win32 `BOOL` typu</span><span class="sxs-lookup"><span data-stu-id="9ab75-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="9ab75-126">COM `DECIMAL` – struktura</span><span class="sxs-lookup"><span data-stu-id="9ab75-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="9ab75-127">Delegát .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-127">.NET Delegate</span></span> | <span data-ttu-id="9ab75-128">Ukazatel na nativní funkci</span><span class="sxs-lookup"><span data-stu-id="9ab75-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="9ab75-129">Win32 `DATE` typu</span><span class="sxs-lookup"><span data-stu-id="9ab75-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="9ab75-130">Win32 `GUID` typu</span><span class="sxs-lookup"><span data-stu-id="9ab75-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="9ab75-131">Několik kategorií zařazování používají různé výchozí hodnoty, pokud jste zařazování jako parametr nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="9ab75-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="9ab75-132">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-132">.NET Type</span></span> | <span data-ttu-id="9ab75-133">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="9ab75-133">Native Type (Parameter)</span></span> | <span data-ttu-id="9ab75-134">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="9ab75-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="9ab75-135">Pole .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-135">.NET array</span></span> | <span data-ttu-id="9ab75-136">Ukazatel na začátku pole nativní reprezentace prvků pole.</span><span class="sxs-lookup"><span data-stu-id="9ab75-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="9ab75-137">Není povoleno bez `[MarshalAs]` atribut</span><span class="sxs-lookup"><span data-stu-id="9ab75-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="9ab75-138">Třída s atributem `LayoutKind` z `Sequential` nebo `Explicit`</span><span class="sxs-lookup"><span data-stu-id="9ab75-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="9ab75-139">Ukazatel na nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="9ab75-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="9ab75-140">Nativní reprezentace třídy</span><span class="sxs-lookup"><span data-stu-id="9ab75-140">The native representation of the class</span></span> |

<span data-ttu-id="9ab75-141">Následující tabulka obsahuje výchozí pravidla, která jsou zařazování jen pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9ab75-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="9ab75-142">Na platformách než Windows nelze zařadit těchto typů.</span><span class="sxs-lookup"><span data-stu-id="9ab75-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="9ab75-143">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-143">.NET Type</span></span> | <span data-ttu-id="9ab75-144">Nativní typ (parametr)</span><span class="sxs-lookup"><span data-stu-id="9ab75-144">Native Type (Parameter)</span></span> | <span data-ttu-id="9ab75-145">Nativní typ (pole)</span><span class="sxs-lookup"><span data-stu-id="9ab75-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="9ab75-146">Rozhraní modelu COM</span><span class="sxs-lookup"><span data-stu-id="9ab75-146">COM interface</span></span> | <span data-ttu-id="9ab75-147">Není povoleno bez `[MarshalAs]` atribut</span><span class="sxs-lookup"><span data-stu-id="9ab75-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="9ab75-148">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="9ab75-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="9ab75-149">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="9ab75-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="9ab75-150">Nepovoleno</span><span class="sxs-lookup"><span data-stu-id="9ab75-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="9ab75-151">`int64_t` představuje počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="9ab75-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="9ab75-152">`int64_t` představuje počet taktů od půlnoci 1. ledna 1601</span><span class="sxs-lookup"><span data-stu-id="9ab75-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="9ab75-153">Některé typy mohou být zařazována pouze jako parametry a ne jako pole.</span><span class="sxs-lookup"><span data-stu-id="9ab75-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="9ab75-154">Tyto typy jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="9ab75-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="9ab75-155">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-155">.NET Type</span></span> | <span data-ttu-id="9ab75-156">Nativní typ (pouze parametr)</span><span class="sxs-lookup"><span data-stu-id="9ab75-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="9ab75-157">Buď `char*` nebo `char16_t*` v závislosti na tom `CharSet` P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="9ab75-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="9ab75-158">Zobrazit [znaková sada dokumentace](charset.md).</span><span class="sxs-lookup"><span data-stu-id="9ab75-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="9ab75-159">`va_list` (pro Windows x86/x64/arm64 jenom)</span><span class="sxs-lookup"><span data-stu-id="9ab75-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="9ab75-160">Pokud tyto výchozí hodnoty neprovádějte přesně to, co chcete, můžete přizpůsobit, jak zařadit parametry.</span><span class="sxs-lookup"><span data-stu-id="9ab75-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="9ab75-161">[Zařazování parametru](customize-parameter-marshaling.md) článek vás provede přizpůsobení jak různé typy parametrů, jsou zařazeny procházení.</span><span class="sxs-lookup"><span data-stu-id="9ab75-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="9ab75-162">Výchozí zařazování ve scénářích modelu COM</span><span class="sxs-lookup"><span data-stu-id="9ab75-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="9ab75-163">Při volání metod na objekty modelu COM v rozhraní .NET, modul .NET runtime změní výchozí pravidla tak aby odpovídala sémantiky společné COM zařazování.</span><span class="sxs-lookup"><span data-stu-id="9ab75-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="9ab75-164">Následující tabulka uvádí pravidla, která moduly .NET runtime používá ve scénářích COM:</span><span class="sxs-lookup"><span data-stu-id="9ab75-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="9ab75-165">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-165">.NET Type</span></span> | <span data-ttu-id="9ab75-166">Nativní typ (volání metody COM)</span><span class="sxs-lookup"><span data-stu-id="9ab75-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="9ab75-167">Typy delegátů</span><span class="sxs-lookup"><span data-stu-id="9ab75-167">Delegate types</span></span> | <span data-ttu-id="9ab75-168">`_Delegate*` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ab75-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="9ab75-169">Nepovolené v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ab75-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="9ab75-170">Pole .NET</span><span class="sxs-lookup"><span data-stu-id="9ab75-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="9ab75-171">`SAFEARRAY` z `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="9ab75-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="9ab75-172">Zařazování tříd a struktur</span><span class="sxs-lookup"><span data-stu-id="9ab75-172">Marshaling classes and structs</span></span>

<span data-ttu-id="9ab75-173">Dalším aspektem typu zařazování je jak předat strukturu pro nespravované metody.</span><span class="sxs-lookup"><span data-stu-id="9ab75-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="9ab75-174">Například některé metody nespravovaného vyžadují strukturu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9ab75-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="9ab75-175">V těchto případech je potřeba vytvořit odpovídající struktury nebo třídy součástí spravované mohli používat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9ab75-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="9ab75-176">Však stačí definování třídy nestačí, budete potřebovat dáte pokyn, aby zařazování odvozovalo způsob mapování polí ve třídě do nespravované struktury.</span><span class="sxs-lookup"><span data-stu-id="9ab75-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="9ab75-177">Tady `StructLayout` atribut je užitečné.</span><span class="sxs-lookup"><span data-stu-id="9ab75-177">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="9ab75-178">Předchozí kód ukazuje jednoduchý příklad volání do `GetSystemTime()` funkce.</span><span class="sxs-lookup"><span data-stu-id="9ab75-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="9ab75-179">Zajímavé bit je na řádku 4.</span><span class="sxs-lookup"><span data-stu-id="9ab75-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="9ab75-180">Atribut určuje, že pole třídy musí být mapována postupně do struktury na druhé straně (nespravovaného).</span><span class="sxs-lookup"><span data-stu-id="9ab75-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="9ab75-181">To znamená, že názvy polí není důležité, že jenom jejich pořadí je důležité, protože je potřeba tak, aby odpovídaly nespravované struktury, je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9ab75-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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

<span data-ttu-id="9ab75-182">Výchozí zařazování pro struktury někdy neumí, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9ab75-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="9ab75-183">[Přizpůsobení struktura zařazování](./customize-struct-marshaling.md) článku se naučíte, jak přizpůsobit, jak je zařadit strukturu.</span><span class="sxs-lookup"><span data-stu-id="9ab75-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
