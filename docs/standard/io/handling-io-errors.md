---
title: Zpracování vstupně-v.I chyb v rozhraní .NET
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
ms.openlocfilehash: c592039b3b12eedcfceda45c2f54403a8e04b5d5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242670"
---
# <a name="handling-io-errors-in-net"></a>Zpracování vstupně-v.I chyb v rozhraní .NET

Kromě výjimek, které mohou být vyvolány v libovolném <xref:System.OutOfMemoryException> volání metody (například když je systém namáhaný nebo <xref:System.NullReferenceException> z důvodu chyby programátora), mohou metody systému souborů .NET vyvolat následující výjimky:

- <xref:System.IO.IOException?displayProperty=nameWithType>, základní třída <xref:System.IO> všech typů výjimek. Je vyvolána pro chyby, jejichž návratové kódy z operačního systému nejsou přímo mapovat na jiný typ výjimky.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, který je vyvolán pro neplatné znaky cesty v rozhraní .NET Framework a na rozhraní .NET Core 2.0 a předchozích verzích.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, který je vyvolán pro neplatné dvojtečky v rozhraní .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, který je vyvolán pro aplikace spuštěné v omezeném vztahu důvěryhodnosti, které nemají potřebná oprávnění pouze v rozhraní .NET Framework. (Úplný vztah důvěryhodnosti je výchozí v rozhraní .NET Framework.)

## <a name="mapping-error-codes-to-exceptions"></a>Mapování kódů chyb na výjimky

Vzhledem k tomu, že systém souborů je prostředek operačního systému, vstupně-no metody v rozhraní .NET Core a .NET Framework zalamování volání základního operačního systému. Dojde-li k chybě vstupně-out v kódu spuštěného operačním systémem, operační systém vrátí informace o chybě metodě V/V.NET. Metoda pak převede informace o chybě, obvykle ve formě kódu chyby, do typu výjimky .NET. Ve většině případů to provádí přímým překladem kódu chyby do odpovídajícího typu výjimky; neprovádí žádné zvláštní mapování chyby na základě kontextu volání metody.

Například v operačním systému Windows se volání metody, `ERROR_FILE_NOT_FOUND` které vrací kód chyby <xref:System.IO.FileNotFoundException>(nebo 0x02) mapuje na a a kód chyby `ERROR_PATH_NOT_FOUND` (nebo 0x03) mapuje na <xref:System.IO.DirectoryNotFoundException>.

Přesné podmínky, za kterých operační systém vrací konkrétní kódy chyb, jsou však často nedokumentované nebo špatně zdokumentované. V důsledku toho může dojít k neočekávaným výjimkám. Například proto, že pracujete s adresářem, nikoli se souborem, očekáváte, že poskytnutí neplatné cesty k adresáři <xref:System.IO.DirectoryInfo.%23ctor%2A> konstruktoru <xref:System.IO.DirectoryNotFoundException>vyvolá . Nicméně, to může <xref:System.IO.FileNotFoundException>také hodit .

## <a name="exception-handling-in-io-operations"></a>Zpracování výjimek v vstupně-va operacích

Z důvodu tohoto spoléhání se na operační systém, stejné podmínky výjimky (například adresář nebyl nalezen chyba v našem příkladu) může mít za následek vstupně-va metody vyvolání některé z celé třídy výjimky vstupně-v..I. To znamená, že při volání vstupně-v. API, váš kód by měl být připraven ke zpracování většiny nebo všech těchto výjimek, jak je znázorněno v následující tabulce:

| Typ výjimky | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Ano | Ano |
| <xref:System.IO.FileNotFoundException> | Ano | Ano |
| <xref:System.IO.DirectoryNotFoundException> | Ano | Ano |
| <xref:System.IO.DriveNotFoundException?> | Ano | Ano |
| <xref:System.IO.PathTooLongException> | Ano | Ano |
| <xref:System.OperationCanceledException> | Ano | Ano |
| <xref:System.UnauthorizedAccessException> | Ano | Ano |
| <xref:System.ArgumentException> | .NET Core 2.0 a starší| Ano |
| <xref:System.NotSupportedException> | Ne | Ano |
| <xref:System.Security.SecurityException> | Ne | Pouze omezená důvěra |

## <a name="handling-ioexception"></a>Zpracování ioException

Jako základní třída pro výjimky v oboru <xref:System.IO> názvů je také vyvolána pro jakýkoli kód chyby, <xref:System.IO.IOException> který není mapován na předdefinovaný typ výjimky. To znamená, že může být vyvolána jakoukoli vstupně-o operací.

> [!IMPORTANT]
> Vzhledem k tomu, že <xref:System.IO.IOException> je <xref:System.IO> základní třída jiných typů `catch` výjimek v oboru názvů, měli byste zpracovat v bloku po zpracování ostatních výjimek souvisejících s vstupně-va.

Kromě toho počínaje .NET Core 2.1, ověření kontroly správnosti cesty (například k zajištění, že neplatné znaky nejsou k dispozici v cestě) byly odebrány a runtime vyvolá výjimku mapována z kódu chyby operačního systému, nikoli z jeho vlastní ověřovací kód. Nejpravděpodobnější výjimka, která má být <xref:System.IO.IOException>vyvolána v tomto případě je , i když jakýkoli jiný typ výjimky může být také vyvolána.

Všimněte si, že v kódu zpracování <xref:System.IO.IOException> výjimek byste měli vždy zpracovat poslední. Jinak, protože je základní třídy všech ostatních výjimek vi, catch bloky odvozené třídy nebudou vyhodnoceny.

V případě <xref:System.IO.IOException>, můžete získat další informace o chybě z [IOException.HResult](xref:System.Exception.HResult) vlastnost. Chcete-li převést hodnotu HResult na kód chyby Win32, odstraňte horních 16 bitů 32bitové hodnoty. V následující tabulce jsou uvedeny kódy <xref:System.IO.IOException>chyb, které mohou být zabaleny do souboru .

| Hresult | Trvalé | Popis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Název souboru chybí nebo je soubor nebo adresář používán. |
| ERROR_FILE_EXISTS | 80 | Soubor již existuje. |
| ERROR_INVALID_PARAMETER | 87 | Argument dodaný metodě je neplatný. |
| ERROR_ALREADY_EXISTS | 183 | Soubor nebo adresář již existuje. |

Můžete zpracovat pomocí `When` klauzule v catch prohlášení, jak ukazuje následující příklad.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Viz také

- [Zpracování a vyvolání výjimek v rozhraní .NET](../exceptions/index.md)
- [Zpracování výjimek (paralelní knihovna úloh)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Doporučené postupy pro výjimky](../exceptions/best-practices-for-exceptions.md)
- [Použití konkrétních výjimek v bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
