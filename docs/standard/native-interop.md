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
# <a name="native-interoperability"></a><span data-ttu-id="f6df6-103">Nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f6df6-103">Native Interoperability</span></span>

<span data-ttu-id="f6df6-104">V tomto dokumentu jsme se bude věnovat trochu hlouběji všechny tři způsoby, jak dělat "nativní interoperabilita", které jsou k dispozici pomocí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f6df6-104">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="f6df6-105">Existuje několik důvodů, proč byste to provádět volání do nativního kódu:</span><span class="sxs-lookup"><span data-stu-id="f6df6-105">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="f6df6-106">Operační systémy jsou dostupné velký objem rozhraní API, která se nenachází v knihoven spravovaných tříd.</span><span class="sxs-lookup"><span data-stu-id="f6df6-106">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="f6df6-107">Typickým příkladem pro tento bude přístup k hardwaru nebo operačního systému funkce správy.</span><span class="sxs-lookup"><span data-stu-id="f6df6-107">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="f6df6-108">Komunikace s ostatními součástmi, které máte, nebo můžete vytvořit instrukce ABI ve stylu jazyka C (nativní instrukce ABI).</span><span class="sxs-lookup"><span data-stu-id="f6df6-108">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="f6df6-109">Toto téma zahrnuje, například kód v Javě, který je zveřejněný prostřednictvím [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohla vést nativní součásti.</span><span class="sxs-lookup"><span data-stu-id="f6df6-109">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="f6df6-110">Na Windows většina softwaru, který se nainstaluje, jako je například sada Microsoft Office registruje komponenty modelu COM, které představují své programy a vývojářům umožňuje automatizovat je nebo je používat.</span><span class="sxs-lookup"><span data-stu-id="f6df6-110">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="f6df6-111">Tento proces také vyžaduje nativní interoperabilita.</span><span class="sxs-lookup"><span data-stu-id="f6df6-111">This also requires native interoperability.</span></span>

<span data-ttu-id="f6df6-112">Samozřejmě seznamu výše nepopisuje všechny potenciální situace a scénáře, ve kterých by vývojář chcete/typu/potřeba rozhraní s nativními komponentami.</span><span class="sxs-lookup"><span data-stu-id="f6df6-112">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="f6df6-113">Knihovna tříd rozhraní .NET, například používá interoperabilitu nativní podporu k implementaci přiměřený počet jejích rozhraní API, jako je podpora konzoly a manipulaci s, přístupu k systému souborů a další.</span><span class="sxs-lookup"><span data-stu-id="f6df6-113">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="f6df6-114">Je ale důležité si uvědomit, že je možnost, by měl jednu potřebovat.</span><span class="sxs-lookup"><span data-stu-id="f6df6-114">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="f6df6-115">Většina příkladů v tomto dokumentu se zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS).</span><span class="sxs-lookup"><span data-stu-id="f6df6-115">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="f6df6-116">Ale příklady krátký a příkladů, stačí jeden vzorek je zobrazit, který používá rozšíření (to znamená "knihovny dll" pro knihovny) a názvy souborů Windows.</span><span class="sxs-lookup"><span data-stu-id="f6df6-116">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="f6df6-117">To neznamená, že tyto funkce nejsou dostupné v systému Linux nebo macOS, bylo provedeno pouze pro usnadnění práce saké.</span><span class="sxs-lookup"><span data-stu-id="f6df6-117">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="f6df6-118">Vyvolání platformy (nespravovaného)</span><span class="sxs-lookup"><span data-stu-id="f6df6-118">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="f6df6-119">P/Invoke je technologie, která umožňuje přístup ke strukturám, zpětná volání a funkce v nespravovaných knihoven ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-119">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="f6df6-120">Většina nespravovaného rozhraní API je součástí dva obory názvů: `System` a `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="f6df6-120">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="f6df6-121">Pomocí těchto dva obory názvů vám umožní přístup pro atributy, které popisují, jak chcete komunikovat s nativní součást.</span><span class="sxs-lookup"><span data-stu-id="f6df6-121">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="f6df6-122">Začněme od Nejběžnějším příkladem a, který je volání nespravovaných funkcí ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-122">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="f6df6-123">Pojďme zobrazit okno se zprávou z aplikace příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="f6df6-123">Let’s show a message box from a command-line application:</span></span>

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

