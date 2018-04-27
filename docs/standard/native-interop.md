---
title: Nativní interoperabilita
description: Informace o rozhraní s nativní součásti v rozhraní .NET.
keywords: Rozhraní .NET, .NET core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9b0fa5ebe37e51c45a8a5d8a42ce9b9688cc7c1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="native-interoperability"></a>Nativní interoperabilita

V tomto dokumentu jsme se podrobně chvíli hlubší všechny tři způsoby, jak to "nativní interoperabilita" které jsou k dispozici, pomocí rozhraní .NET.

Existuje několik důvodů, proč byste měli volání do nativního kódu:

*   Operační systémy se dodávají s velkým množstvím rozhraní API, která se nenacházejí v knihovnách spravovanou třídou. Typickým příkladem pro tento bude přístup k hardwaru nebo funkce operačního systému správy.
*   Komunikaci s ostatními součástmi, které máte nebo můžete vytvořit bis stylu jazyka C (nativní bis ). Toto se vztahuje, například Java kód, který je zveřejněný prostřednictvím [Java nativní rozhraní (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jakéhokoli jiného spravované jazyka, který může vytvářet nativní součásti.
*   V systému Windows většina softwaru, který získá nainstalovali, jako je například sada Microsoft Office, zaregistruje komponenty modelu COM, které představují jejich programy a umožňují vývojářům automatizovat je nebo je používat. To také vyžaduje nativní interoperabilita.

Samozřejmě seznamu výše nepopisuje všechny potenciální situace a scénáře, ve kterých vývojář by chcete/jako/potřeba rozhraní s nativní součásti. Knihovna tříd rozhraní .NET, například používá nativní interoperabilita podporu k implementaci úloha dostatečný počet jeho rozhraní API, jako je podpora konzoly a manipulaci, přístupu k systému souborů a dalších. Je ale důležité si uvědomit, že je možnost, by měl jeden ho potřebovat.

> [!NOTE]
> Většina v příkladech v tomto dokumentu zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a systému macOS). Příklady krátký a příkladů je však pouze jeden ukázka uvádějí, která používá rozšíření (tedy "dll" pro knihovny) a názvy souborů systému Windows. To neznamená, že tyto funkce nejsou k dispozici v systému Linux nebo systému macOS, bylo potřeba jenom pro usnadnění práce saké.

## <a name="platform-invoke-pinvoke"></a>Vyvolání platformy (P/Invoke)

P/Invoke je technologie, která vám umožní přistupovat k struktury, zpětná volání a funkce v nespravované knihovny ze spravovaného kódu. Velká část rozhraní API P/Invoke není součástí dva obory názvů: `System` a `System.Runtime.InteropServices`. Pomocí těchto dva obory názvů vám umožní přístup k atributy, které popisují, jak chcete komunikovat s komponentou nativní.

Začněme z nejběžnějších příkladu a který je volání nespravovaných funkcí ve spravovaném kódu. Umožňuje zobrazit okno se zprávou z příkazového řádku aplikace:

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

V předchozím příkladu je poměrně jednoduché, ale zobrazit vypnout co je potřeba k volání nespravovaných funkcí ze spravovaného kódu. Umožňuje procházet v příkladu:

*   Řádek #1 ukazuje použití příkazu pro `System.Runtime.InteropServices` které je obor názvů, který obsahuje všechny položky, potřebujeme.
*   Zavádí řádku #5 `DllImport` atribut. Tento atribut je velmi důležitý, když informuje modul runtime, ho by se měly načíst knihovnu DLL nespravované. Toto je knihovnu DLL, do kterého chceme vyvolání.
*   Řádek #6 je crux P/Invoke práce. Definuje spravované metodu, která má **přesný stejným podpisem** jako nespravované. Deklaraci má nové klíčové slovo, které můžete si všimnete, `extern`, která sděluje modulu runtime to je externí metodu a zda při vyvolání ho, modul runtime by měl zjistit v knihovně DLL zadaný v `DllImport` atribut.

Zbytek v příkladu je právě volání metody, stejně jako jiné spravované metody.

Ukázka je podobné pro systému macOS. Jedna z věcí, které je potřeba změnit je samozřejmě název knihovny v nástroji `DllImport` atribut systému macOS má jiné schéma názvových dynamické knihovny. Ukázka níže používá `getpid(2)` funkci k získání ID procesu aplikace a vytiskněte ke konzole.

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

Je to podobné v systému Linux. Název funkce je stejné, protože `getpid(2)` je standard [POSIX](https://en.wikipedia.org/wiki/POSIX) systémového volání.

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

### <a name="invoking-managed-code-from-unmanaged-code"></a>Vyvolání spravovaného kódu z nespravovaného kódu

Samozřejmě modul runtime umožňuje komunikaci tok obou směrech, které umožňuje provádět volání do spravovaných artefakty z nativní funkce, pomocí ukazatele na funkce. Je nejblíže si ukazatel na funkci ve spravovaném kódu **delegovat**, takže je to, co používá k povolení zpětná volání z nativní kód do spravovaného kódu.

Způsob použití této funkce je podobná spravovat tak, aby nativní proces popsaný výše. Pro danou zpětné volání zadejte delegáta, který odpovídá podpisu a který předání do externího metody. Modul runtime se postará o nic jiného.

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

Před jsme v našem příkladu provede, je vhodné si projít signatur potřebné pro práci s nespravovaným funkcím. Funkce, kterou chcete volat k vytvoření výčtu všech windows má následující podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

První parametr je zpětné volání. Uvedené zpětného volání má následující podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Myslete na to projděme v příkladu:

*   Řádek #8 v příkladu definuje delegáta, který odpovídá podpis zpětného volání z nespravovaného kódu. Všimněte si, jak jsou typy LPARAM a HWND reprezentované pomocí `IntPtr` ve spravovaném kódu.
*   Řádky #10 a #11 zavést `EnumWindows` funkce z knihovny user32.dll.
*   Řádky #13 až 16 implementovat delegát. V tomto příkladu jednoduché my chceme jenom výstup popisovač ke konzole.
*   V řádku #19 jsme nakonec vyvolat metodu externí a předat delegát.

Níže jsou uvedeny příklady Linux a systému macOS. Pro ně, použijeme `ftw` funkce, který se nachází v `libc`, knihovna jazyka C. Tato funkce se používá k procházení adresáře hierarchií a trvá ukazatel na funkci jako jeden z jeho parametrů. Uvedené funkce má následující podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

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

Příklad systému macOS používá stejnou funkci a jediným rozdílem je, že argument `DllImport` atributů, protože udržuje systému macOS `libc` na jiné místo.

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

Obě uvedených příkladech závisí na parametry a v obou případech jsou uvedeny parametry, jako spravované typy. Modul runtime má "správné funkci" a zpracuje tyto na jeho ekvivalenty na druhé straně. Vzhledem k tomu, že tento proces je důležité, psaní kódu pro nativní spolupráce kvality, Podívejme se na co se stane, když modul runtime _marshals_ typy.

## <a name="type-marshalling"></a>Zařazování typů

**Zařazování** je proces transformace typy, když potřebují překročit spravované hranice do nativní a naopak.

Zařazování důvod je potřeba je proto, že typy v kód spravovanými a nespravovanými se liší. Ve spravovaném kódu, například máte `String`, zatímco v nespravované world mohou být řetězce Unicode ("širokou"), kódování Unicode, ukončené hodnotou null, ASCII, atd. Ve výchozím nastavení, se pokusí provést věc vpravo na výchozí chování, které se zobrazí na základě subsystém P/Invoke [MSDN](../../docs/framework/interop/default-marshaling-behavior.md). Pro tyto situace, kdy potřebujete další kontrolu, ale můžete použít `MarshalAs` atribut k určení, co je očekávaný typ na nespravované straně. Například pokud chceme řetězec, který má být odeslán jako ANSI řetězce ukončené hodnotou null, můžeme ho udělat takto:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Zařazování tříd a struktur

Další aspekt zařazování typ je uveden postup předat struktury metodu nespravované. Například některé nespravované metody vyžadovat struktury jako parametr. V těchto případech je potřeba vytvořit odpovídající struktury nebo třída spravované část na světě můžete použít jako parametr. Ale právě definice třídy není dostatečně, musíme také vyzvat zařazování mapování polí ve třídě do nespravovaných struktura. To je, kdy `StructLayout` atribut pochází do play.

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

Výše uvedený příklad ukazuje vypnout jednoduchý příklad volání do `GetSystemTime()` funkce. Zajímavé bit je na řádku 4. Atribut určuje, že pole třídy by měly být namapované postupně k struktura na druhé straně (nespravovaný). To znamená, že se není důležité, názvy polí, jenom jejich pořadí je důležité, protože je tak, aby odpovídaly nespravované struktura, vidíte níže:

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

Už jsme viděli příklad Linux a systému macOS pro tento v předchozím příkladu. Se znovu zobrazí níže.

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

`StatClass` Třída reprezentuje strukturu, která je vrácený `stat` systémového volání v systémech UNIX. Představuje informace o daném souboru. Třída výše je reprezentace stat – struktura ve spravovaném kódu. Znovu pole ve třídě, musí být ve stejném pořadí jako nativní struct (můžete najít tak, že perusing man stránky na implementaci Oblíbené UNIX) a musí být stejného základního typu.

## <a name="more-resources"></a>Další prostředky

*   [PInvoke.net wiki](https://www.pinvoke.net/) vynikající Wiki s informacemi o společné rozhraní Win32 API a jak je volat.
*   [P/Invoke na webu MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [Na P/Invoke mono dokumentace](https://www.mono-project.com/docs/advanced/pinvoke/)
