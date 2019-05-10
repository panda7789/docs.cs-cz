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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb39f6f68d0d36449153ae16eca38a15cb7055de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648627"
---
# <a name="marshaling-classes-structures-and-unions"></a>Zařazování tříd, struktur a sjednocení
Třídy a struktury jsou podobné jako u rozhraní .NET Framework. Můžete mít pole, vlastnosti a události. Můžou také mít statické a nestatické metody. Jeden velký rozdíl je, že struktury jsou typy hodnot a třídy jsou odkazové typy.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; Popisuje jejich použití; a získáte odkaz na odpovídající platformu vyvolání vzorku.  
  
|Type|Popis|Ukázka|  
|----------|-----------------|------------|  
|Třída podle hodnoty.|Předá třída s atributem členů celého čísla jako vstupně-výstupní parametr, jako spravované případ.|SysTime – ukázka|  
|Struktura podle hodnoty.|Předává struktury jako parametry in.|Ukázka struktur|  
|Struktura podle odkazu.|Předává struktury jako vstup a výstup parametry.|OSInfo – ukázka|  
|Struktura s vnořené struktury (plochý).|Předává třídu, která reprezentuje strukturu s vnořené struktury v nespravované funkci. Struktura se sloučí do jednoho velké objemy struktury v spravovaný prototyp.|FindFile – ukázka|  
|Struktura s ukazatelem na jinou strukturu.|Předává strukturu, která obsahuje ukazatel na strukturu druhý jako člena.|Ukázka struktur|  
|Pole struktury s celými čísly podle hodnoty.|Předá pole struktury, které obsahují pouze celá čísla jako vstupně-výstupní parametr. Členy pole lze změnit.|Ukázka polí|  
|Pole struktury s celá čísla a řetězce podle odkazu.|Předá pole struktury, které obsahují řetězce a celá čísla jako parametr Out. Volaná funkce přiděluje paměť pro pole.|OutArrayOfStructs – ukázka|  
|Sjednocení s typy hodnot.|Předá sjednocení s typy hodnot (celé číslo a dvojitá).|sjednocení – ukázka|  
|Sjednocení s smíšené typy.|Předá sjednocení s smíšené typy (celé číslo a řetězec).|sjednocení – ukázka|  
|Hodnoty Null ve struktuře.|Předá odkaz s hodnotou null (**nic** v jazyce Visual Basic) namísto odkazu na typ hodnoty.|HandleRef – ukázka|  
  
## <a name="structures-sample"></a>Ukázka struktur  
 Tento příklad ukazuje, jak předat strukturu, která odkazuje na druhý strukturu, předejte strukturu s vložené struktury a předejte strukturu s vložené pole.  
  
 Ukázka struktur používá následující nespravované funkce zobrazené s původní deklarací funkce:  
  
- **TestStructInStruct** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- **TestStructInStruct3** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- **TestArrayInStruct** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, a **MYARRAYSTRUCT**. Tyto struktury obsahují následující prvky:  
  
```  
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
  
 Spravovanou `MyPerson`, `MyPerson2`, `MyPerson3`, a `MyArrayStruct` struktury mají následující charakteristiky:  
  
- `MyPerson` obsahuje pouze členy řetězec. [CharSet](specifying-a-character-set.md) pole nastaví řetězce formátu ANSI předány nespravované funkci.  
  
- `MyPerson2` obsahuje **IntPtr** k `MyPerson` struktury. **IntPtr** typ nahradí původní ukazatel na nespravované struktury, protože aplikace rozhraní .NET Framework nepoužívejte ukazatele, pokud kód je označen **nebezpečné**.  
  
- `MyPerson3` obsahuje `MyPerson` jako vložené struktury. Struktura vložených v jiné struktuře můžete plochý tak, že prvky vložené struktury přímo do hlavní struktury nebo ji lze ponechat jako vložené struktury, jak je tomu v této ukázce.  
  
- `MyArrayStruct` obsahuje pole celých čísel. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> hodnotu výčtu pro **ByValArray**, který se používá k určení počtu prvků v poli.  
  
 Pro všechny struktury v této ukázce <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributu se použije pro zajištění, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.  
  
 `LibWrap` Třída obsahuje spravované prototypy pro `TestStructInStruct`, `TestStructInStruct3`, a `TestArrayInStruct` volané metody `App` třídy. Každý prototyp deklaruje jediný parametr, následujícím způsobem:  
  
- `TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako svůj parametr.  
  
- `TestStructInStruct3` deklaruje typ `MyPerson3` jako svůj parametr a předá podle hodnoty parametru.  
  