<span data-ttu-id="f6df6-124">V příkladu výše je docela jednoduché, ale předvést toho, co je potřeba k vyvolání nespravovaných funkcí ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-124">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="f6df6-125">Projděme si příklad:</span><span class="sxs-lookup"><span data-stu-id="f6df6-125">Let’s step through the example:</span></span>

*   <span data-ttu-id="f6df6-126">Řádek #1 ukazuje na pomocí příkazu pro `System.Runtime.InteropServices` což je obor názvů, který obsahuje všechny položky, potřebujeme.</span><span class="sxs-lookup"><span data-stu-id="f6df6-126">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="f6df6-127">Představuje řádek #5 `DllImport` atribut.</span><span class="sxs-lookup"><span data-stu-id="f6df6-127">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="f6df6-128">Tento atribut je zásadní, protože říká modul runtime, že by se měly načíst nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="f6df6-128">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="f6df6-129">To je knihovna DLL, do které bychom chtěli vyvolat.</span><span class="sxs-lookup"><span data-stu-id="f6df6-129">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="f6df6-130">Řádek #6 je jádrem pracovní P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="f6df6-130">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="f6df6-131">Definuje spravované metody, která má **přesně stejnou signaturu** jako nespravovaný.</span><span class="sxs-lookup"><span data-stu-id="f6df6-131">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="f6df6-132">Deklarace má nové klíčové slovo, můžete si všimnete, `extern`, který dává pokyn modulu runtime to je externí metoda a že při vyvolání jeho, modul runtime měl nacházet v knihovny DLL určené v `DllImport` atribut.</span><span class="sxs-lookup"><span data-stu-id="f6df6-132">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="f6df6-133">Zbývající část v příkladu je právě volání metody, stejně jako jiné spravované metody.</span><span class="sxs-lookup"><span data-stu-id="f6df6-133">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="f6df6-134">Vzorek je podobný pro macOS.</span><span class="sxs-lookup"><span data-stu-id="f6df6-134">The sample is similar for macOS.</span></span> <span data-ttu-id="f6df6-135">Jednou z věcí, kterou je potřeba změnit je, samozřejmě, název knihovny `DllImport` atribut, protože s macOS má jiné schéma názvů dynamické knihovny.</span><span class="sxs-lookup"><span data-stu-id="f6df6-135">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="f6df6-136">Ukázkové níže využívá `getpid(2)` funkce, která se získat ID procesu aplikace a vytiskne na konzolu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-136">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

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

