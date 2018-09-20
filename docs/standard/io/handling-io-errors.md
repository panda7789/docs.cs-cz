---
title: Zpracování chyb vstupně-výstupní operace v rozhraní .NET
ms.date: 08/27/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50dee427913e1ec94a06f1202966bb0f7f5f2099
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326687"
---
# <a name="handling-io-errors-in-net"></a>Zpracování chyb vstupně-výstupní operace v rozhraní .NET

Kromě výjimky, které mohou být vyvolány v žádném volání metody (například <xref:System.OutOfMemoryException> systému je třeba zdůraznit, nebo s <xref:System.NullReferenceException> z důvodu chyby programátor), .NET metody systému souborů může vyvolat následující výjimky:

- <xref:System.IO.IOException?displayProperty=nameWithType>, základní třída všech <xref:System.IO> typy výjimek. Je vyvolána výjimka, chyby, jehož návratové kódy z operačního systému není mapují přímo na jiný typ výjimky.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, která je vyvolána neplatná cesta znaků v rozhraní .NET Framework a .NET Core 2.0 a předchozí verze.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, která je vyvolána neplatná použití dvojteček v rozhraní .NET Framework.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, která je vyvolána pro aplikace běžící v omezené vztahu důvěryhodnosti, které nemají potřebná oprávnění na rozhraní .NET Framework pouze. (Úplný vztah důvěryhodnosti je výchozí hodnota v rozhraní .NET Framework.)

## <a name="mapping-error-codes-to-exceptions"></a>Mapování kódů chyb a výjimek

Protože systém souborů je prostředek operačního systému, vstupně-výstupní metody v .NET Core a .NET Framework obalují volání základního operačního systému. Když dojde k chybě vstupně-výstupní operace v kódu prováděném operačním systémem, operační systém vrátí informace o chybě metodě .NET vstupně-výstupních operací. Metoda pak přeloží informace o chybě, obvykle v podobě chybový kód, na typ .NET výjimky. Ve většině případů to dělá tak, že přímo překládá na jeho odpovídající typ výjimky; kód chyby: neprovede žádné speciální mapování chybu na základě kontextu volání metody.

Například v operačním systému Windows, volání metody, která vrací kód chyby `ERROR_FILE_NOT_FOUND` (nebo 0x02) mapuje na <xref:System.IO.FileNotFoundException>a kód chyby `ERROR_PATH_NOT_FOUND` (nebo 0x03) se mapuje <xref:System.IO.DirectoryNotFoundException>.

Přesné podmínky, za kterých operační systém vrátí určité chybové kódy je však často nedokumentované nebo špatně dokument. V důsledku toho může dojít k neočekávaným výjimkám. Například vzhledem k tomu, že pracujete s adresáři, nikoli soubor, které by uživatel očekával poskytující neplatná cesta k adresáři na <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> vyvolá konstruktor <xref:System.IO.DirectoryNotFoundException>. Ale může také vyvolat <xref:System.IO.FileNotFoundException>.

## <a name="exception-handling-in-io-operations"></a>Zpracování výjimek v vstupně-výstupních operací

Z důvodu této závislosti na operačním systému podmínky výjimek identické (například adresář nebyl nalezen chyba v našem příkladu) může vést k metodu vstupně-výstupních operací vyvolání některý celou třídu výjimky vstupně-výstupních operací. To znamená, že při volání rozhraní API pro vstupně-výstupních operací, váš kód by měla být připravena zpracovat většinu nebo všechny tyto výjimky, jak je znázorněno v následující tabulce:

| Typ výjimky | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Ano | Ano |
| <xref:System.IO.FileNotFoundException> | Ano | Ano |
| <xref:System.IO.DirectoryNotFoundException> | Ano | Ano |
| <xref:System.IO.DriveNotFoundException?> | Ano | Ano |
| <xref:System.IO.PathTooLongException> | Ano | Ano |
| <xref:System.OperationCanceledException> | Ano | Ano |
| <xref:System.UnauthorizedAccessException> | Ano | Ano |
| <xref:System.ArgumentException> | .NET core 2.0 a starší| Ano |
| <xref:System.NotSupportedException> | Ne | Ano |
| <xref:System.Security.SecurityException> | Ne | Pouze omezený vztah důvěryhodnosti |

## <a name="handling-ioexception"></a>IOException – zpracování

Jako základní třída pro výjimky ve <xref:System.IO> obor názvů, <xref:System.IO.IOException> je také pro libovolný kód chyby, které nejsou namapované na typ předdefinovaná výjimka vyvolána. To znamená, že mohou být vyvolány ve všech vstupně-výstupní operace.

> [!IMPORTANT]
> Protože <xref:System.IO.IOException> je základní třídou jiné typy výjimek v <xref:System.IO> obor názvů, můžete pracovat v `catch` blokovat po jsme zpracování I O souvisejícím s/výjimky.

Kromě toho počínaje .NET Core 2.1, ověřovacích kontrol správnosti cestu (například k zajištění, že neplatné znaky nejsou k dispozici v cestě) byly odebrány, a modul runtime vyvolá výjimku, mapovaná z kód chyby operačního systému místo z vlastního ověřovacího kódu. V tomto případě je pravděpodobně výjimka, která má být vyvolána <xref:System.IO.IOException>, i když může být vyvoláno také jakýkoli jiný typ výjimky.

Všimněte si, že v váš kód zpracování výjimek, vždy zpracovávejte <xref:System.IO.IOException> poslední. Jinak protože je základní třídy pro všechny ostatní výjimky vstupně-výstupních operací, nebude vyhodnocen bloky catch odvozených tříd.

V případě třídy <xref:System.IO.IOException>, získáte další informace o chybě z [IOException.HResult](xref:System.Exception.HResult) vlastnost. Převede hodnotu HResult kódu chyby Win32, můžete odstranit horní 16 bitů 32bitová hodnota. V následující tabulce jsou uvedeny kódy chyb, které mohou být uzavřen do <xref:System.IO.IOException>.

| Hodnota HResult | Konstanta | Popis |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Chybí název souboru nebo souboru nebo adresáře se používá. |
| ERROR_FILE_EXISTS | 80 | Soubor již existuje. |
| ERROR_INVALID_PARAMETER | 87 | Argument zadaný pro metodu je neplatný. |
| ERROR_ALREADY_EXISTS | 183 | Soubor nebo adresář již existuje. |

Můžete zpracovat pomocí `When` klauzulí catch příkazu, jak ukazuje následující příklad.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Viz také:

- [Zpracování a vyvolání výjimek v rozhraní .NET](../exceptions/index.md)
- [Zpracování výjimek (Task Parallel Library)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Doporučené postupy pro výjimky](../exceptions/best-practices-for-exceptions.md)
- [Postup používání specifických výjimek v bloku catch](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)