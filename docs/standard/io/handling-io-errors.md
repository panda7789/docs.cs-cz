---
title: Zpracování vstupně-výstupních chyb v .NET
description: Přečtěte si, jak zpracovávat chyby v/v v .NET. Mapování kódů chyb na výjimky, zpracování výjimek v vstupně-výstupních operacích a zpracování IOException.
ms.date: 08/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45f3951b727d3b615d8384541ff169e8840acab0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599799"
---
# <a name="handling-io-errors-in-net"></a>Zpracování vstupně-výstupních chyb v .NET

Kromě výjimek, které mohou být vyvolány v jakémkoli volání metody (například <xref:System.OutOfMemoryException> při zdůraznění systému nebo v <xref:System.NullReferenceException> důsledku chyby programátora), mohou metody systému souborů .NET vyvolat následující výjimky:

- <xref:System.IO.IOException?displayProperty=nameWithType>, základní třída všech <xref:System.IO> typů výjimek. Je vyvolána pro chyby, jejichž návratové kódy z operačního systému nejsou přímo mapovány na žádný jiný typ výjimky.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, která je vyvolána pro neplatné znaky cesty v .NET Framework a v .NET Core 2,0 a předchozích verzích.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, který je vyvolána pro neplatná dvojtečka v .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, který je vyvolána pro aplikace spuštěné v omezeném vztahu důvěryhodnosti, které nemají potřebná oprávnění pouze pro .NET Framework. (Ve výchozím nastavení je nastavená plná důvěryhodnost .NET Framework.)

## <a name="mapping-error-codes-to-exceptions"></a>Mapování kódů chyb na výjimky

Vzhledem k tomu, že systém souborů je prostředkem operačního systému, vstupně-výstupní metody v rozhraní .NET Core a .NET Framework zabalit volání do základního operačního systému. Pokud dojde k vstupně-výstupní chybě v kódu spuštěném operačním systémem, operační systém vrátí informace o chybě metodě .NET I/O. Metoda pak přeloží informace o chybě, obvykle ve formě kódu chyby, do typu výjimky .NET. Ve většině případů to dělá přímo v překladu kódu chyby na odpovídající typ výjimky; neprovádí žádné speciální mapování chyb na základě kontextu volání metody.

Například v operačním systému Windows, volání metody, které vrací chybový kód `ERROR_FILE_NOT_FOUND` (nebo 0x02), mapuje na a <xref:System.IO.FileNotFoundException> , a chybový kód `ERROR_PATH_NOT_FOUND` (nebo 0x03) se mapuje na <xref:System.IO.DirectoryNotFoundException> .

Přesné podmínky, za kterých operační systém vrátí konkrétní kódy chyb, ale často nedokumentují nebo špatně zdokumentují. Výsledkem je, že může dojít k neočekávaným výjimkám. Například vzhledem k tomu, že pracujete s adresářem namísto souboru, očekáváte, že zadáním neplatné cesty adresáře pro <xref:System.IO.DirectoryInfo.%23ctor%2A> konstruktor vyvolá <xref:System.IO.DirectoryNotFoundException> . Může však také vyvolat výjimku <xref:System.IO.FileNotFoundException> .

## <a name="exception-handling-in-io-operations"></a>Zpracování výjimek v vstupně-výstupních operacích

Vzhledem k tomu, že se jedná o závislé na operačním systému, může být výsledkem identické podmínky výjimky (například Chyba adresář nebyl nalezen v našem příkladu). To znamená, že při volání rozhraní API v/v by měl být váš kód připraven zpracovat většinu nebo všechny tyto výjimky, jak je znázorněno v následující tabulce:

| Typ výjimky | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Ano | Ano |
| <xref:System.IO.FileNotFoundException> | Ano | Ano |
| <xref:System.IO.DirectoryNotFoundException> | Ano | Ano |
| <xref:System.IO.DriveNotFoundException?> | Ano | Ano |
| <xref:System.IO.PathTooLongException> | Ano | Ano |
| <xref:System.OperationCanceledException> | Ano | Ano |
| <xref:System.UnauthorizedAccessException> | Ano | Ano |
| <xref:System.ArgumentException> | .NET Core 2,0 a starší| Yes |
| <xref:System.NotSupportedException> | Ne | Yes |
| <xref:System.Security.SecurityException> | Ne | Jenom omezená důvěra |

## <a name="handling-ioexception"></a>Zpracování IOException

Jako základní třída pro výjimky v <xref:System.IO> oboru názvů <xref:System.IO.IOException> je také vyvolána pro jakýkoliv kód chyby, který není namapován na předdefinovaný typ výjimky. To znamená, že může být vyvolána jakoukoli operací I/O.

> [!IMPORTANT]
> Vzhledem k tomu <xref:System.IO.IOException> , že je základní třídou dalších typů výjimek v <xref:System.IO> oboru názvů, měli byste zpracovat v `catch` bloku po zpracování dalších výjimek souvisejících s vstupem/výstupem.

Kromě toho, počínaje rozhraním .NET Core 2,1, ověřuje správnost cesty (například pro zajištění, že nejsou k dispozici neplatné znaky v cestě) a modul runtime vyvolá výjimku namapovanou z kódu chyby operačního systému, nikoli z vlastního ověřovacího kódu. Nejpravděpodobnější výjimka, která je vyvolána v tomto případě je <xref:System.IO.IOException> , i když jakýkoli jiný typ výjimky může být vyvolán také.

Všimněte si, že v kódu zpracování výjimek byste měli vždy zpracovat <xref:System.IO.IOException> Poslední. V opačném případě, protože se jedná o základní třídu všech ostatních výjimek v/v, nebudou vyhodnoceny bloky catch odvozených tříd.

V případě nástroje <xref:System.IO.IOException> můžete získat další informace o chybě z vlastnosti [IOException. HRESULT](xref:System.Exception.HResult) . Chcete-li převést hodnotu HResult na kód chyby Win32, provedete horní 16 bitů hodnoty 32. V následující tabulce jsou uvedeny kódy chyb, které mohou být zabaleny do <xref:System.IO.IOException> .

| HResult | Trvalé | Popis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Chybí název souboru, nebo je soubor nebo adresář používán. |
| ERROR_FILE_EXISTS | 80 | Soubor již existuje. |
| ERROR_INVALID_PARAMETER | 87 | Argument dodaný metodě je neplatný. |
| ERROR_ALREADY_EXISTS | 183 | Soubor nebo adresář již existuje. |

Můžete je zpracovat pomocí `When` klauzule v příkazu catch, jak ukazuje následující příklad.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Viz také

- [Zpracování a vyvolávání výjimek v rozhraní .NET](../exceptions/index.md)
- [Zpracování výjimek (Task Parallel Library)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Osvědčené postupy pro výjimky](../exceptions/best-practices-for-exceptions.md)
- [Používání specifických výjimek v bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
