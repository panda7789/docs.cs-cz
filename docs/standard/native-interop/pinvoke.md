---
title: Vyvolání platformy (nespravovaného)
description: Zjistěte, jak volat nativní funkce prostřednictvím P/Invoke v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c6dcfdb9543abceb688fee2d73c242f1742ab27d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582551"
---
# <a name="platform-invoke-pinvoke"></a>Vyvolání platformy (nespravovaného)

P/Invoke je technologie, která umožňuje přístup ke strukturám, zpětná volání a funkce v nespravovaných knihoven ze spravovaného kódu. Většina nespravovaného rozhraní API je součástí dva obory názvů: `System` a `System.Runtime.InteropServices`. Tyto dva obory názvů pomocí získáte všechny nástroje k popisu způsobu komunikovat s nativní součást.

Začněme od Nejběžnějším příkladem a, který je volání nespravovaných funkcí ve spravovaném kódu. Pojďme zobrazit okno se zprávou z aplikace příkazového řádku:

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

V předchozím příkladu je jednoduché, ale je předvést, co je potřeba k volání nespravovaných funkcí ze spravovaného kódu. Projděme si příklad:

* Řádek #1 ukazuje na pomocí příkazu pro `System.Runtime.InteropServices` obor názvů, který obsahuje všechny položky, které jsou potřeba.
* Představuje řádek #7 `DllImport` atribut. Tento atribut je zásadní, protože říká modul runtime, že by se měly načíst nespravovaná knihovna DLL. Předaný řetězec je knihovna DLL je náš cíl funkce v. Kromě toho určuje, které [znaková sada](./charset.md) pro zařazování řetězce. A konečně, určuje, že tato funkce volá [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) a modul runtime sbíral tento chybový kód tak, že uživatel může načíst ho přes <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.
* Řádek #8 je jádrem pracovní P/Invoke. Definuje spravované metody, která má **přesně stejnou signaturu** jako nespravovaný. Deklarace má nové klíčové slovo, můžete si všimnete, `extern`, který dává pokyn modulu runtime to je externí metoda a že při vyvolání jeho, modul runtime měl nacházet v knihovny DLL určené v `DllImport` atribut.

Zbývající část v příkladu je právě volání metody, stejně jako jiné spravované metody.

Vzorek je podobný pro macOS. Název knihovny `DllImport` atributů je potřeba změnit, protože s macOS má jiné schéma názvů dynamické knihovny. Následující ukázkový používá `getpid(2)` funkce, která se získat ID procesu aplikace a vytiskne ji do konzoly:

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

Je to podobné v Linuxu. Název funkce je stejný, protože `getpid(2)` je standard [POSIX](https://en.wikipedia.org/wiki/POSIX) volání systému.

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a>Volání spravovaného kódu z nespravovaného kódu

Modul runtime povoluje komunikaci probíhaly v obou směrech, umožňuje volat zpět do spravovaného kódu z nativní funkce pomocí ukazatelů na funkce. Je nejbližší věcí s ukazatelem na funkci ve spravovaném kódu **delegovat**, takže je to, co se používá k povolení zpětných volání z nativního kódu do spravovaného kódu.

Způsob, jak používat tuto funkci je podobný jako spravované do nativní popsaných výše. Pro dané zpětné volání definovat delegáta, která odpovídá podpisu a předat ho do externí metody. Modul runtime se postará o všechno ostatní.

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

Před provede v příkladu, je vhodné zkontrolovat podpisy nespravované funkce, které potřebujete pro práci s. Funkce, která se dá zavolat, aby vypisovat výčet všech oken má následující podpis: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

První parametr je zpětné volání. Uvedené zpětné volání má následující podpis: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Nyní projděme si příklad:

* Řádek #9 v příkladu definuje delegáta, který se shoduje se signaturou zpětného volání z nespravovaného kódu. Všimněte si, jak jsou reprezentovány typy LPARAM a HWND pomocí `IntPtr` ve spravovaném kódu.
* Zavést řádky #13 a #14 `EnumWindows` funkce z knihovny user32.dll.
* Řádky #17 20 implementaci delegáta. Tento jednoduchý příklad my chceme jenom výstupní popisovač do konzoly.
* Nakonec v řádku #24 externí metoda je volána a předaný delegátovi.

Níže jsou uvedeny příklady operačních systémů Linux a macOS. Pro ně používáme `ftw` funkce, která lze nalézt v `libc`, knihovna C. Tato funkce slouží k procházení hierarchie adresáře a bere ukazatel na funkci jako jeden ze svých parametrů. Uvedení funkce má následující podpis: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

macOS příklad používá stejnou funkci, a jediným rozdílem je, že argument `DllImport` atribut, protože udržuje macOS `libc` na jiném místě.

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

I v předchozích příkladech záviset na parametrech a v obou případech jsou uvedeny parametry, jako spravované typy. Modul runtime dělá "správné věci" a zpracuje do své ekvivalenty na druhé straně. Seznamte se s typy, jak jsou zařazeny do nativního kódu na naší stránce [typu zařazování](type-marshaling.md).

## <a name="more-resources"></a>Další materiály

- [PInvoke.net wiki](https://www.pinvoke.net/) vynikající Wiki s informacemi o společné rozhraní API Windows a postupu při jejich volání.
- [P/Invoke v C++vyhodnocovací](/cpp/dotnet/native-and-dotnet-interoperability)
- [Dokumentace mono na P/Invoke](https://www.mono-project.com/docs/advanced/pinvoke/)
