---
title: Zařazování tříd, struktur a sjednocení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 708ed6a232950cb69796f105f6f198749ed53a24
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200012"
---
# <a name="marshaling-classes-structures-and-unions"></a>Zařazování tříd, struktur a sjednocení

Třídy a struktury jsou podobné v .NET Framework. Oba můžou mít pole, vlastnosti a události. Mohou mít také statické a nestatické metody. Jedním z významných rozdílů je, že struktury jsou typy hodnot a třídy jsou odkazové typy.

V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; popisuje jejich použití. a poskytuje odkaz na odpovídající ukázku vyvolání platformy.

|Typ|Popis|Ukázka|
|----------|-----------------|------------|
|Třída podle hodnoty|Předá třídu s celočíselnými členy jako parametr in/out, jako je například spravovaný případ.|[SysTime – ukázka](#systime-sample)|
|Struktura podle hodnoty.|Předá struktury jako v parametrech.|[Ukázka struktur](#structures-sample)|
|Struktura podle odkazu|Předává struktury jako vstupně-výstupní parametry.|[OSInfo – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|
|Struktura s vnořenými strukturami (ploché).|Předá třídu, která představuje strukturu s vnořenými strukturami v nespravované funkci. Struktura je v rámci spravovaného prototypu Sloučená do jedné velké struktury.|[FindFile – ukázka](#findfile-sample)|
|Struktura s ukazatelem na jinou strukturu.|Předá strukturu, která obsahuje ukazatel na druhou strukturu jako člen.|[Ukázka struktur](#structures-sample)|
|Pole struktur s celými čísly podle hodnoty|Předá pole struktur, které obsahují pouze celá čísla jako vstupně-výstupní parametr. Členy pole lze změnit.|[Ukázka polí](marshaling-different-types-of-arrays.md)|
|Pole struktur s celými čísly a řetězci podle odkazu|Předá pole struktury, které obsahují celá čísla a řetězce jako výstupní parametr. Volaná funkce přiděluje paměť pro pole.|[Ukázka Outarrayofstructs –](#outarrayofstructs-sample)|
|Sjednocení s typy hodnot.|Předá sjednocení s typy hodnot (Integer a Double).|[sjednocení – ukázka](#unions-sample)|
|Sjednocení se smíšenými typy.|Předá sjednocení se smíšenými typy (Integer a String).|[sjednocení – ukázka](#unions-sample)|
|Struktura s rozložením pro konkrétní platformu.|Předá typ s definicemi nativního balení.|[Ukázka platformy](#platform-sample)|
|Hodnoty null ve struktuře.|Předá odkaz s hodnotou null (**Nothing** v Visual Basic) místo odkazu na typ hodnoty.|[HandleRef – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))|

## <a name="structures-sample"></a>Ukázka struktur

Tato ukázka předvádí, jak předat strukturu, která odkazuje na druhou strukturu, předejte strukturu s vloženou strukturou a předejte strukturu vloženému poli.  
  
Ukázka struktury používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:

- **TestStructInStruct** exportovaný z knihovny pinvokelib. dll.

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- **TestStructInStruct3** exportovaný z knihovny pinvokelib. dll.

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- **TestArrayInStruct** exportovaný z knihovny pinvokelib. dll.

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**a **MYARRAYSTRUCT**. Tyto struktury obsahují následující prvky:

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

Struktury spravované `MyPerson`, `MyPerson2`, `MyPerson3`a `MyArrayStruct` mají následující charakteristiky:

- `MyPerson`obsahuje pouze členy řetězce. Pole [CharSet](specifying-a-character-set.md) nastaví řetězce na formát ANSI při předání do nespravované funkce.

- `MyPerson2`obsahuje **IntPtr** ke `MyPerson` struktuře. Typ **IntPtr** nahrazuje původní ukazatel na nespravovanou strukturu, protože .NET Framework aplikace nepoužívají ukazatele, pokud není kód označen jako **nebezpečný**.

- `MyPerson3`obsahuje `MyPerson` jako vloženou strukturu. Strukturu vloženou v jiné struktuře lze sloučit umístěním prvků vložené struktury přímo do hlavní struktury, nebo může být ponechána jako vložená struktura, jak je provedeno v této ukázce.

- `MyArrayStruct`obsahuje pole celých čísel. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu na **ByValArray**, která slouží k označení počtu prvků v poli.

Pro všechny struktury v této ukázce se používá <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, aby bylo zajištěno, že jsou členy uspořádány v paměti postupně, v pořadí, ve kterém jsou uvedeny.

`NativeMethods` Třída obsahuje `TestStructInStruct`spravované prototypy pro, a `TestStructInStruct3` `TestArrayInStruct` metody, které jsou `App` volány třídou. Každý prototyp deklaruje jeden parametr následujícím způsobem:

- `TestStructInStruct`deklaruje odkaz na typ `MyPerson2` jako jeho parametr.

- `TestStructInStruct3`Deklaruje typ `MyPerson3` jako svůj parametr a předá parametr podle hodnoty.

- `TestArrayInStruct`deklaruje odkaz na typ `MyArrayStruct` jako jeho parametr.

Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr neobsahuje klíčové slovo **ref** (**ByRef** in Visual Basic). Například `TestStructInStruct` metoda předává odkaz (hodnota adresy) objektu typu `MyPerson2` na nespravovaný kód. Aby bylo možné manipulovat se strukturou, na kterou `MyPerson2` odkazuje, ukázka vytvoří vyrovnávací paměť zadané velikosti a vrátí její adresu kombinací metod <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> V dalším kroku zkopíruje ukázka obsah spravované struktury do nespravované vyrovnávací paměti. Nakonec ukázka používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodu pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metodu pro uvolnění nespravovaného bloku paměti.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a>Volání funkcí

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a>FindFile – ukázka

Tato ukázka předvádí, jak předat strukturu, která obsahuje druhou, vloženou strukturu do nespravované funkce. Také ukazuje, jak použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k deklaraci pole s pevnou délkou v rámci struktury. V této ukázce jsou vložené prvky struktury přidány do nadřazené struktury. Ukázku vložené struktury, která není shrnuta, naleznete v části [struktury Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).

Ukázka FindFile – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:

- **FindFirstFile** exportovaný z Kernel32. dll.

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

Původní struktura předaná funkci obsahuje následující prvky:

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

V této ukázce `FindData` třída obsahuje odpovídající datový člen pro každý prvek původní struktury a vloženou strukturu. Místo dvou původních vyrovnávacích pamětí znaků třída nahradí řetězce. **MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který slouží k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaných strukturách.

`NativeMethods` Třída obsahuje spravovaný prototyp `FindFirstFile` metody, která předá `FindData` třídu jako parametr. Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> , protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a>Volání funkcí

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a>sjednocení – ukázka

Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující typ hodnoty a řetězec jako parametry nespravované funkce, které očekávají sjednocení. Sjednocení představuje umístění v paměti, které může být sdíleno dvěma nebo více proměnnými.

Vzor sjednocení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:

- **TestUnion** exportovaný z knihovny pinvokelib. dll.

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci dříve uvedené funkce a dvou sjednocení, **MYUNION** a **MYUNION2**. Sjednocení obsahují následující prvky:

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

Ve spravovaném kódu jsou sjednocení definována jako struktury. `MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a typ Double. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na řízení přesné pozice jednotlivých datových členů. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut poskytuje fyzickou pozici polí v rámci nespravované reprezentace sjednocení. Všimněte si, že oba členové mají stejné hodnoty posunutí, takže členové mohou definovat stejnou část paměti.

`MyUnion2_1`a `MyUnion2_2` obsahují hodnotový typ (Integer) a řetězec v uvedeném pořadí. Ve spravovaném kódu se typy hodnot a typy odkazů nepovolují překrývat. Tato ukázka používá přetížení metody, aby volající mohl použít oba typy při volání stejné nespravované funkce. Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu. Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení nejsou povolena s odkazovým typem. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který se používá k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaném vyjádření sjednocení.

`NativeMethods` Třída obsahuje prototypy pro metody `TestUnion` a `TestUnion2` . `TestUnion2`je přetížený pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametry.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a>Volání funkcí

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a>Ukázka platformy

V některých scénářích `struct` se `union` rozložení může lišit v závislosti na cílové platformě. Zvažte například typ, který [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) je definován ve scénáři modelu com:

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

Výše uvedená `struct` deklarace je deklarována s hlavičkou systému Windows, které mají vliv na rozložení paměti daného typu. Pokud je definována ve spravovaném prostředí, tyto podrobnosti o rozložení jsou potřeba ke správné spolupráci s nativním kódem.

Správná spravovaná definice tohoto typu v rámci 32 procesu je:

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

U 64 procesu se velikost *a* posunutí polí liší. Správné rozložení je:

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

Při nesprávném zvážení nativního rozložení ve scénáři spolupráce může dojít k náhodným chybám nebo horším, nesprávným výpočtům.

Ve výchozím nastavení mohou být sestavení .NET spouštěna v 32 a 64 verze modulu runtime .NET. Aplikace musí počkat, než čas spuštění určí, který z předchozích definic se má použít.

Následující fragment kódu ukazuje příklad, jak zvolit mezi 32 a 64 bitů definice v době běhu.

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a>SysTime – ukázka

Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.

Ukázka sysTime – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:

- **GetSystemTime** exportovaný z Kernel32. dll.

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

Původní struktura předaná funkci obsahuje následující prvky:

```cpp
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

V této ukázce `SystemTime` třída obsahuje prvky původní struktury reprezentované jako členy třídy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.

`NativeMethods` Třída obsahuje spravovaný prototyp `GetSystemTime` metody, která ve výchozím nastavení předává `SystemTime` třídu jako vstupně-výstupní parametr. Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> , protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení. Aby volající mohl přijímat výsledky, musí být tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) aplikovány explicitně. `App` Třída vytvoří novou instanci `SystemTime` třídy a přistupuje k jejím datovým polím.

### <a name="code-samples"></a>Ukázky kódů

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs – ukázka

Tento příklad ukazuje, jak předat pole struktur obsahující celá čísla a řetězce jako výstupní parametry nespravované funkci.

Tento příklad ukazuje, jak volat nativní funkci pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nebezpečného kódu.

Tato ukázka používá funkce obálky a vyvolání platformy definované v [knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), které jsou také k dispozici ve zdrojových souborech. Používá `TestOutArrayOfStructs` funkci a `MYSTRSTRUCT2` strukturu. Struktura obsahuje následující prvky:

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

`MyStruct` Třída obsahuje objekt řetězce znaků ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formát ANSI. `MyUnsafeStruct`, je struktura obsahující <xref:System.IntPtr> typ místo řetězce.

`NativeMethods` Třída obsahuje přetíženou metodu `TestOutArrayOfStructs` prototypu. Pokud metoda deklaruje ukazatel jako parametr, třída by měla být označena `unsafe` klíčovým slovem. Vzhledem k tomu, že Visual Basic nemůže použít nezabezpečený kód, přetíženou metodu, nezabezpečený modifikátor a `MyUnsafeStruct` strukturu jsou zbytečné.

`App` Třída implementuje `UsingMarshaling` metodu, která provádí všechny úlohy, které jsou nezbytné k předání pole. Pole je označeno pomocí `out` klíčového`ByRef` slova (v Visual Basic) k označení toho, že data přecházejí z volaného volajícího. Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:

- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu.

- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>uvolnění paměti rezervované pro řetězce ve struktuře.

- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>uvolnění paměti rezervované pro dané pole.

Jak už jsme uvedli, C# umožňuje nezabezpečený kód a Visual Basic ne. V ukázce jazyka C# `UsingUnsafePointer` je alternativou implementace metody, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy k předání pole obsahujícího `MyUnsafeStruct` strukturu.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a>Volání funkcí

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a>Viz také

- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Zařazování řetězců](marshaling-strings.md)
- [Zařazování různých typů polí](marshaling-different-types-of-arrays.md)
