---
title: Nativní interoperabilita
description: Zjistěte, jak spolupracovat s nativními komponentami v rozhraní .NET.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 2f427eb5d8f41f730d4263425e268213db92236d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143179"
---
# <a name="native-interoperability"></a>Nativní interoperabilita

V tomto dokumentu jsme se bude věnovat trochu hlouběji všechny tři způsoby, jak dělat "nativní interoperabilita", které jsou k dispozici pomocí rozhraní .NET.

Existuje několik důvodů, proč byste to provádět volání do nativního kódu:

*   Operační systémy jsou dostupné velký objem rozhraní API, která se nenachází v knihoven spravovaných tříd. Typickým příkladem pro tento bude přístup k hardwaru nebo operačního systému funkce správy.
*   Komunikace s ostatními součástmi, které máte, nebo můžete vytvořit instrukce ABI ve stylu jazyka C (nativní instrukce ABI). Toto téma zahrnuje, například kód v Javě, který je zveřejněný prostřednictvím [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohla vést nativní součásti.
*   Na Windows většina softwaru, který se nainstaluje, jako je například sada Microsoft Office registruje komponenty modelu COM, které představují své programy a vývojářům umožňuje automatizovat je nebo je používat. Tento proces také vyžaduje nativní interoperabilita.

Samozřejmě seznamu výše nepopisuje všechny potenciální situace a scénáře, ve kterých by vývojář chcete/typu/potřeba rozhraní s nativními komponentami. Knihovna tříd rozhraní .NET, například používá interoperabilitu nativní podporu k implementaci přiměřený počet jejích rozhraní API, jako je podpora konzoly a manipulaci s, přístupu k systému souborů a další. Je ale důležité si uvědomit, že je možnost, by měl jednu potřebovat.

> [!NOTE]
> Většina příkladů v tomto dokumentu se zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS). Ale příklady krátký a příkladů, stačí jeden vzorek je zobrazit, který používá rozšíření (to znamená "knihovny dll" pro knihovny) a názvy souborů Windows. To neznamená, že tyto funkce nejsou dostupné v systému Linux nebo macOS, bylo provedeno pouze pro usnadnění práce saké.

## <a name="platform-invoke-pinvoke"></a>Vyvolání platformy (nespravovaného)

P/Invoke je technologie, která umožňuje přístup ke strukturám, zpětná volání a funkce v nespravovaných knihoven ze spravovaného kódu. Většina nespravovaného rozhraní API je součástí dva obory názvů: `System` a `System.Runtime.InteropServices`. Pomocí těchto dva obory názvů vám umožní přístup pro atributy, které popisují, jak chcete komunikovat s nativní součást.

Začněme od Nejběžnějším příkladem a, který je volání nespravovaných funkcí ve spravovaném kódu. Pojďme zobrazit okno se zprávou z aplikace příkazového řádku:

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

V příkladu výše je docela jednoduché, ale předvést toho, co je potřeba k vyvolání nespravovaných funkcí ze spravovaného kódu. Projděme si příklad:

*   Řádek #1 ukazuje na pomocí příkazu pro `System.Runtime.InteropServices` což je obor názvů, který obsahuje všechny položky, potřebujeme.
*   Představuje řádek #5 `DllImport` atribut. Tento atribut je zásadní, protože říká modul runtime, že by se měly načíst nespravovaná knihovna DLL. To je knihovna DLL, do které bychom chtěli vyvolat.
*   Řádek #6 je jádrem pracovní P/Invoke. Definuje spravované metody, která má **přesně stejnou signaturu** jako nespravovaný. Deklarace má nové klíčové slovo, můžete si všimnete, `extern`, který dává pokyn modulu runtime to je externí metoda a že při vyvolání jeho, modul runtime měl nacházet v knihovny DLL určené v `DllImport` atribut.

Zbývající část v příkladu je právě volání metody, stejně jako jiné spravované metody.

Vzorek je podobný pro macOS. Jednou z věcí, kterou je potřeba změnit je, samozřejmě, název knihovny `DllImport` atribut, protože s macOS má jiné schéma názvů dynamické knihovny. Ukázkové níže využívá `getpid(2)` funkce, která se získat ID procesu aplikace a vytiskne na konzolu.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

