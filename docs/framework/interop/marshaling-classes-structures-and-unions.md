---
title: Zařazování tříd, struktur a sjednocení
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc7141bb8fce5d5e1c2420a48d6081fa89aa0d53
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-classes-structures-and-unions"></a>Zařazování tříd, struktur a sjednocení
Třídy a struktury jsou podobné v rozhraní .NET Framework. Mají obě můžete polí, vlastnosti a události. Může mít také statické a nestatické metody. Jeden pozoruhodný rozdíl je, že jsou typy hodnot struktury a třídy jsou odkazové typy.  
  
 Následující tabulka uvádí možnosti zařazování tříd, struktur a sjednocení; Popisuje jejich použití; odkaz na odpovídající platformy vyvolání ukázka.  
  
|Typ|Popis|Ukázka|  
|----------|-----------------|------------|  
|Třída hodnotou.|Jako parametr v nebo na více systémů, jako spravované případě předá třídu se členy celé číslo.|SysTime – ukázka|  
|Struktura hodnotou.|Předá struktury jako parametry.|Ukázka struktury|  
|Struktura odkazem.|Předá struktury jako vstupně -výstupní parametry.|OSInfo – ukázka|  
|Struktura s vnořené struktury (průmětu).|Předá třídu, která reprezentuje strukturu s vnořené struktury v nespravované funkce. Struktura je průmětu do jeden velký struktury v spravované prototypu.|FindFile – ukázka|  
|Struktura pomocí ukazatele do jiné struktury.|Předá strukturu, která obsahuje ukazatel na druhý struktura jako člena.|Ukázka struktur|  
|Pole struktur s celými čísly hodnotou.|Předá pole struktury, které obsahují jenom celá čísla jako parametr v nebo na více systémů. Členy pole lze změnit.|Ukázka polí|  
|Pole struktur s celá čísla a řetězce odkazem.|Předá pole struktury, které obsahují celá čísla a řetězce jako parametr typu Out. Volaná funkce přidělí paměť pro pole.|OutArrayOfStructs – ukázka|  
|Sjednocení s typy hodnot.|Předá sjednocení s typy hodnot (celé číslo a dvojitou).|sjednocení – ukázka|  
|Sjednocení s smíšený typy.|Předá sjednocení s smíšený typy (celé číslo a řetězec).|sjednocení – ukázka|  
|Hodnoty Null ve struktuře.|Předá odkaz s hodnotou null (**nic** v jazyce Visual Basic) namísto odkaz na typ hodnoty.|HandleRef – ukázka|  
  
## <a name="structures-sample"></a>Ukázka struktury  
 Tento příklad ukazuje, jak předat strukturu, která odkazuje na druhý struktura, předejte strukturu s vložené struktury a předat struktura s vloženého pole.  
  
 Ukázka struktury používá následující nespravované funkce s jejich původní deklarace funkce:  
  
-   **TestStructInStruct** exportovaný z PinvokeLib.dll.  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   **TestStructInStruct3** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   **TestArrayInStruct** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementace pro výše uvedených funkcí a čtyři struktury: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, a **MYARRAYSTRUCT**. Tyto struktury obsahovat tyto prvky:  
  
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
  
 Spravovaný `MyPerson`, `MyPerson2`, `MyPerson3`, a `MyArrayStruct` struktury mít následující vlastnosti:  
  
-   `MyPerson` obsahuje pouze členové řetězec. [CharSet](specifying-a-character-set.md) pole nastaví řetězce formátu ANSI při nespravované funkci byl předán.  
  
-   `MyPerson2` obsahuje **IntPtr** k `MyPerson` struktura. **IntPtr** typ nahradí původní ukazatel na strukturu nespravované, protože aplikace rozhraní .NET Framework ukazatele nepoužívejte, pokud kód je označen **unsafe**.  
  
-   `MyPerson3` obsahuje `MyPerson` jako vložené struktury. Struktura vložených v rámci jiné struktury můžete vyrovnány tím, že umístíte elementy vložené struktury přímo do hlavní struktury nebo je možné ho nechat jako vložené struktury, jak se provádí v této ukázce.  
  