<span data-ttu-id="f6df6-137">Je to podobné v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-137">It is also similar on Linux.</span></span> <span data-ttu-id="f6df6-138">Název funkce je stejný, protože `getpid(2)` je standard [POSIX](https://en.wikipedia.org/wiki/POSIX) volání systému.</span><span class="sxs-lookup"><span data-stu-id="f6df6-138">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

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

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="f6df6-139">Volání spravovaného kódu z nespravovaného kódu</span><span class="sxs-lookup"><span data-stu-id="f6df6-139">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="f6df6-140">Samozřejmě modul runtime povoluje komunikaci tok oba způsoby, které umožňuje provádět volání do spravovaného artefakty z nativní funkce pomocí deklarátoru ukazatele na funkce.</span><span class="sxs-lookup"><span data-stu-id="f6df6-140">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="f6df6-141">Je nejbližší věcí s ukazatelem na funkci ve spravovaném kódu **delegovat**, takže je to, co se používá k povolení zpětných volání z nativního kódu do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-141">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="f6df6-142">Způsob, jak používat tuto funkci je podobný spravované do nativní výše popsaný proces.</span><span class="sxs-lookup"><span data-stu-id="f6df6-142">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="f6df6-143">Pro dané zpětné volání definovat delegáta, která odpovídá podpisu a předat ho do externí metody.</span><span class="sxs-lookup"><span data-stu-id="f6df6-143">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="f6df6-144">Modul runtime se postará o všechno ostatní.</span><span class="sxs-lookup"><span data-stu-id="f6df6-144">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="f6df6-145">Než vás provedeme procesem náš příklad, je vhodné si projít podpisy nespravované funkce potřebné pro práci s.</span><span class="sxs-lookup"><span data-stu-id="f6df6-145">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="f6df6-146">Funkce, které chceme volat k vytvoření výčtu všech oken má následující podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f6df6-146">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="f6df6-147">První parametr je zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="f6df6-147">The first parameter is a callback.</span></span> <span data-ttu-id="f6df6-148">Uvedené zpětné volání má následující podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f6df6-148">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="f6df6-149">S myslete na to projděme si příklad:</span><span class="sxs-lookup"><span data-stu-id="f6df6-149">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="f6df6-150">Řádek #8 v příkladu definuje delegáta, který odpovídá signatuře zpětného volání z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-150">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="f6df6-151">Všimněte si, jak jsou reprezentovány typy LPARAM a HWND pomocí `IntPtr` ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-151">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="f6df6-152">Zavést řádky #10 a #11 `EnumWindows` funkce z knihovny user32.dll.</span><span class="sxs-lookup"><span data-stu-id="f6df6-152">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="f6df6-153">Řádky #13 16 implementaci delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6df6-153">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="f6df6-154">Tento jednoduchý příklad my chceme jenom výstupní popisovač do konzoly.</span><span class="sxs-lookup"><span data-stu-id="f6df6-154">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="f6df6-155">Na řádku #19 jsme nakonec volání externí metody a předat delegáta.</span><span class="sxs-lookup"><span data-stu-id="f6df6-155">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="f6df6-156">Níže jsou uvedeny příklady operačních systémů Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="f6df6-156">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="f6df6-157">Pro ně používáme `ftw` funkce, která lze nalézt v `libc`, knihovna C.</span><span class="sxs-lookup"><span data-stu-id="f6df6-157">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="f6df6-158">Tato funkce slouží k procházení hierarchie adresáře a bere ukazatel na funkci jako jeden ze svých parametrů.</span><span class="sxs-lookup"><span data-stu-id="f6df6-158">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="f6df6-159">Uvedení funkce má následující podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="f6df6-159">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="f6df6-160">macOS příklad používá stejnou funkci, a jediným rozdílem je, že argument `DllImport` atribut, protože udržuje macOS `libc` na jiném místě.</span><span class="sxs-lookup"><span data-stu-id="f6df6-160">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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

<span data-ttu-id="f6df6-161">Z výše uvedených příkladech záviset na parametrech a v obou případech jsou uvedeny parametry, jako spravované typy.</span><span class="sxs-lookup"><span data-stu-id="f6df6-161">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="f6df6-162">Modul runtime dělá "správné věci" a zpracuje do své ekvivalenty na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="f6df6-162">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="f6df6-163">Protože tento proces je skutečně potřeba psaní nativního kódu spolupráce kvality, Pojďme se podívat, co se stane, když modul runtime _marshals_ typy.</span><span class="sxs-lookup"><span data-stu-id="f6df6-163">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="f6df6-164">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="f6df6-164">Type marshalling</span></span>

