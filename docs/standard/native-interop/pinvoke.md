---
title: Vyvolání platformy (volání nespravovaného objektu)
description: Naučte se volat nativní funkce prostřednictvím volání nespravovaného kódu v .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cda738a173cbe61cf49f79ceef78c533a5a879d9
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106788"
---
# <a name="platform-invoke-pinvoke"></a>Vyvolání platformy (volání nespravovaného objektu)

Volání nespravovaného kódu je technologie, která umožňuje přístup ke strukturám, zpětným voláním a funkcím v nespravovaných knihovnách ze spravovaného kódu. Většina rozhraní API pro volání nespravovaného systému je obsažena ve `System` dvou `System.Runtime.InteropServices`oborech názvů: a. Pomocí těchto dvou oborů názvů získáte nástroje pro popis toho, jak chcete komunikovat s nativní součástí.

Pojďme začít z nejběžnějšího příkladu a volat nespravované funkce ve spravovaném kódu. Pojďme zobrazit okno se zprávou z aplikace příkazového řádku:

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

Předchozí příklad je jednoduchý, ale ukazuje, co je potřeba k vyvolání nespravovaných funkcí ze spravovaného kódu. Podíváme se na příklad:

- Řádková #1 zobrazuje příkaz using pro `System.Runtime.InteropServices` obor názvů, který obsahuje všechny potřebné položky.
- Řádek #7 zavádí `DllImport` atribut. Tento atribut je rozhodující, protože říká modulu runtime, že by měl načíst nespravovanou knihovnu DLL. Předaný řetězec je naším cílovou funkcí knihovny DLL. Kromě toho určuje, která [znaková sada](./charset.md) se má použít pro zařazování řetězců. Nakonec určuje, že tato funkce volá [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) a že má modul runtime zachytit kód chyby, aby ho uživatel mohl načíst prostřednictvím <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.
- Řádková #8 je Crux práce P/Invoke. Definuje spravovanou metodu, která má **přesně stejný podpis** jako nespravovaný. Deklarace má nové klíčové slovo, které si můžete všimnout, `extern`a který oznamuje modulu runtime, že se jedná o externí metodu a že když ji vyvoláte, modul runtime ji by měl najít v knihovně `DllImport` DLL určené v atributu.

Zbytek příkladu je pouze volání metody, stejně jako u jakékoli jiné spravované metody.

Ukázka je podobná pro macOS. Název knihovny v `DllImport` atributu musí být změněn, protože MacOS má jiné schéma pojmenování dynamických knihoven. Následující příklad používá `getpid(2)` funkci k získání ID procesu aplikace a jejím tisku do konzoly:

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

Je to také podobné na Linux. Název funkce je stejný, protože `getpid(2)` se jedná o standardní systémové volání [POSIX](https://en.wikipedia.org/wiki/POSIX) .

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a>Vyvolání spravovaného kódu z nespravovaného kódu

Modul runtime umožňuje komunikaci s tokem v obou směrech, takže můžete volat zpět do spravovaného kódu z nativních funkcí pomocí ukazatelů na funkce. Nejbližší odkaz na ukazatel na funkci ve spravovaném kódu je **delegát**, takže to je to, co se používá k povolení zpětných volání z nativního kódu do spravovaného kódu.

Způsob použití této funkce je podobný jako dříve popsaný proces spravovaný k nativnímu procesu. Pro dané zpětné volání definujete delegáta, který odpovídá podpisu a předává ho do externí metody. Modul runtime se postará o všechno ostatní.

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

Než projdete příklad, je dobré zkontrolovat signatury nespravovaných funkcí, se kterými potřebujete pracovat. Funkce, která se má volat pro zobrazení výčtu všech oken, má následující signaturu:`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

První parametr je zpětné volání. Uvedené zpětné volání má následující signaturu:`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Teď projdeme příkladem:

- Řádek #9 v příkladu definuje delegáta, který odpovídá podpisu zpětného volání z nespravovaného kódu. Všimněte si, jak jsou typy lParam a HWND reprezentovány pomocí `IntPtr` spravovaného kódu.
- Řádky #13 a #14 zavádějí `EnumWindows` funkci z knihovny User32. dll.
- Řádky #17-20 implementujte delegáta. V tomto jednoduchém příkladu chceme pouze výstup tohoto popisovače do konzoly.
- Nakonec na řádku #24 je externí metoda volána a předána delegátovi.

Příklady pro Linux a macOS jsou uvedené níže. Pro tyto `ftw` funkce používáme funkci, kterou lze najít v `libc`knihovně jazyka C. Tato funkce se používá k procházení hierarchií adresářů a přebírá ukazatel na funkci jako jeden z jeho parametrů. Tato funkce má následující signaturu: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

MacOS příklad používá stejnou funkci a jediným rozdílem je argument `DllImport` atributu, protože MacOS uchovává `libc` na jiném místě.

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

Oba předchozí příklady závisí na parametrech a v obou případech jsou parametry zadány jako spravované typy. Modul runtime provádí "správnou věc" a zpracovává je na druhé straně. Přečtěte si informace o tom, jak jsou typy zařazeny do nativního kódu na naší stránce při [zařazování typů](type-marshaling.md).

## <a name="more-resources"></a>Další materiály

- [PInvoke.NET wiki](https://www.pinvoke.net/) skvělý wikiweb s informacemi o běžných rozhraních API pro Windows a o tom, jak je volat.
- [P/Invoke v C++/CLI](/cpp/dotnet/native-and-dotnet-interoperability)
- [Dokumentace mono pro volání nespravovaného volání](https://www.mono-project.com/docs/advanced/pinvoke/)
