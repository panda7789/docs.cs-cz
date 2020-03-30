---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s doporučenými postupy pro propojení s nativními součástmi v rozhraní .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391218"
---
# <a name="native-interoperability-best-practices"></a>Nativní osvědčené postupy interoperability

Rozhraní .NET nabízí různé způsoby přizpůsobení nativního kódu interoperability. Tento článek obsahuje pokyny, které microsoft .NET týmy postupujte pro nativní interoperabilitu.

## <a name="general-guidance"></a>Obecné pokyny

Pokyny v této části platí pro všechny scénáře interop.

- ✔️ do použít stejné pojmenování a velká písmena pro vaše metody a parametry jako nativní metody, které chcete volat.
- ✔️ zvážit použití stejného pojmenování a velkých písmen pro konstantní hodnoty.
- ✔️ DO použijte typy .NET, které mapují nejblíže k nativnímu typu. Například v jazyce `uint` C# použijte, `unsigned int`když je nativní typ .
- ✔️ do `[In]` a `[Out]` atributy pouze v případě, že chování, které chcete, se liší od výchozího chování.
- ✔️ zvážit <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> použití k fondu nativní vyrovnávací paměti pole.
- ✔️ ZVAŽTe zabalení deklarací P/Invoke do třídy se stejným názvem a velkými písmeny jako nativní knihovna.
  - To umožňuje `[DllImport]` atributy pomocí funkce `nameof` jazyka C# předat název nativní knihovny a ujistěte se, že jste nechybově název nativní knihovny.

## <a name="dllimport-attribute-settings"></a>Nastavení atributu DllImport

