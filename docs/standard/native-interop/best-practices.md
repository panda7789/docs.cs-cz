---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s osvědčenými postupy pro propojení s nativními komponentami v .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 0405fd5aef9d89fc1f47123ed358e6358656d95b
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70923768"
---
# <a name="native-interoperability-best-practices"></a>Nativní osvědčené postupy interoperability

.NET nabízí různé způsoby přizpůsobení nativního kódu interoperability. Tento článek obsahuje pokyny, které tým .NET Microsoftu sleduje pro zajištění nativní interoperability.

## <a name="general-guidance"></a>Obecné pokyny

Pokyny v této části se vztahují na všechny scénáře spolupráce.

- **✔️** použít stejné názvy a velká písmena pro vaše metody a parametry jako nativní metodu, kterou chcete volat.
- **✔️ zvažte** použití stejných názvů a velkých a malých písmen pro konstantní hodnoty.
- **✔️** použít typy .NET, které jsou mapovány nejblíže k nativnímu typu. Například v C#, použijte `uint` , pokud je `unsigned int`nativní typ.
- **✔️** použít `[In]` pouze atributy a `[Out]` , pokud se chování, které požadujete, se liší od výchozího chování.
- **✔️ zvažte** použití <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vašich nativních vyrovnávacích pamětí pole.
- **✔️ zvažte** zabalení deklarací volání nespravovaného kódu ve třídě se stejným názvem a velkými písmeny jako vaše nativní knihovna.
  - Tím umožníte `[DllImport]` , aby atributy C# `nameof` používaly funkci jazyka k předání názvu nativní knihovny a aby se zajistilo, že jste nezadali název nativní knihovny.

## <a name="dllimport-attribute-settings"></a>Nastavení atributu DllImport

