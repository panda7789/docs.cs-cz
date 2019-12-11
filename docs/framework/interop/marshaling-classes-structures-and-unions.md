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
ms.openlocfilehash: d761d8ed7488e99f29d4844d061867915a624b96
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960014"
---
# <a name="marshaling-classes-structures-and-unions"></a>Zařazování tříd, struktur a sjednocení

Třídy a struktury jsou podobné v .NET Framework. Oba můžou mít pole, vlastnosti a události. Mohou mít také statické a nestatické metody. Jedním z významných rozdílů je, že struktury jsou typy hodnot a třídy jsou odkazové typy.

V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; popisuje jejich použití. a poskytuje odkaz na odpovídající ukázku vyvolání platformy.

|Type|Popis|Ukázka|
|----------|-----------------|------------|
|Třída podle hodnoty|Předá třídu s celočíselnými členy jako parametr in/out, jako je například spravovaný případ.|[Ukázka sysTime –](#systime-sample)|
|Struktura podle hodnoty.|Předá struktury jako v parametrech.|[Ukázka struktur](#structures-sample)|
|Struktura podle odkazu|Předává struktury jako vstupně-výstupní parametry.|[Ukázka OSINFO –](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|
|Struktura s vnořenými strukturami (ploché).|Předá třídu, která představuje strukturu s vnořenými strukturami v nespravované funkci. Struktura je v rámci spravovaného prototypu Sloučená do jedné velké struktury.|[Ukázka FindFile –](#findfile-sample)|
|Struktura s ukazatelem na jinou strukturu.|Předá strukturu, která obsahuje ukazatel na druhou strukturu jako člen.|[Ukázka struktur](#structures-sample)|
|Pole struktur s celými čísly podle hodnoty|Předá pole struktur, které obsahují pouze celá čísla jako vstupně-výstupní parametr. Členy pole lze změnit.|[Ukázka polí](marshaling-different-types-of-arrays.md)|
|Pole struktur s celými čísly a řetězci podle odkazu|Předá pole struktury, které obsahují celá čísla a řetězce jako výstupní parametr. Volaná funkce přiděluje paměť pro pole.|[Ukázka Outarrayofstructs –](#outarrayofstructs-sample)|
|Sjednocení s typy hodnot.|Předá sjednocení s typy hodnot (Integer a Double).|[Sjednocení – ukázka](#unions-sample)|
|Sjednocení se smíšenými typy.|Předá sjednocení se smíšenými typy (Integer a String).|[Sjednocení – ukázka](#unions-sample)|
|Hodnoty null ve struktuře.|Předá odkaz s hodnotou null (**Nothing** v Visual Basic) místo odkazu na typ hodnoty.|[Ukázka HandleRef –](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))|

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

Spravované `MyPerson`, `MyPerson2`, `MyPerson3`a struktury `MyArrayStruct` mají následující charakteristiky:

- `MyPerson` obsahuje pouze řetězcové členy. Pole [CharSet](specifying-a-character-set.md) nastaví řetězce na formát ANSI při předání do nespravované funkce.

- `MyPerson2` obsahuje **IntPtr** ke struktuře `MyPerson`. Typ **IntPtr** nahrazuje původní ukazatel na nespravovanou strukturu, protože .NET Framework aplikace nepoužívají ukazatele, pokud není kód označen jako **nebezpečný**.

- `MyPerson3` obsahuje `MyPerson` jako vloženou strukturu. Strukturu vloženou v jiné struktuře lze sloučit umístěním prvků vložené struktury přímo do hlavní struktury, nebo může být ponechána jako vložená struktura, jak je provedeno v této ukázce.

- `MyArrayStruct` obsahuje pole celých čísel. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> nastaví hodnotu výčtu <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValArray**, která slouží k označení počtu prvků v poli.

Pro všechny struktury v této ukázce je použit atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou uvedeny.

Třída `NativeMethods` obsahuje spravované prototypy pro `TestStructInStruct`, `TestStructInStruct3`a metody `TestArrayInStruct`, které jsou volány `App` třídou. Každý prototyp deklaruje jeden parametr následujícím způsobem:

- `TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako svůj parametr.

- `TestStructInStruct3` deklaruje typ `MyPerson3` jako svůj parametr a předá parametr podle hodnoty.

- `TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako svůj parametr.

Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr neobsahuje klíčové slovo **ref** (**ByRef** in Visual Basic). Například metoda `TestStructInStruct` předává odkaz (hodnotu adresy) objektu typu `MyPerson2` nespravovanému kódu. Aby bylo možné manipulovat se strukturou, na kterou `MyPerson2` odkazuje, ukázka vytvoří vyrovnávací paměť zadané velikosti a vrátí její adresu kombinováním metod <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>. V dalším kroku zkopíruje ukázka obsah spravované struktury do nespravované vyrovnávací paměti. Nakonec ukázka používá metodu <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> k zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu a metoda <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> pro uvolnění nespravovaného bloku paměti.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a>Funkce volání

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a>FindFile – ukázka

Tato ukázka předvádí, jak předat strukturu, která obsahuje druhou, vloženou strukturu do nespravované funkce. Také ukazuje, jak použít atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> k deklaraci pole s pevnou délkou v rámci struktury. V této ukázce jsou vložené prvky struktury přidány do nadřazené struktury. Ukázku vložené struktury, která není shrnuta, naleznete v části [struktury Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).

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

V této ukázce třída `FindData` obsahuje odpovídající datový člen pro každý prvek původní struktury a vloženou strukturu. Místo dvou původních vyrovnávacích pamětí znaků třída nahradí řetězce. **MarshalAsAttribute** nastaví výčet <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValTStr**, který slouží k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaných strukturách.

Třída `NativeMethods` obsahuje spravovaný prototyp metody `FindFirstFile`, která předá třídu `FindData` jako parametr. Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute>, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a>Funkce volání

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

Ve spravovaném kódu jsou sjednocení definována jako struktury. Struktura `MyUnion` obsahuje dva typy hodnot jako členy: celé číslo a typ Double. Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven na kontrolu nad přesným umístěním každého datového člena. Atribut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> poskytuje fyzickou pozici polí v rámci nespravované reprezentace sjednocení. Všimněte si, že oba členové mají stejné hodnoty posunutí, takže členové mohou definovat stejnou část paměti.

`MyUnion2_1` a `MyUnion2_2` obsahují hodnotový typ (Integer) a řetězec v uvedeném pořadí. Ve spravovaném kódu se typy hodnot a typy odkazů nepovolují překrývat. Tato ukázka používá přetížení metody, aby volající mohl použít oba typy při volání stejné nespravované funkce. Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu. Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože pro typy odkazů nejsou povolena explicitní rozložení. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> nastaví výčet <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValTStr**, který se používá k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaném vyjádření sjednocení.

Třída `NativeMethods` obsahuje prototypy pro metody `TestUnion` a `TestUnion2`. `TestUnion2` je přetížena pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametrů.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a>Funkce volání

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

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

V této ukázce třída `SystemTime` obsahuje prvky původní struktury reprezentované jako členy třídy. Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven, aby bylo zajištěno, že členové jsou uspořádáni v paměti sekvenčně v pořadí, ve kterém jsou uvedeni.

Třída `NativeMethods` obsahuje spravovaný prototyp metody `GetSystemTime`, která ve výchozím nastavení předává třídu `SystemTime` jako vstupně-výstupní parametr. Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute>, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení. Aby volající mohl přijímat výsledky, musí být tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) aplikovány explicitně. Třída `App` vytvoří novou instanci třídy `SystemTime` a přistupuje k jejím datovým polím.

### <a name="code-samples"></a>Ukázky kódu

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs – ukázka

Tento příklad ukazuje, jak předat pole struktur obsahující celá čísla a řetězce jako výstupní parametry nespravované funkci.

Tento příklad ukazuje, jak volat nativní funkci pomocí třídy <xref:System.Runtime.InteropServices.Marshal> a pomocí nebezpečného kódu.

Tato ukázka používá funkce obálky a vyvolání platformy definované v [knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), které jsou také k dispozici ve zdrojových souborech. Používá funkci `TestOutArrayOfStructs` a strukturu `MYSTRSTRUCT2`. Struktura obsahuje následující prvky:

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

Třída `MyStruct` obsahuje objekt řetězce znaků ANSI. Pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> určuje formát ANSI. `MyUnsafeStruct`je struktura obsahující <xref:System.IntPtr> typu místo řetězce.

Třída `NativeMethods` obsahuje přetíženou metodu `TestOutArrayOfStructs` prototypu. Pokud metoda deklaruje ukazatel jako parametr, třída by měla být označena klíčovým slovem `unsafe`. Vzhledem k tomu, že Visual Basic nemůže použít nezabezpečený kód, přetíženou metodu, nezabezpečený modifikátor a `MyUnsafeStruct` strukturu jsou zbytečné.

Třída `App` implementuje `UsingMarshaling` metodu, která provádí všechny úlohy nezbytné k předání pole. Pole je označeno pomocí klíčového slova `out` (`ByRef` in Visual Basic) k označení toho, že data přecházejí ze volaného volajícího. Implementace používá následující metody třídy <xref:System.Runtime.InteropServices.Marshal>:

- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazovat data z nespravované vyrovnávací paměti do spravovaného objektu.

- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> uvolnění paměti rezervované pro řetězce ve struktuře.

- pro uvolnění paměti rezervované pro pole <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>.

Jak už jsme uvedli C# , umožňuje nezabezpečený kód a Visual Basic ne. V C# ukázce je `UsingUnsafePointer` alternativou implementace metody, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy k předání pole obsahujícího strukturu `MyUnsafeStruct`.

### <a name="declaring-prototypes"></a>Deklarace prototypů

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a>Funkce volání

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a>Viz také:

- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Zařazování řetězců](marshaling-strings.md)
- [Zařazování různých typů polí](marshaling-different-types-of-arrays.md)
