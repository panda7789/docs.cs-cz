---
title: Nativní interoperabilita osvědčené postupy – .NET
description: Podívejte se na osvědčené postupy pro propojení s nativními komponentami v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 5b65f80d3a81fab0d74ce26aec3b454c716a5d51
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412055"
---
# <a name="native-interoperability-best-practices"></a>Osvědčené postupy nativní interoperabilita

.NET nabízí celou řadu způsobů, jak přizpůsobit interoperabilitu nativní kód. Tento článek obsahuje pokyny, které následují .NET týmy Microsoftu pro interoperabilitu nativní.

## <a name="general-guidance"></a>Obecné pokyny

Pokyny v této části platí pro všechny scénáře spolupráce.

- **PROVEĎTE ✔️** používat stejné pojmenování a malá a velká písmena jako nativní metody, kterou chcete volat pro metody a parametrů.
- **✔️ ZVAŽTE** pomocí stejného pojmenování a velkých písmen pro konstantní hodnoty.
- **PROVEĎTE ✔️** typy .NET, které se nachází nejblíže mapují na nativní typ použít. Například v C#, použijte `uint` Pokud je nativní typ `unsigned int`.
- **PROVEĎTE ✔️** používat pouze `[In]` a `[Out]` atributy, pokud chcete, aby chování se liší od výchozí chování.
- **✔️ ZVAŽTE** pomocí <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vyrovnávací paměti vaší nativní pole.
- **✔️ ZVAŽTE** ve třídě se stejným názvem a velká písmena jako nativní knihovnu pro zabalení vaší deklarace P/Invoke.
  - To umožňuje vaší `[DllImport]` atributů, které mají používat C# `nameof` funkci jazyka předat název nativní knihovnu a ujistěte se, že název nativní knihovny nebyla mít překlep.

## <a name="dllimport-attribute-settings"></a>Nastavení atributu DllImport

