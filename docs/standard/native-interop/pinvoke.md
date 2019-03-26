---
title: Vyvolání platformy (nespravovaného)
description: Zjistěte, jak volat nativní funkce prostřednictvím P/Invoke v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 4836096e12f6c3d317daa5da91566ab472053ede
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409234"
---
# <a name="platform-invoke-pinvoke"></a>Vyvolání platformy (nespravovaného)

P/Invoke je technologie, která umožňuje přístup ke strukturám, zpětná volání a funkce v nespravovaných knihoven ze spravovaného kódu. Většina nespravovaného rozhraní API je součástí dva obory názvů: `System` a `System.Runtime.InteropServices`. Tyto dva obory názvů pomocí získáte všechny nástroje k popisu způsobu komunikovat s nativní součást.

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

V předchozím příkladu je jednoduché, ale je předvést, co je potřeba k volání nespravovaných funkcí ze spravovaného kódu. Projděme si příklad:

*   Řádek #1 ukazuje na pomocí příkazu pro `System.Runtime.InteropServices` obor názvů, který obsahuje všechny položky, které jsou potřeba.
*   Představuje řádek #7 `DllImport` atribut. Tento atribut je zásadní, protože říká modul runtime, že by se měly načíst nespravovaná knihovna DLL. Předaný řetězec je knihovna DLL je náš cíl funkce v.
*   Řádek #8 je jádrem pracovní P/Invoke. Definuje spravované metody, která má **přesně stejnou signaturu** jako nespravovaný. Deklarace má nové klíčové slovo, můžete si všimnete, `extern`, který dává pokyn modulu runtime to je externí metoda a že při vyvolání jeho, modul runtime měl nacházet v knihovny DLL určené v `DllImport` atribut.

Zbývající část v příkladu je právě volání metody, stejně jako jiné spravované metody.

Vzorek je podobný pro macOS. Název knihovny `DllImport` atributů je potřeba změnit, protože s macOS má jiné schéma názvů dynamické knihovny. Následující ukázkový používá `getpid(2)` funkce, která se získat ID procesu aplikace a vytiskne ji do konzoly:

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

## <a name="invoking-managed-code-from-unmanaged-code"></a>Volání spravovaného kódu z nespravovaného kódu

Modul runtime povoluje komunikaci probíhaly v obou směrech, umožňuje volat zpět do spravovaného kódu z nativní funkce pomocí ukazatelů na funkce. Je nejbližší věcí s ukazatelem na funkci ve spravovaném kódu **delegovat**, takže je to, co se používá k povolení zpětných volání z nativního kódu do spravovaného kódu.

Způsob, jak používat tuto funkci je podobný jako spravované do nativní popsaných výše. Pro dané zpětné volání definovat delegáta, která odpovídá podpisu a předat ho do externí metody. Modul runtime se postará o všechno ostatní.

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

Před provede v příkladu, je vhodné zkontrolovat podpisy nespravované funkce, které potřebujete pro práci s. Funkce, která se dá zavolat, aby vypisovat výčet všech oken má následující podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

První parametr je zpětné volání. Uvedené zpětné volání má následující podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Nyní projděme si příklad:

*   Řádek #9 v příkladu definuje delegáta, který se shoduje se signaturou zpětného volání z nespravovaného kódu. Všimněte si, jak jsou reprezentovány typy LPARAM a HWND pomocí `IntPtr` ve spravovaném kódu.
*   Zavést řádky #13 a #14 `EnumWindows` funkce z knihovny user32.dll.
*   Řádky #17 20 implementaci delegáta. Tento jednoduchý příklad my chceme jenom výstupní popisovač do konzoly.
*   Nakonec v řádku #24 externí metoda je volána a předaný delegátovi.

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
        // represents that struct in managed code.
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

I v předchozích příkladech záviset na parametrech a v obou případech jsou uvedeny parametry, jako spravované typy. Modul runtime dělá "správné věci" a zpracuje do své ekvivalenty na druhé straně. Další informace o tom, jak jsou typy zařazeno do nativního kódu na naší stránce [typu zařazování](type-marshalling.md).


## <a name="more-resources"></a>Další materiály

*   [PInvoke.net wiki](https://www.pinvoke.net/) vynikající Wiki s informacemi o společné rozhraní API Windows a postupu při jejich volání.
*   [P/Invoke na webu MSDN](/cpp/dotnet/native-and-dotnet-interoperability)
*   [Dokumentace mono na P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