<span data-ttu-id="f6df6-165">**Zařazování** je proces transformace typy, když je budou potřebovat překračují hranice spravované do nativní a naopak.</span><span class="sxs-lookup"><span data-stu-id="f6df6-165">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="f6df6-166">Z důvodu zařazování je potřeba je, protože se liší typy v spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="f6df6-166">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="f6df6-167">Ve spravovaném kódu, například můžete mít `String`, zatímco nespravované světě mohou být řetězce Unicode ("širokých"), kódování Unicode, zakončený hodnotou null, ASCII, atd. Ve výchozím nastavení, se pokusí že správně dělají na základě deklarace P/Invoke subsystému [výchozí chování](../../docs/framework/interop/default-marshaling-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="f6df6-167">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the right thing based on the [default behavior](../../docs/framework/interop/default-marshaling-behavior.md).</span></span> <span data-ttu-id="f6df6-168">Pro tyto situace, kdy potřebujete další ovládací prvek, ale můžete použít [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) atribut k určení, co je očekávaný typ v nespravované oblasti.</span><span class="sxs-lookup"><span data-stu-id="f6df6-168">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="f6df6-169">Například pokud se mají řetězec, který má být odeslán jako ANSI řetězec zakončený hodnotou null, může Uděláme to takto:</span><span class="sxs-lookup"><span data-stu-id="f6df6-169">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="f6df6-170">Zařazování tříd a struktur</span><span class="sxs-lookup"><span data-stu-id="f6df6-170">Marshalling classes and structs</span></span>

<span data-ttu-id="f6df6-171">Dalším aspektem typu zařazování je jak předat strukturu pro nespravované metody.</span><span class="sxs-lookup"><span data-stu-id="f6df6-171">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="f6df6-172">Například některé metody nespravovaného vyžadují strukturu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f6df6-172">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="f6df6-173">V těchto případech potřebujeme vytvořit odpovídající struktury nebo třídy součástí spravované mohli používat jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f6df6-173">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="f6df6-174">Však stačí definování třídy není dostatečně, musíme také dáte pokyn, aby zařazování způsob mapování polí ve třídě do nespravované struktury.</span><span class="sxs-lookup"><span data-stu-id="f6df6-174">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="f6df6-175">Tady `StructLayout` atribut pochází do hry.</span><span class="sxs-lookup"><span data-stu-id="f6df6-175">This is where the `StructLayout` attribute comes into play.</span></span>

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

<span data-ttu-id="f6df6-176">Výše uvedený příklad ukazuje vypnout jednoduchý příklad volání do `GetSystemTime()` funkce.</span><span class="sxs-lookup"><span data-stu-id="f6df6-176">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="f6df6-177">Zajímavé bit je na řádku 4.</span><span class="sxs-lookup"><span data-stu-id="f6df6-177">The interesting bit is on line 4.</span></span> <span data-ttu-id="f6df6-178">Atribut určuje, že pole třídy musí být mapována postupně do struktury na druhé straně (nespravovaného).</span><span class="sxs-lookup"><span data-stu-id="f6df6-178">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="f6df6-179">To znamená, že názvy polí není důležité, pouze jejich pořadí je důležité, dokud jej potřebuje tak, aby odpovídaly nespravované struktury, vidíte níže:</span><span class="sxs-lookup"><span data-stu-id="f6df6-179">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

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

<span data-ttu-id="f6df6-180">Už jsme viděli v příkladu se systémy Linux a macOS k tomu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-180">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="f6df6-181">Se znovu zobrazí níže.</span><span class="sxs-lookup"><span data-stu-id="f6df6-181">It is shown again below.</span></span>

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

<span data-ttu-id="f6df6-182">`StatClass` Třída reprezentuje strukturu, která je vrácena `stat` volání systému v systémech UNIX.</span><span class="sxs-lookup"><span data-stu-id="f6df6-182">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="f6df6-183">Představuje informace o daném souboru.</span><span class="sxs-lookup"><span data-stu-id="f6df6-183">It represents information about a given file.</span></span> <span data-ttu-id="f6df6-184">Třída výše je reprezentace stat – struktura ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="f6df6-184">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="f6df6-185">Opět pole ve třídě musí být ve stejném pořadí jako nativní – struktura (můžete vyhledat těchto perusing man stránky na vaší oblíbené implementace UNIX) a musí být stejný základní typ.</span><span class="sxs-lookup"><span data-stu-id="f6df6-185">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="f6df6-186">Další materiály</span><span class="sxs-lookup"><span data-stu-id="f6df6-186">More resources</span></span>

*   <span data-ttu-id="f6df6-187">[PInvoke.net wiki](https://www.pinvoke.net/) vynikající Wiki s informacemi o společné rozhraní API systému Win32 a postupu při jejich volání.</span><span class="sxs-lookup"><span data-stu-id="f6df6-187">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="f6df6-188">P/Invoke na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="f6df6-188">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="f6df6-189">Dokumentace mono na P/Invoke</span><span class="sxs-lookup"><span data-stu-id="f6df6-189">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)