Je to podobné v Linuxu. Název funkce je stejný, protože `getpid(2)` je standard [POSIX](https://en.wikipedia.org/wiki/POSIX) volání systému.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a>Volání spravovaného kódu z nespravovaného kódu

Samozřejmě modul runtime povoluje komunikaci tok oba způsoby, které umožňuje provádět volání do spravovaného artefakty z nativní funkce pomocí deklarátoru ukazatele na funkce. Je nejbližší věcí s ukazatelem na funkci ve spravovaném kódu **delegovat**, takže je to, co se používá k povolení zpětných volání z nativního kódu do spravovaného kódu.

Způsob, jak používat tuto funkci je podobný spravované do nativní výše popsaný proces. Pro dané zpětné volání definovat delegáta, která odpovídá podpisu a předat ho do externí metody. Modul runtime se postará o všechno ostatní.

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

Než vás provedeme procesem náš příklad, je vhodné si projít podpisy nespravované funkce potřebné pro práci s. Funkce, které chceme volat k vytvoření výčtu všech oken má následující podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

První parametr je zpětné volání. Uvedené zpětné volání má následující podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

S myslete na to projděme si příklad:

*   Řádek #8 v příkladu definuje delegáta, který odpovídá signatuře zpětného volání z nespravovaného kódu. Všimněte si, jak jsou reprezentovány typy LPARAM a HWND pomocí `IntPtr` ve spravovaném kódu.
*   Zavést řádky #10 a #11 `EnumWindows` funkce z knihovny user32.dll.
*   Řádky #13 16 implementaci delegáta. Tento jednoduchý příklad my chceme jenom výstupní popisovač do konzoly.
*   Na řádku #19 jsme nakonec volání externí metody a předat delegáta.

Níže jsou uvedeny příklady operačních systémů Linux a macOS. Pro ně používáme `ftw` funkce, která lze nalézt v `libc`, knihovna C. Tato funkce slouží k procházení hierarchie adresáře a bere ukazatel na funkci jako jeden ze svých parametrů. Uvedení funkce má následující podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

macOS příklad používá stejnou funkci, a jediným rozdílem je, že argument `DllImport` atribut, protože udržuje macOS `libc` na jiném místě.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

Z výše uvedených příkladech záviset na parametrech a v obou případech jsou uvedeny parametry, jako spravované typy. Modul runtime dělá "správné věci" a zpracuje do své ekvivalenty na druhé straně. Protože tento proces je skutečně potřeba psaní nativního kódu spolupráce kvality, Pojďme se podívat, co se stane, když modul runtime _marshals_ typy.

## <a name="type-marshalling"></a>Zařazování typů

**Zařazování** je proces transformace typy, když je budou potřebovat překračují hranice spravované do nativní a naopak.

Z důvodu zařazování je potřeba je, protože se liší typy v spravovaným a nespravovaným kódem. Ve spravovaném kódu, například můžete mít `String`, zatímco nespravované světě mohou být řetězce Unicode ("širokých"), kódování Unicode, zakončený hodnotou null, ASCII, atd. Ve výchozím nastavení, se pokusí že správně dělají na základě deklarace P/Invoke subsystému [výchozí chování](../../docs/framework/interop/default-marshaling-behavior.md). Pro tyto situace, kdy potřebujete další ovládací prvek, ale můžete použít [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) atribut k určení, co je očekávaný typ v nespravované oblasti. Například pokud se mají řetězec, který má být odeslán jako ANSI řetězec zakončený hodnotou null, může Uděláme to takto:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Zařazování tříd a struktur

Dalším aspektem typu zařazování je jak předat strukturu pro nespravované metody. Například některé metody nespravovaného vyžadují strukturu jako parametr. V těchto případech potřebujeme vytvořit odpovídající struktury nebo třídy součástí spravované mohli používat jako parametr. Však stačí definování třídy není dostatečně, musíme také dáte pokyn, aby zařazování způsob mapování polí ve třídě do nespravované struktury. Tady `StructLayout` atribut pochází do hry.

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

Výše uvedený příklad ukazuje vypnout jednoduchý příklad volání do `GetSystemTime()` funkce. Zajímavé bit je na řádku 4. Atribut určuje, že pole třídy musí být mapována postupně do struktury na druhé straně (nespravovaného). To znamená, že názvy polí není důležité, pouze jejich pořadí je důležité, dokud jej potřebuje tak, aby odpovídaly nespravované struktury, vidíte níže:

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

Už jsme viděli v příkladu se systémy Linux a macOS k tomu v předchozím příkladu. Se znovu zobrazí níže.

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

`StatClass` Třída reprezentuje strukturu, která je vrácena `stat` volání systému v systémech UNIX. Představuje informace o daném souboru. Třída výše je reprezentace stat – struktura ve spravovaném kódu. Opět pole ve třídě musí být ve stejném pořadí jako nativní – struktura (můžete vyhledat těchto perusing man stránky na vaší oblíbené implementace UNIX) a musí být stejný základní typ.

## <a name="more-resources"></a>Další materiály

*   [PInvoke.net wiki](https://www.pinvoke.net/) vynikající Wiki s informacemi o společné rozhraní API systému Win32 a postupu při jejich volání.
*   [P/Invoke na webu MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Dokumentace mono na P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