-   `MyArrayStruct` obsahuje pole celých čísel. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> hodnotu výčtu **ByValArray**, který slouží k označení počet prvků v poli.  
  
 Pro všechny struktury v této ukázce <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut se používá k zajištění, že členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.  
  
 `LibWrap` Třída obsahuje spravovaných prototypy pro `TestStructInStruct`, `TestStructInStruct3`, a `TestArrayInStruct` volá metody `App` třídy. Každý prototypu deklaruje jeden parametr, následujícím způsobem:  
  
-   `TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako jeho parametr.  
  
-   `TestStructInStruct3` deklaruje typ `MyPerson3` jako jeho parametr a předá parametr hodnotou.  
  
-   `TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako jeho parametr.  
  
 Struktury jako argumenty pro metody jsou předanou hodnotu, pokud parametr obsahuje **ref** (**ByRef** v jazyce Visual Basic) – klíčové slovo. Například `TestStructInStruct` metoda předá odkaz (hodnota adresy) na objekt typu `MyPerson2` na nespravovaný kód. K manipulaci s strukturu, `MyPerson2` odkazuje na ukázku vytvoří zadaná velikost vyrovnávací paměti a vrátí jeho adresy tím, že zkombinujete <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody. V dalším kroku ukázku zkopíruje obsah struktury spravovaných do nespravovaných vyrovnávací paměti. Nakonec ukázce se používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metoda zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metoda uvolnit nespravované bloku paměti.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile – ukázka  
 Tento příklad znázorňuje, jak předat strukturu, která obsahuje strukturu, druhý, vložené do nespravované funkce. Také ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pevnou délkou pole v rámci strukturu deklarovat. V této ukázce jsou elementy vložené struktury přidat pro nadřazenou strukturu. Ukázka vložené struktury, která se nesloučí, najdete v části [ukázka struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100)).  
  
 Ukázka FindFile používá následující nespravované funkce, zobrazí se jeho původní funkce deklaraci:  
  
-   **FindFirstFile** exportovaný z Kernel32.dll.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 Původní struktura předaný funkci obsahuje následující prvky:  
  
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
  
 V této ukázce `FindData` třída obsahuje odpovídající datových členů pro každý prvek původní struktury a vložené struktury. Místo dvou původní znak vyrovnávací paměti nahradí třída řetězce. **MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, maticových pevnou délkou znak, který se zobrazí v rámci nespravované struktury.  
  
 `LibWrap` Třída obsahuje spravované prototyp `FindFirstFile` metodu, která předá `FindData` třída jako parametr. Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributů, protože jsou třídy, které jsou odkazové typy, předat jako parametry ve výchozím nastavení.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>sjednocení – ukázka  
 Tento příklad znázorňuje, jak předat struktury obsahující pouze typy hodnot a struktury obsahující řetězec a typ hodnoty jako parametry do nespravované funkce byl očekáván sjednocení. Sjednocení představuje umístění paměti, které může být sdílen dvěma nebo více proměnných.  
  
 Ukázka sjednocení funkce následující nespravované, zobrazí se jeho původní funkce deklaraci:  
  