| Nastavení | Výchozí | Doporučení | Podrobnosti |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Ponechat výchozí  | Pokud to explicitně nastavená na false, neúspěšných vrácené hodnoty HRESULT bude převeden na výjimky (a vrácená hodnota v definici změní na hodnotu null v důsledku).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | závisí na rozhraní API  | Nastavte tuto hodnotu na hodnotu true, pokud používá funkce GetLastError rozhraní API a použít Marshal.GetLastWin32Error má být získána hodnota. Pokud rozhraní API nastavte podmínku, která říká, že došlo k chybě, zobrazí chybová zpráva před provedením další volání vyhnout neúmyslně jej přepsat.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, který spadne zpět na `CharSet.Ansi` chování  | Explicitně `CharSet.Unicode` nebo `CharSet.Ansi` když řetězce nebo znaků, jsou k dispozici v definici | Určuje chování sběrného systému řetězců a co `ExactSpelling` když `false`. Všimněte si, že `CharSet.Ansi` je ve skutečnosti UTF8 v systému Unix. _Většina_ času Windows používá kódování Unicode, zatímco Unix používá UTF8. Další informace o naleznete [dokumentaci o znakových sad](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Nastavte tuto hodnotu na true a získat výhody mírné výkonu jako modul runtime nebude hledat názvy alternativní funkcí s příponou buď "A" nebo "W" v závislosti na hodnotu `CharSet` nastavení ("A" pro `CharSet.Ansi` a "W" pro `CharSet.Unicode`). |

## <a name="string-parameters"></a>Parametry řetězce

Když je znakové sady Unicode nebo argument je explicitně označena jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán podle hodnoty (ne `ref` nebo `out`), řetězec připnuté, který se používá nativní kód (spíše než zkopíruje).

Mějte na paměti k označení `[DllImport]` jako `Charset.Unicode` Pokud chcete explicitně ANSI zacházení s řetězci.

**❌ NEPODPORUJÍ** použít `[Out] string` parametry. Řetězec, předán podle hodnoty s parametry `[Out]` atribut můžou destabilizovat modul runtime, pokud řetězec je interned řetězec. Další informace o interning řetězce v dokumentaci k <xref:System.String.Intern%2A?displayProperty=nameWithType>.

**❌ Nepoužívejte** `StringBuilder` parametry. `StringBuilder` zařazování *vždy* vytvoří kopii nativní vyrovnávací paměti. V důsledku toho může být velmi neefektivní. Využijte Typický scénář volání Windows API, která přebírá řetězec:

1. Vytvoření SB požadovanou kapacitu (přidělí kapacita managed) **{1}**
2. Vyvolat
   1. Přidělí nativní vyrovnávací paměť **{2}**  
   2. Zkopíruje obsah, když `[In]` _(výchozí nastavení pro `StringBuilder` parametr)_  
   3. Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole, když `[Out]` **{3}** _(také výchozí `StringBuilder`)_  
3. `ToString()` přiděluje další spravovaného pole **{4}**

To znamená *{4}* přidělení získat řetězec z nativního kódu. Nejlepší způsobů, jak toto omezení je znovu použít `StringBuilder` v jiného volání, ale tím se ušetří stále pouze *1* přidělení. Je mnohem lepší použít a ukládat do vyrovnávací paměti pro znaky z mezipaměti `ArrayPool`-pak můžete získat k přidělení pro `ToString()` při dalších volání.

Problém s `StringBuilder` je, že vždy kopíruje návratové vyrovnávací paměti zálohování do první hodnotu null. Pokud back předaný řetězec není ukončený nebo je dvojitou hodnotu null ukončující řetězec, je deklarace P/Invoke nesprávný nejlépe.

Pokud jste *proveďte* použít `StringBuilder`, jeden poslední gotcha je, že se kapacita **není** zahrnout skryté null, který je vždy zahrnuté v zprostředkovatele komunikace s objekty. Je běžné, že lidé se to získat nesprávná, protože většina rozhraní API má velikost vyrovnávací paměti *včetně* hodnotu null. Výsledkem může být ztraceny, a zbytečné přidělení. Kromě toho tato gotcha zabraňuje modulu runtime optimalizace `StringBuilder` minimalizovat kopie sběrného systému.

**✔️ ZVAŽTE** pomocí `char[]`s ze `ArrayPool`.

Další informace o zařazování pro řetězce, naleznete v tématu [výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování pro řetězce](customize-parameter-marshalling.md#customizing-string-parameters).

> __Specifické pro Windows__  
> Pro `[Out]` řetězce CLR použije `CoTaskMemFree` ve výchozím nastavení uvolnit řetězce nebo `SysStringFree` pro řetězce, které jsou označeny jako `UnmanagedType.BSTR`.  
**Většina rozhraní API s řetězci výstupní vyrovnávací paměť:**  
> Předaný v znaku musí obsahovat počet hodnotu null. Pokud vrácená hodnota je menší než předaný počet znaků v úspěšném volání a hodnota je počet znaků *bez* koncovou hodnotu null. Jinak je požadovaná velikost vyrovnávací paměti počet *včetně* znak null.  
> - Předejte 5, 4 získat: Řetězec je 4 znaky dlouhý s koncovou hodnotou null.
> - Předejte 5, 6 získat: Řetězec je 5 znaků, třeba 6 znaků vyrovnávací paměť pro uchování hodnotu null.  
> [Datové typy Windows pro řetězce](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Logické parametry a pole

Logické hodnoty jsou snadno schválně pokazí. Ve výchozím nastavení, .NET `bool` je zařazeno do Windows `BOOL`, kde je to hodnota 4 bajty. Ale `_Bool`, a `bool` jsou typy v jazyce C a C++ *jeden* bajtů. To může vést k náročné sledovat chyby jako poloviční návratová hodnota se zahodí, který bude pouze *potenciálně* změnit výsledek. Další informace o zařazování .NET `bool` hodnoty do jazyka C nebo C++ `bool` typy, naleznete v dokumentaci [přizpůsobení zařazování pro pole logickou](customize-struct-marshalling.md#customizing-boolean-field-marshalling).

## <a name="guids"></a>Identifikátory GUID

Lze použít přímo v signaturách identifikátory GUID. Mnoho rozhraní Windows API využít `GUID&` zadejte aliasy jako `REFIID`. Když předány podle odkazu, je můžete předat buď `ref` nebo se `[MarshalAs(UnmanagedType.LPStruct)]` atribut.

| GUID | Identifikátor GUID podle odkazu |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**❌ NEPODPORUJÍ** použití `[MarshalAs(UnmanagedType.LPStruct)]` pro nic jiného než `ref` parametry identifikátor GUID.

## <a name="blittable-types"></a>Přenositelné typy

Přenositelné typy jsou typy, které mají stejnou reprezentaci úrovni bitů v spravovaného a nativního kódu. Proto není nutné pro převod na jiném formátu tak být zařazeno do a z nativního kódu a jak to zvyšuje výkon se bude upřednostňovat.

**Přenositelné typy:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- -nested jednorozměrné pole přenositelné typy (například `int[]`)
- struktury a třídy s pevným rozložením, které mít pouze hodnotu přenositelné typy pro instanci pole
  - pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo `[StructLayout(LayoutKind.Explicit)]`
  - struktury jsou `LayoutKind.Sequential` jsou standardně třídy `LayoutKind.Auto`

**NENÍ typu blittable:**

- `bool`

**NĚKDY blittable:**

- `char`, `string`

Když přenositelné typy jsou předány podle odkazu, se jednoduše připnout podle marshaller namísto kopírování do zprostředkující vyrovnávací paměti. (Třídy jsou ze své podstaty předány podle odkazu, struktur jsou předány podle odkazu při použití s `ref` nebo `out`.)

`char` přenositelné v jednorozměrné pole je **nebo** Pokud se jedná o typ, který ji obsahuje je explicitně označena `[StructLayout]` s `CharSet = CharSet.Unicode`.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` je typu blittable, pokud není obsažen v jiném typu a je předávána jako argument, který je označen `[MarshalAs(UnmanagedType.LPWStr)]` nebo `[DllImport]` má `CharSet = CharSet.Unicode` nastavit.

Můžete zobrazit, pokud je typu blittable pokusem o vytvoření připnutého `GCHandle`. Pokud typ není řetězec nebo považovat za blittable, `GCHandle.Alloc` vyvolá výjimku `ArgumentException`.

**PROVEĎTE ✔️** Ujistěte se, vaši blittable struktury, pokud je to možné.

Další informace naleznete v tématu:

- [Přenositelné a nepřenositelné typy](../../framework/interop/blittable-and-non-blittable-types.md)  
- [Zařazování typů](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a>Ponechání spravovaných objektů, které jsou aktivní

`GC.KeepAlive()` zajistí, že objekt zůstane v oboru až do dosažení metodu KeepAlive.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) Umožňuje marshaller k zachování objektu po dobu trvání P/Invoke. Je možné místo `IntPtr` v podpisy metod. `SafeHandle` efektivně nahrazuje této třídy a místo toho by měla sloužit.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) Umožňuje Připnutí spravovaný objekt a získávání nativní ukazatel na ni. Základní model je:  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Připnutí není výchozí nastavení pro `GCHandle`. Další hlavní vzor je odkaz na spravovaný objekt prostřednictvím nativního kódu a zpět do spravovaného kódu, obvykle pomocí zpětného volání při předávání. Toto je vzor:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nezapomeňte, že `GCHandle` musí být explicitně uvolněna, aby nevracení paměti.

## <a name="common-windows-data-types"></a>Běžné typy dat Windows

Tady je seznam datových typů používaných v rozhraní Windows API a které C# typů pro použití při volání do kódu Windows.

Následující typy mají stejnou velikost na 32bitová verze a 64bitová verze Windows, bez ohledu na jejich názvy.

| Šířka | Windows          | C (Windows)          | C#       | Alternativní                          |
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


Následující typy ukazatelů, se podle šířku platformy. Použití `IntPtr` / `UIntPtr` pro tyto.

| Podepsané typy ukazatelů (použijte `IntPtr`) | Typy ukazatelů, bez znaménka (použijte `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Windows `PVOID` tedy C `void*` můžete zařadit jako buď `IntPtr` nebo `UIntPtr`, ale dáváte přednost `void*` Pokud je to možné.

[Datové typy Windows](/windows/desktop/WinProg/windows-data-types)

[Rozsahy datových typů](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Spravované struktury jsou vytvořeny v zásobníku a se neodeberou, dokud se metoda vrátí. Podle definice a pak, že nejsou "připnuté" (nebudete získáte přesunout uvolňování paměti). Můžete také jednoduše provést adresu v nezabezpečený kód bloky Pokud nativního kódu nebude používat ukazatel ukazující za aktuální metody.

Přenositelné struktury jsou výrazně výkonnější jako může být jednoduše použít přímo ve vrstvě sběrného systému. Pokuste se uskutečnit blittable struktury (například vyhnout `bool`). Další informace najdete v tématu [přenositelné typy](#blittable-types) oddílu.

*Pokud* struktury je typu blittable, použijte `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro zajištění lepšího výkonu. Jak je uvedeno výše, můžete ověřit, že je typu blittable pokusem o vytvoření připnutého `GCHandle`. Pokud typ není řetězec nebo považovat za blittable, `GCHandle.Alloc` vyvolá výjimku `ArgumentException`.

Odkazy na struktury v definicích se musí buď předávat `ref` nebo použijte `unsafe` a `*`.

**PROVEĎTE ✔️** odpovídat spravovaná struktura co nejpřesněji tvar a názvy, které se používají v dokumentaci oficiální platforma nebo hlavičce.

**PROVEĎTE ✔️** použít C# `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro struktury blittable ke zlepšení výkonu.

Pole, jako jsou `INT_PTR Reserved1[2]` musí být zařazen do dvou `IntPtr` pole, `Reserved1a` a `Reserved1b`. Pokud je nativní pole primitivní typ, můžeme použít `fixed` – klíčové slovo pro zápis o něco více čistě. Například `SYSTEM_PROCESS_INFORMATION` vypadá přibližně takto v hlavičce nativní:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

V C#, nám můžete napsat takto:

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

Existují však některé možná úskalí s pevných vyrovnávacích pamětí. Nepřenositelné typy pevných vyrovnávacích pamětí nesmí být zařazeno správně, tak místní pole vyžaduje rozbalen navýšení kapacity na několik jednotlivá pole. Navíc v rozhraní .NET Framework a .NET Core před 3.0, pokud je vnořená struktura obsahující vyrovnávací paměť pevné pole v rámci nepřenositelné struktury pole vyrovnávací paměť pevné nesmí být zařazeno správně do nativního kódu.