| Nastavení | Výchozí | Doporučení | Podrobnosti |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  zachovat výchozí nastavení  | Pokud je to explicitně nastaveno na false, vrácené hodnoty HRESULT se změní na výjimky (a vrácená hodnota v definici se stane nulovou jako výsledek).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | závisí na API  | Nastavte tuto hodnotu na hodnotu true, pokud rozhraní API používá GetLastError a k získání hodnoty použijte marshal.GetLastWin32Error. Pokud rozhraní API nastaví podmínku, která říká, že má chybu, získejte chybu před provedením dalších volání, aby nedošlo k nechtěnému přepsání.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, který se `CharSet.Ansi` vrací k chování  | Explicitně `CharSet.Unicode` `CharSet.Ansi` použít nebo pokud jsou v definici přítomny řetězce nebo znaky | To určuje zařazování chování `ExactSpelling` řetězců `false`a co dělá, když . Všimněte `CharSet.Ansi` si, že je vlastně UTF8 na Unixu. _Většinu_ času systém Windows používá Unicode, zatímco Unix používá UTF8. Další informace o dokumentaci ke [znakové sady](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Nastavte tuto hodnotu na hodnotu true a získejte nepatrnou výhodu perf, protože modul runtime nebude hledat alternativní `CharSet` názvy funkcí `CharSet.Ansi` s příponou `CharSet.Unicode`"A" nebo "W" v závislosti na hodnotě nastavení ("A" pro a "W" pro ). |

## <a name="string-parameters"></a>Parametry řetězce

Pokud CharSet je Unicode nebo argument `[MarshalAs(UnmanagedType.LPWSTR)]` je explicitně označen jako `ref` _a_ řetězec je předán hodnotou (ne nebo `out`), řetězec bude připnut a používán přímo nativní kód (spíše než zkopírovat).

Nezapomeňte označit `[DllImport]` jako, `Charset.Unicode` pokud výslovně chcete ANSI léčbu vašich řetězců.

❌Nepoužívejte `[Out] string` parametry. Parametry řetězce předané `[Out]` hodnotou s atributem mohou destabilizovat dobu runtime, pokud je řetězec internovaný řetězec. Další informace o interning řetězce <xref:System.String.Intern%2A?displayProperty=nameWithType>v dokumentaci pro .

❌Vyhněte se `StringBuilder` parametrům. `StringBuilder`zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti. Jako takový může být extrémně neefektivní. Vezměte si typický scénář volání rozhraní API systému Windows, který přebírá řetězec:

1. Vytvoření SB požadované kapacity (přiděluje spravovanou kapacitu)**{1}**
2. Invoke
   1. Přidělí nativní vyrovnávací paměť.**{2}**
   2. Zkopíruje obsah, pokud `[In]` _(výchozí pro `StringBuilder` parametr)_
   3. Zkopíruje nativní vyrovnávací paměť do `[Out]` **{3}** nově přiděleného spravovaného pole, pokud _(také výchozí `StringBuilder`pro)_
3. `ToString()`přiděluje další spravované pole**{4}**

To *{4}* je přidělení získat řetězec z nativního kódu. To nejlepší, co můžete udělat pro `StringBuilder` omezení je znovu použít v jiném volání, ale to stále šetří pouze *1* přidělení. Je mnohem lepší použít a uložit do `ArrayPool`mezipaměti vyrovnávací paměť znaků z `ToString()` - pak se můžete dostat dolů pouze přidělení pro následné volání.

Další problém `StringBuilder` s je, že vždy zkopíruje zpětnou vyrovnávací paměť zpět zpět až do první null. Pokud předaný zpětný řetězec není ukončen nebo je řetězec s dvojitou hodnotou null, je p/invoke přinejlepším nesprávný.

Pokud *používáte* `StringBuilder`, jeden poslední gotcha je, že kapacita **neobsahuje** skryté null, který je vždy zaúčtovánv interop. Je běžné, že lidé si to špatně jako většina api chtějí velikost vyrovnávací paměti *včetně* null. To může mít za následek zbytečné přidělení. Navíc tento gotcha zabraňuje runtime optimalizace `StringBuilder` zařazování minimalizovat kopie.

✔️ ZVÁŽIT `char[]`použití `ArrayPool`s z .

Další informace o zařazování řetězců naleznete [v tématu Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).

> __Specifické pro Windows__ Pro `[Out]` řetězce clr bude `CoTaskMemFree` ve výchozím nastavení `SysStringFree` používat k uvolnění řetězců `UnmanagedType.BSTR`nebo pro řetězce, které jsou označeny jako .
> **Pro většinu api s vyrovnávací pamětí výstupního řetězce:** Předaný počet znaků musí obsahovat null. Pokud vrácená hodnota je menší než předán v počtu znaků volání proběhlo úspěšně a hodnota je počet znaků *bez* koncové null. V opačném případě je počet požadovanou velikost vyrovnávací paměti *včetně* nulového znaku.
>
> - Pass in 5, get 4: Řetězec je 4 znaky dlouhé s koncovou hodnotou null.
> - Předat v 5, získat 6: Řetězec je 5 znaků dlouhý, potřebují 6 znaků vyrovnávací paměti pro uložení null.
> [Datové typy systému Windows pro řetězce](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Logické parametry a pole

Booleans jsou snadno zkazit. Ve výchozím nastavení `bool` je rozhraní .NET `BOOL`zařazeno do systému Windows , kde je hodnota 4 bajtů. Však `_Bool`, `bool` a typy v Jazyce C a C++ jsou *jeden* bajt. To může vést k obtížné vystopovat chyby jako polovina vrácená hodnota bude zahozena, což bude pouze *potenciálně* změnit výsledek. Další informace o zařazování hodnot `bool` .NET `bool` do typů jazyka C nebo C++ naleznete v dokumentaci k [přizpůsobení zařazování logického pole](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>Guid

Identifikátory GUID jsou použitelné přímo v podpisech. Mnoho oken API `GUID&` systému `REFIID`Windows trvat aliasy typu jako . Při předání ref, mohou být `ref` předány `[MarshalAs(UnmanagedType.LPStruct)]` nebo s atributem.

| GUID | Identifikátor GUID pro odkaz na odkaz |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌NEPOUŽÍVEJTE `[MarshalAs(UnmanagedType.LPStruct)]` pro nic `ref` jiného než parametry GUID.

## <a name="blittable-types"></a>Přenositelné typy

Přenositelné typy jsou typy, které mají stejnou reprezentaci na úrovni bitů ve spravovaném a nativním kódu. Jako takové není nutné převést do jiného formátu, který má být zařazen do a z nativního kódu, a protože to zlepšuje výkon, měly by být upřednostňovány.

**Přenositelné typy:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- nevnořená jednorozměrná pole přenositelných typů `int[]`(například)
- struktury a třídy s pevným rozložením, které mají pouze přenositelné typy hodnot pro pole instancí
  - pevné rozložení `[StructLayout(LayoutKind.Sequential)]` vyžaduje nebo`[StructLayout(LayoutKind.Explicit)]`
  - struktury jsou `LayoutKind.Sequential` ve výchozím nastavení, třídy jsou`LayoutKind.Auto`

**NENÍ přenositelný:**

- `bool`

**Někdy přenositelný:**

- `char`, `string`

Při přenositelné typy jsou předány odkazem, jsou jednoduše připnul zařazovacím roštinou namísto zkopírování do zprostředkující vyrovnávací paměti. (Třídy jsou ze své podstaty předány odkazem, `ref` `out`struktury jsou předávány odkazem při použití s nebo .)

`char`je přenositelná v jednorozměrném poli **nebo** pokud je součástí typu, který `[StructLayout]` obsahuje, je explicitně označen . `CharSet = CharSet.Unicode`

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`je přenositelný, pokud není obsažen v jiném typu a je předáván `[MarshalAs(UnmanagedType.LPWStr)]` jako `[DllImport]` argument, který je označen nebo má `CharSet = CharSet.Unicode` nastaveno.

Můžete zjistit, zda je typ přenositelný pokusem `GCHandle`o vytvoření připnutého . Pokud typ není řetězec nebo považován za `GCHandle.Alloc` přenositelný, bude hodit `ArgumentException`.

✔️ DO, aby vaše struktury blittable, pokud je to možné.

Další informace naleznete v tématu:

- [Přenositelné a nepřenositelné typy](../../framework/interop/blittable-and-non-blittable-types.md)
- [Zařazování typu](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Udržování spravovaných objektů při životě

`GC.KeepAlive()`zajistí, že objekt zůstane v oboru, dokud není přístupná metoda KeepAlive.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umožňuje zařazovacímu objektu udržovat objekt naživu po dobu trvání P/Invoke. Lze jej použít `IntPtr` místo v podpisech metody. `SafeHandle`účinně nahrazuje tuto třídu a místo toho by měly být použity.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umožňuje připnutí spravovaného objektu a získání nativního ukazatele. Základní vzorec je:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Připnutí není výchozí `GCHandle`pro . Další hlavní vzor je pro předávání odkazu na spravovaný objekt prostřednictvím nativního kódu a zpět na spravovaný kód, obvykle s zpětným voláním. Zde je vzor:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nezapomeňte, že `GCHandle` je třeba explicitně uvolnit, aby se zabránilo nevracení paměti.

## <a name="common-windows-data-types"></a>Běžné datové typy systému Windows

Zde je seznam datových typů běžně používaných v systému Windows API a které c# typy použít při volání do kódu systému Windows.

Následující typy mají stejnou velikost v 32bitovém a 64bitovém systému Windows, a to navzdory jejich názvům.

| impulzu | Windows          | C (Windows)          | C#       | Alternativní                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |

Následující typy, které jsou ukazatele, postupujte podle šířky platformy. `IntPtr` / Použij `UIntPtr` na tohle.

| Typy podepsaných `IntPtr`ukazatelů (použití) | Nepodepsané typy ukazatelů `UIntPtr`(použití) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Systém `PVOID` Windows, který `void*` je C může `IntPtr` `UIntPtr`být zařazen `void*` jako buď nebo , ale raději, pokud je to možné.

[Datové typy systému Windows](/windows/desktop/WinProg/windows-data-types)

[Rozsahy datových typů](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Spravované struktury jsou vytvořeny v zásobníku a nejsou odebrány, dokud se metoda nevrátí. Podle definice pak jsou "připnuté" (nebude se pohybovat gc). Můžete také jednoduše vzít adresu v nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.

Přenositelné struktury jsou mnohem výkonnější, protože mohou být jednoduše použity přímo zařazovací vrstvou. Snažte se, aby struktury blittable `bool`(například vyhnout ). Další informace naleznete v části [Blittable Types.](#blittable-types)

*Pokud* je struktura přenosná, `sizeof()` použijte `Marshal.SizeOf<MyStruct>()` místo pro lepší výkon. Jak bylo uvedeno výše, můžete ověřit, že typ je přenositelný `GCHandle`pokusem o vytvoření připnutého . Pokud typ není řetězec nebo považován za `GCHandle.Alloc` přenositelný, bude hodit `ArgumentException`.

Ukazatele na struktury v definicích musí být `ref` buď `unsafe` `*`předány, nebo použít a .

✔️ DO odpovídají spravované struktury co nejblíže k tvaru a názvy, které se používají v dokumentaci oficiální platformy nebo záhlaví.

✔️ do použít `sizeof()` C# `Marshal.SizeOf<MyStruct>()` místo pro přenositelné struktury ke zlepšení výkonu.

❌Vyhněte se použití `System.Delegate` nebo `System.MulticastDelegate` pole představují pole ukazatele funkce ve strukturách.

Vzhledem k tomu, <xref:System.Delegate?displayProperty=fullName> a <xref:System.MulticastDelegate?displayProperty=fullName> nemají požadovaný podpis, nezaručují, že delegát předán v bude odpovídat podpisu nativní kód očekává. Navíc v rozhraní .NET Framework a .NET Core může `System.Delegate` zařazování struktury obsahující nebo `System.MulticastDelegate` z jeho nativní reprezentace do spravovaného objektu destabilizovat dobu runtime, pokud hodnota pole v nativní reprezentaci není ukazatelem funkce, který zabalí spravovaného delegáta. V rozhraní .NET 5 a novějších verzích není podporováno zařazování pole `System.Delegate` nebo `System.MulticastDelegate` z nativní reprezentace do spravovaného objektu. Místo nebo `System.Delegate` `System.MulticastDelegate`.

### <a name="fixed-buffers"></a>Pevné vyrovnávací paměti

Pole jako `INT_PTR Reserved1[2]` musí být zařazeno `IntPtr` do `Reserved1a` `Reserved1b`dvou polí a . Když nativní pole je primitivní typ, `fixed` můžeme použít klíčové slovo napsat trochu čistěji. Například `SYSTEM_PROCESS_INFORMATION` vypadá takto v nativní záhlaví:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

V C#, můžeme napsat takto:

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

Nicméně, tam jsou některé gotchas s pevnými vyrovnávacími pamětí. Pevné vyrovnávací paměti nepřenositelných typů nebudou správně zařazeny, takže pole na místě musí být rozbaleno do více jednotlivých polí. Navíc v rozhraní .NET Framework a .NET Core před 3.0, pokud je struktura obsahující pevné vyrovnávací pole vnořena do nepřenositelné struktury, nebude pevné vyrovnávací pole správně zařazeno do nativního kódu.