- `TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako svůj parametr.  
  
 Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr obsahuje **ref** (**ByRef** v jazyce Visual Basic) – klíčové slovo. Například `TestStructInStruct` metoda předává odkazem (hodnota adresy) na objekt typu `MyPerson2` nespravovaného kódu. K manipulaci s strukturu, která `MyPerson2` odkazuje na ukázky vytvoří vyrovnávací paměti o zadané velikosti a vrátí jeho adresu tím, že zkombinujete <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody. Dále ukázka zkopíruje obsah spravovaná struktura do nespravované vyrovnávací paměti. Nakonec příklad používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodu zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metodu pro uvolnění nespravovaných blok paměti.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile – ukázka  
 Tato ukázka předvádí, jak předat strukturu, která obsahuje druhý, vložené struktury nespravované funkci. Také ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut, chcete-li deklarovat pole s pevnou délkou v rámci struktury. V této ukázce jsou elementy vložené struktury přidány pro nadřazenou strukturu. Ukázka vložené struktury, která se nesloučí, naleznete v tématu [ukázka struktur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).  
  
 Findfile – Ukázka používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:  
  
- **FindFirstFile** exportovaná ze souboru Kernel32.dll.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 Původní struktura předaná funkci obsahuje následující prvky:  
  
```  
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
  
 V této ukázce `FindData` třída obsahuje odpovídající datový člen pro každý prvek původní struktury a vložené struktury. Místo dvou původní znak vyrovnávacích pamětí nahradí třída řetězce. **MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, znaků pevné délky pole, která se zobrazí v rámci nespravované struktury.  
  
 `LibWrap` Třída obsahuje spravovaný prototyp metody `FindFirstFile` metodu, která předává `FindData` jako parametr předávat třídu. Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, protože třídy, které jsou odkazové typy, jsou předány jako parametry in ve výchozím nastavení.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>sjednocení – ukázka  
 Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující hodnotový typ a řetězec jako parametry pro nespravovaná funkce očekává sjednocení. Sjednocení představuje umístění paměti, které je možné sdílet mezi dvěma nebo více proměnných.  
  
 Ukázka spojení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:  
  
- **TestUnion** exportovaná z knihovny PinvokeLib.dll.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a dvě spojení **MYUNION** a **MYUNION2**. Sjednocení obsahovat následující prvky:  
  
```  
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
  
 Ve spravovaném kódu sjednocení jsou definovány jako struktury. `MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a typ double. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na ovládací prvek přesné pozice každého datového člena. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut obsahuje fyzické umístění pole ve sjednocení nespravované reprezentace. Všimněte si, že oba členy mají stejné hodnoty posunu, aby členové mohli definovat stejnou část paměti.  
  
 `MyUnion2_1` a `MyUnion2_2` obsahovat hodnotu typu (integer) a řetězec, v uvedeném pořadí. Ve spravovaném kódu nejsou povoleny typy hodnot a odkazové typy překrytí. Tato ukázka používá metody přetížení pro povolení volajícím použít oba typy při volání metody stejnou nespravovanou funkci. Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu. Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení se nedá vymezit přes typy odkazů. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, znaků pevné délky pole, která se zobrazí v rámci nespravované reprezentace sjednocení.  
  
 `LibWrap` Třída obsahuje prototypy pro `TestUnion` a `TestUnion2` metody. `TestUnion2` je přetížena pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametry.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime – ukázka  
 Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.  
  
 Systime – Ukázka používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:  
  
- **GetSystemTime** exportovaná ze souboru Kernel32.dll.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 Původní struktura předaná funkci obsahuje následující prvky:  
  
```  
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
  
 V této ukázce `SystemTime` třída obsahuje prvky původní struktury reprezentovaná jako členy třídy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na Ujistěte se, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.  
  
 `LibWrap` Třída obsahuje spravovaný prototyp metody `GetSystemTime` metodu, která předává `SystemTime` třídy jako vstupně -výstupní parametr ve výchozím nastavení. Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, protože třídy, které jsou odkazové typy, jsou předány jako parametry in ve výchozím nastavení. Pro volajícího na příjem výsledků tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) musí být použito explicitně. `App` Vytvoří novou instanci třídy `SystemTime` třídy a přistupuje k jeho datová pole.  
  
### <a name="code-samples"></a>Ukázky kódu  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs – ukázka  
 Tento příklad ukazuje, jak předat pole struktury, která obsahuje celá čísla a řetězce jako výstupní parametry nespravované funkci.  
  
 Tato ukázka předvádí, jak volat nativní funkce pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nezabezpečený kód.  
  
 Tato ukázka používá funkce obálky, a vyvolá platformu podle [knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), k dispozici také ve zdrojových souborech. Používá `TestOutArrayOfStructs` funkce a `MYSTRSTRUCT2` struktury. Struktura obsahuje následující prvky:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Třída obsahuje objekt řetězce znaků ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formátu ANSI. `MyUnsafeStruct`, je struktura obsahující <xref:System.IntPtr> typ namísto řetězce.  
  
 `LibWrap` Třída obsahuje přetížené `TestOutArrayOfStructs` prototyp metody. Metoda deklaruje ukazatel, jako parametr, by měly být třídy označené `unsafe` – klíčové slovo. Protože [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nelze použít nezabezpečený kód, přetěžované metody, modifikátor unsafe a `MyUnsafeStruct` struktura nejsou potřeba.  
  
 `App` Implementuje třída `UsingMarshaling` metodu, která provádí všechny úkoly, které jsou nutné předat pole. Pole je označeno `out` (`ByRef` v jazyce Visual Basic) předá – klíčové slovo k označení tato data z volaný volající. Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:  
  
- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu.  
  
- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> k uvolnění paměti vyhrazená pro řetězce ve struktuře.  
  
- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> k uvolnění paměti vyhrazená pro pole.  
  
 Jak už jsme zmínili, C# umožňuje nezabezpečený kód a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] tak není. V C# ukázce `UsingUnsafePointer` je to alternativní metoda pro implementace, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy předat zpět na pole obsahující `MyUnsafeStruct` struktury.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)
- [Zařazování řetězců](marshaling-strings.md)
- [Zařazování různých typů polí](marshaling-different-types-of-arrays.md)