-   **TestUnion** exportovaný z PinvokeLib.dll.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementaci pro funkci výše uvedených a dvě sjednocení **MYUNION** a **MYUNION2**. Sjednocení obsahovat tyto prvky:  
  
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
  
 Ve spravovaném kódu sjednocení definovány jako struktury. `MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a datový typ double. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Nastavený atribut pro řízení přesné pozice každého datového člena. <xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut poskytuje fyzické umístění polí v rámci nespravované reprezentace spojení. Všimněte si, že oba členové mají stejné hodnoty posunutí tak členy můžete definovat stejnou část paměti.  
  
 `MyUnion2_1` a `MyUnion2_2` obsahovat řetězec a hodnota typu (integer) v uvedeném pořadí. Ve spravovaném kódu nejsou povolené typy hodnot a typy odkazu překrytí. Tato ukázka používá metodu přetížení povolit volající pro oba typy při volání nespravovaného stejné funkce. Rozložení `MyUnion2_1` explicitní a má hodnotu přesné posunutí. Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení nejsou povoleny pro odkazové typy. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, maticových pevnou délkou znak, který se zobrazí v rámci reprezentace nespravovaná sjednocení.  
  
 `LibWrap` Třída obsahuje prototypy pro `TestUnion` a `TestUnion2` metody. `TestUnion2` je přetížena deklarovat `MyUnion2_1` nebo `MyUnion2_2` jako parametry.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime – ukázka  
 Tento příklad znázorňuje, jak předat ukazatel na třídu k nespravované funkci, která očekává ukazatel na strukturu.  
  
 Ukázka SysTime používá následující nespravované funkce, zobrazí se jeho původní funkce deklaraci:  
  
-   **GetSystemTime** exportovaný z Kernel32.dll.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 Původní struktura předaný funkci obsahuje následující prvky:  
  
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
  
 V této ukázce `SystemTime` třída obsahuje prvky původní struktura reprezentován jako členové třídy. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Je nastavena na hodnotu zabezpečit, aby členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.  
  
 `LibWrap` Třída obsahuje spravované prototyp `GetSystemTime` metodu, která předá `SystemTime` třída jako ve vstupně -výstupnímu parametru ve výchozím nastavení. Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributů, protože jsou třídy, které jsou odkazové typy, předat jako parametry ve výchozím nastavení. Pro volající získat výsledky tyto [směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100)) musí být explicitně použity. `App` Vytvoří novou instanci třídy `SystemTime` třídy a přistupuje k jeho datová pole.  
  
### <a name="code-samples"></a>Ukázky kódu  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs – ukázka  
 Tento příklad ukazuje, jak předat pole struktury, které obsahuje celá čísla a řetězce jako výstupní parametry do nespravované funkce.  
  
 Tento příklad ukazuje způsob volání nativní funkce pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nezabezpečený kód.  
  
 Tato ukázka používá funkce obálky a vyvolá platformy definovaný v [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)), také zadaný ve zdrojových souborech. Použije `TestOutArrayOfStructs` funkce a `MYSTRSTRUCT2` struktury. Struktura obsahuje následující prvky:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` Třída obsahuje objekt řetězec znaků ANSI. <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formát ANSI. `MyUnsafeStruct`, je strukturou obsahující <xref:System.IntPtr> typu místo řetězec.  
  
 `LibWrap` Třída obsahuje přetížené `TestOutArrayOfStructs` metoda prototypu. Pokud metoda deklaruje ukazatel jako parametr, třída by měl být označen s `unsafe` – klíčové slovo. Protože [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nelze použít nezabezpečený kód, přetížené metody, unsafe modifikátor a `MyUnsafeStruct` struktura nejsou potřeba.  
  
 `App` Třída implementuje `UsingMarshaling` metodu, která provádí všechny úlohy, které jsou nutné předat pole. Toto pole je označené jako `out` (`ByRef` v jazyce Visual Basic) předává – klíčové slovo označíte, že data z volaný volajícího. Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu.  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> Chcete-li uvolnit paměť vyhrazené pro řetězce ve struktuře.  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> k uvolnění paměti vyhrazené pro pole.  
  
 Jak už jsme zmínili, C# umožňuje nezabezpečený kód a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] neexistuje. V jazyce C# ukázce `UsingUnsafePointer` je alternativní metoda pro implementace, která používá ukazatele místo <xref:System.Runtime.InteropServices.Marshal> třída předat zpět obsahující pole `MyUnsafeStruct` struktura.  
  
### <a name="declaring-prototypes"></a>Deklarace prototypů  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>Volání funkcí  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>Viz také  
 [Zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md)  
 [Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Zařazování řetězců](marshaling-strings.md)  
 [Zařazování pole typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
