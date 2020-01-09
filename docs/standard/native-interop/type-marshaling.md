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
# <a name="type-marshaling"></a>Zařazování typů

**Zařazování** je proces transformace typů, když potřebují mezi spravovaným a nativním kódem.

Zařazování je potřeba, protože typy ve spravovaném a nespravovaném kódu se liší. Ve spravovaném kódu například máte `String`, zatímco v nespravovaných světových řetězcích může být Unicode ("roztažitelné"), ne Unicode, zakončené znakem null, ASCII atd. Ve výchozím nastavení se podsystém P/Invoke pokusí provést správnou funkci na základě výchozího chování, které je popsáno v tomto článku. Nicméně pro případy, kdy potřebujete zvýšené řízení, můžete použít atribut [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) k určení toho, co je očekávaného typu na nespravované straně. Například pokud chcete, aby byl řetězec odeslán jako řetězec ANSI zakončený hodnotou null, můžete to udělat takto:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a>Výchozí pravidla pro zařazování běžných typů

Obecně platí, že modul runtime se při zařazování pokusí udělat "správnou věc", aby od vás vyžadovala nejmenší množství práce. Následující tabulky popisují způsob, jakým jsou jednotlivé typy zařazeny ve výchozím nastavení při použití v parametru nebo poli. Typ Integer a typy znaků s pevnou šířkou C99/C++ 11 se používá k zajištění, že následující tabulka je správná pro všechny platformy. Můžete použít jakýkoliv nativní typ, který má stejné požadavky na zarovnání a velikost jako tyto typy.

Tato první tabulka popisuje mapování pro různé typy, pro které je zařazování stejné pro volání nespravovaného kódů a polí.

| Typ .NET | Nativní typ  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | Buď `char`, nebo `char16_t` v závislosti na `CharSet`i nebo v rámci struktury volání nespravovaného systému. Podívejte se na [dokumentaci k charset](charset.md). |
| `string`  | Buď `char*`, nebo `char16_t*` v závislosti na `CharSet`i nebo v rámci struktury volání nespravovaného systému. Podívejte se na [dokumentaci k charset](charset.md). |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| Typy ukazatelů .NET (např. `void*`)  | `void*` |
| Typ odvozený z `System.Runtime.InteropServices.SafeHandle` | `void*` |
| Typ odvozený z `System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Typ `BOOL` Win32       |
| `decimal` | Struktura `DECIMAL` COM |
| Delegát .NET | Nativní ukazatel na funkci |
| `System.DateTime` | Typ `DATE` Win32 |
| `System.Guid` | Typ `GUID` Win32 |

Několik kategorií zařazování má jiné výchozí hodnoty, pokud je zařazování jako parametr nebo struktura.

| Typ .NET | Nativní typ (parametr) | Nativní typ (pole) |
|-----------|-------------------------|---------------------|
| .NET – pole | Ukazatel na začátek pole nativní reprezentace prvků pole. | Není povolené bez atributu `[MarshalAs]`.|
| Třída s `LayoutKind` `Sequential` nebo `Explicit` | Ukazatel na nativní reprezentace třídy | Nativní reprezentace třídy |

Následující tabulka obsahuje výchozí pravidla zařazování, která jsou pouze pro systém Windows. Na platformách jiných než Windows se tyto typy nedají zařadit.

| Typ .NET | Nativní typ (parametr) | Nativní typ (pole) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | Rozhraní COM | Není povolené bez atributu `[MarshalAs]`. |
| `System.ArgIterator` | `va_list` | Není povoleno |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | Není povoleno |
| `System.Collections.IEnumerable` | `IDispatch*` | Není povoleno |
| `System.DateTimeOffset` | `int64_t` představující počet taktů od půlnoci 1. ledna 1601 || `int64_t` představující počet taktů od půlnoci 1. ledna 1601 |

Některé typy lze zařadit pouze jako parametry, nikoli jako pole. Tyto typy jsou uvedeny v následující tabulce:

| Typ .NET | Nativní typ (pouze parametr) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | Buď `char*`, nebo `char16_t*` v závislosti na `CharSet` volání nespravovaného volání.  Podívejte se na [dokumentaci k charset](charset.md). |
| `System.ArgIterator` | `va_list` (pouze v systému Windows x86/x64/arm64) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Pokud tyto výchozí hodnoty nedělají přesně podle vašich představ, můžete přizpůsobit způsob, jakým jsou zařazování parametrů. Článek [zařazování parametrů](customize-parameter-marshaling.md) vás provede postupem přizpůsobení způsobu, jakým jsou zařazování různých typů parametrů.

## <a name="default-marshaling-in-com-scenarios"></a>Výchozí zařazování ve scénářích modelu COM

Při volání metod v objektech COM v rozhraní .NET modul runtime aplikace změní výchozí pravidla zařazování tak, aby odpovídala běžným sémantikám modelu COM. V následující tabulce jsou uvedena pravidla, která prostředí .NET runtime používají ve scénářích modelu COM:

| Typ .NET | Nativní typ (volání metod COM) |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| Typy delegátů | `_Delegate*` v .NET Framework. Zakázáno v .NET Core. |
| `System.Drawing.Color` | `OLECOLOR`        |
| .NET – pole | `SAFEARRAY`                   |
| `string[]` | `SAFEARRAY` `BSTR`s        |

## <a name="marshaling-classes-and-structs"></a>Zařazování tříd a struktur

Dalším aspektem zařazování typů je předání struktury do nespravované metody. Například některé z nespravovaných metod vyžadují strukturu jako parametr. V těchto případech je potřeba vytvořit odpovídající strukturu nebo třídu ve spravované části světa a použít ji jako parametr. Avšak pouze definování třídy není dostatečné, je také nutné instruovat zařazování, jak mapovat pole ve třídě na nespravovanou strukturu. Tady se atribut `StructLayout` hodí.

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

Předchozí kód ukazuje jednoduchý příklad volání do funkce `GetSystemTime()`. Zajímavý bit je na řádku 4. Atribut určuje, že pole třídy by měly být postupně mapovány na strukturu na druhé (nespravované) straně. To znamená, že názvy polí nejsou důležité, pouze jejich pořadí je důležité, protože musí odpovídat nespravované struktuře, jak je znázorněno v následujícím příkladu:

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

Někdy výchozí zařazování pro vaši strukturu neudělá to, co potřebujete. Článek [přizpůsobení strukturování struktur](./customize-struct-marshaling.md) vás seznámí s postupem přizpůsobení struktury vaší struktury.