| Nastavení | Výchozí | Doporučení | Podrobnosti |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  zachovat výchozí  | Pokud je toto nastavení explicitně nastaveno na hodnotu false, neúspěšné návratové hodnoty HRESULT budou převedeny na výjimky (a návratová hodnota v definici bude jako výsledek null).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | závisí na rozhraní API  | Tuto hodnotu nastavte na true, pokud rozhraní API používá GetLastError, a k získání hodnoty použijte Marshal. GetLastWin32Error. Pokud rozhraní API nastaví podmínku, která říká, že obsahuje chybu, před dalším voláním zajistěte chybu, aby se zabránilo nechtěnému přepsání.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, který se vrátí k `CharSet.Ansi` chování  | Explicitně použít `CharSet.Unicode` nebo `CharSet.Ansi` v případě, že jsou v definici přítomné řetězce nebo znaky | To určuje chování zařazování řetězců a to, `ExactSpelling` co `false`dělá. Všimněte si `CharSet.Ansi` , že ve skutečnosti je UTF8 v systému UNIX. _Většina_ času v systému Windows používá kódování Unicode, zatímco systém UNIX používá UTF8. Další informace najdete v [dokumentaci k charset](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Nastavte tuto hodnotu na true a získejte mírné zvýhodnění výkonu, protože modul runtime nebude hledat alternativní názvy funkcí s příponou "a" nebo "w" v závislosti na hodnotě `CharSet` nastavení ("a `CharSet.Ansi` " pro a "w" pro `CharSet.Unicode`). |

## <a name="string-parameters"></a>Řetězcové parametry

Pokud je znaková sada Unicode nebo je argument explicitně označen jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán pomocí hodnoty (ne `ref` nebo `out`), řetězec bude připnuté a použit přímo pomocí nativního kódu (místo kopírování).

Nezapomeňte označit jako `Charset.Unicode` , `[DllImport]` Pokud explicitně nechcete, aby byly řetězce v kódu ANSI.

**❌** Nepoužívejte `[Out] string` parametry. Řetězcové parametry předávané hodnotou s `[Out]` atributem mohou destabilizovat modul runtime, pokud je řetězec interně řetězec. Další informace o přehlašování řetězců najdete v dokumentaci pro <xref:System.String.Intern%2A?displayProperty=nameWithType>.

**❌ Se vyhnout** `StringBuilder` parametry. `StringBuilder`zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti. V takovém případě může být mimořádně neefektivní. Vyjistěte si Typický scénář volání rozhraní API systému Windows, které přijímá řetězec:

1. Vytvořte SB požadované kapacity (přiděluje spravovanou kapacitu). **{1}**
2. Vyvolat
   1. Přiděluje nativní vyrovnávací paměť. **{2}**  
   2. Zkopíruje obsah, pokud `[In]` _( `StringBuilder` výchozí hodnota parametru)_ .  
   3. Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole `[Out]` **{3}** _(také `StringBuilder`výchozí pro)_ .  
3. `ToString()`přidělí ještě jiné spravované pole. **{4}**

To je *{4}* přidělení pro získání řetězce z nativního kódu. To nejlepší můžete udělat tak, že je znovu použijete v `StringBuilder` jiném volání, ale bude se dál ukládat jenom *1* přidělení. Je mnohem lepší použít a ukládat do mezipaměti znaková vyrovnávací paměť `ArrayPool`– můžete se pak dostat až do přidělení `ToString()` pro při následném volání.

Dalším problémem `StringBuilder` je, že se vždy zkopíruje návratovou vyrovnávací paměť zpět na první hodnotu null. Pokud předaný řetězec není ukončen nebo se jedná o řetězec zakončený hodnotou null, vaše volání nespravovaného volání není správné.

Pokud *použijete* `StringBuilder`, bude jedna poslední gotcha taková, že **kapacita neobsahuje skrytý** znak null, který je vždy zaúčtován v rámci spolupráce. Je běžné, že lidé mají špatný přístup, protože většina rozhraní API má velikost vyrovnávací paměti, *včetně* hodnoty null. To může vést k plýtvání/zbytečným přidělením. Kromě toho tento gotcha brání modulu runtime v optimalizaci `StringBuilder` zařazování pro minimalizaci kopií.

**✔️ zvažte** použití `char[]`s z `ArrayPool`.

Další informace o zařazování řetězců naleznete v tématu [Výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování řetězců](customize-parameter-marshaling.md#customizing-string-parameters).

> __Specifické pro systém Windows__  
> Pro `[Out]` řetězce, které bude CLR `CoTaskMemFree` používat ve výchozím nastavení, pro `SysStringFree` uvolnění řetězců nebo pro řetězce, `UnmanagedType.BSTR`které jsou označeny jako.  
**Pro většinu rozhraní API výstupní vyrovnávací paměť řetězců:**  
> Počet předaných znaků musí obsahovat hodnotu null. Pokud je vrácená hodnota menší než předaný počet znaků, volání bylo úspěšné a hodnota je počet znaků *bez* koncové hodnoty null. V opačném případě je požadovaná velikost vyrovnávací paměti, *včetně* znaku null.  
>
> - Průchod 5, Get 4: Řetězec má délku 4 znaky s koncovým znakem null.
> - Pass in 5, Get 6: Řetězec má délku 5 znaků, pro uložení hodnoty null je zapotřebí vyrovnávací paměť 6 znaků.  
> [Datové typy Windows pro řetězce](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Logické parametry a pole

Logické hodnoty se dají snadno vytvořit. Ve výchozím nastavení je rozhraní `bool` .NET zařazeno do systému Windows `BOOL`, kde je hodnota 4 bajty. Nicméně, a `bool` typy v jazyce C C++ a jsou jedním bajtem. `_Bool` To může vést k tomu, že je možné sledovat chyby jako polovinu, návratová hodnota bude zahozena, což *může pouze změnit* výsledek. Další informace `bool` o zařazování hodnot .NET do jazyka C nebo C++ `bool` typů naleznete v dokumentaci k [přizpůsobení zařazování logických polí](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>Identifikátory GUID

Identifikátory GUID lze použít přímo v signaturách. Mnoho rozhraní API systému `GUID&` Windows přijímá aliasy typů, jako `REFIID`je. Při předání odkazem, mohou být buď předány pomocí `ref` nebo `[MarshalAs(UnmanagedType.LPStruct)]` s atributem.

| GUID | Identifikátor GUID podle odkazu |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**❌** Použijte `[MarshalAs(UnmanagedType.LPStruct)]` pro jiné než `ref` parametry GUID.

## <a name="blittable-types"></a>Typy přenosit

Přenositelné typy jsou typy, které mají stejné reprezentace na úrovni bitů ve spravovaném a nativním kódu. Vzhledem k tomu, že není nutné je převádět do jiného formátu, aby bylo možné je zařadit do a z nativního kódu a jak to zlepšuje výkon, by měly být upřednostňovány.

**Typy přenositeli:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- nevnořená jednorozměrná pole typů s více typy (například `int[]`)
- struktury a třídy s pevným rozložením, které pro pole instancí mají jenom typy přenositelné hodnoty.
  - pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo`[StructLayout(LayoutKind.Explicit)]`
  - struktury jsou `LayoutKind.Sequential` ve výchozím nastavení třídy`LayoutKind.Auto`

**Nenositelný odkaz:**

- `bool`

**NĚKDY přenositelná:**

- `char`, `string`

Když jsou přenositelné typy předány odkazem, jsou místo kopírování do mezilehlé vyrovnávací paměti jednoduše připnuté serializátorem. (Třídy jsou ze své podstaty předány odkazem, struktury jsou předány odkazem `out`při použití s `ref` nebo.)

`char`je přímo v jednorozměrném poli **nebo** , pokud je součástí typu, který obsahuje explicitně označený `[StructLayout]` pomocí. `CharSet = CharSet.Unicode`

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`je chráněná, pokud není obsažena v jiném typu a je předávána jako argument, který je `[MarshalAs(UnmanagedType.LPWStr)]` označen jako `[DllImport]` nebo `CharSet = CharSet.Unicode` má nastaven.

Když se pokusíte vytvořit připnutý `GCHandle`, můžete zjistit, jestli je typ přenositelný. Pokud typ není řetězec nebo se považuje za Nepřenositelný `GCHandle.Alloc` , `ArgumentException`vyvolá výjimku.

**✔️ proveďte** přenositeli struktury, pokud je to možné.

Další informace naleznete v tématu:

- [Přenositelné a nepřenositelné typy](../../framework/interop/blittable-and-non-blittable-types.md)  
- [Zařazování typů](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Udržování spravovaných objektů

`GC.KeepAlive()`zajistí, že objekt zůstane v oboru, dokud nebude dosaženo metody kontroly naživu.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umožňuje zařazování zachovat objekt aktivní po dobu trvání volání nespravovaného objektu. Dá se použít místo `IntPtr` signatury metody. `SafeHandle`efektivně nahrazuje tuto třídu a měla by se používat místo toho.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umožňuje připnutí spravovaného objektu a získání nativního ukazatele na něj. Základní vzor je:  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Připnutí není výchozím nastavením `GCHandle`pro. Druhým hlavním vzorem je předání odkazu spravovanému objektu prostřednictvím nativního kódu a zpět ke spravovanému kódu, obvykle pomocí zpětného volání. Tady je vzor:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Nezapomeňte, že `GCHandle` je nutné explicitně uvolnit, aby nedošlo k nevracení paměti.

## <a name="common-windows-data-types"></a>Běžné datové typy Windows

Tady je seznam datových typů, které se běžně používají v rozhraních API C# systému Windows, a typy, které se mají použít při volání do kódu Windows.

Následující typy mají stejnou velikost v 32 a 64 bitovém systému Windows, bez ohledu na jejich názvy.

| Šířka | Windows          | C (Windows)          | C#       | Jiné                          |
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

Následující typy jsou ukazatele, které následují po šířce platformy. Použijte `IntPtr` / pro ně`UIntPtr` .

| Typy podepsaných ukazatelů ( `IntPtr`použít) | Typy nepodepsaných ukazatelů `UIntPtr`(použít) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Systém Windows `PVOID` , který je v `void*` jazyce C, lze zařadit `IntPtr` jako `UIntPtr`buď nebo, `void*` ale preferovat, pokud je to možné.

[Datové typy Windows](/windows/desktop/WinProg/windows-data-types)

[Rozsahy datových typů](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Struktury

Spravované struktury se vytvoří v zásobníku a neodstraňují se, dokud se metoda nevrátí. Podle definice pak jsou "připnuté" (nebudou přesunuty do GC). Můžete také jednoduše převzít adresu z nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.

Přenositelné struktury jsou mnohem větší, protože je lze jednoduše použít přímo zařazovací vrstvou. Snažte se vytvořit struktury (například Nepoužívejte `bool`). Další informace najdete v části [typy přenosit](#blittable-types) .

*Pokud* je struktura přenositelná, `sizeof()` použijte místo `Marshal.SizeOf<MyStruct>()` pro lepší výkon. Jak je uvedeno výše, můžete ověřit, zda je typ přenositelný, pokus o vytvoření připnutého `GCHandle`. Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` `ArgumentException`vyvolá výjimku.

Ukazatele na struktury v definicích musí být buď předány `ref` , nebo pomocí `unsafe` a. `*`

**✔️** podle tvaru a názvů, které se používají v dokumentaci k oficiální platformě nebo v hlavičce, co nejvíce porovnává se spravovanou strukturou.

**✔️** C# použít`sizeof()` místo`Marshal.SizeOf<MyStruct>()` pro přenositelné struktury ke zvýšení výkonu.

Pole jako `INT_PTR Reserved1[2]` musí být zařazeno do dvou `IntPtr` polí `Reserved1a` a `Reserved1b`. Pokud je nativním polem primitivní typ, můžeme pomocí `fixed` klíčového slova ho zapsat trochu efektivněji. Například `SYSTEM_PROCESS_INFORMATION` vypadá jako v nativní hlavičce:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

V C#nástroji můžeme zapisovat takto:

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

Existuje však několik možná úskalí s pevnými vyrovnávacími pamětmi. Pevné vyrovnávací paměti nepřenositelného typu nebudou správně zařazeny, takže musí být místní pole rozšířeno na více jednotlivých polí. V .NET Framework a .NET Core před 3,0 platí, že pokud je struktura obsahující pevné pole vyrovnávací paměti vnořena do nepřenositelné struktury, pole pevné vyrovnávací paměti se správně nezazařazuje do nativního kódu.
