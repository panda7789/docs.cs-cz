---
title: Vstupně-tono-datové hodu a datového proudu – rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
ms.openlocfilehash: 3c69e0fd23b1f8bc11fe908c66ba492f31a53f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706592"
---
# <a name="file-and-stream-io"></a>I/O souborů a proudů

Vstupem/výstupem souborů a datových proudů se rozumí přenos dat z úložného média nebo na něj. V rozhraní .NET `System.IO` Framework obsahují obory názvů typy, které umožňují čtení a zápis synchronně i asynchronně v datových proudech a souborech. Tyto obory názvů obsahují také typy provádějící kompresi a dekompresi souborů a typy umožňující komunikaci pomocí kanálů a sériových portů.

Soubor je uspořádaná a pojmenovaná kolekce bajtů s trvalým úložištěm. Pracujete-li se soubory, pracujete s cestami adresářů, diskovým úložištěm a názvy souborů a adresářů. Naproti tomu datový proud je posloupnost bajtů, kterou lze použít ke čtení nebo zápisu na záložní úložiště, jímž může být jedno nebo více úložných médií (například disky nebo paměť). Stejně jako existuje několik záložních úložišť jiných než disky, existuje několik druhů datových proudů jiných než datové proudy souborů, například proudy sítí, pamětí nebo kanálů.

## <a name="files-and-directories"></a>Soubory a adresáře

Typy v oboru <xref:System.IO?displayProperty=nameWithType> názvů můžete použít k interakci se soubory a adresáři. Lze tak například načíst nebo nastavit vlastnosti souborů a adresářů nebo načíst kolekce souborů a adresářů na základě kritérií vyhledávání.

Konvence pojmenování cest a způsoby vyjádření cesty k souboru pro systémy Windows, včetně syntaxe zařízení DOS podporované v rozhraní .NET Core 1.1 a novější a rozhraní .NET Framework 4.6.2 a novější, naleznete v [tématu Formáty cest souborů v systémech Windows](file-path-formats.md).

Zde jsou některé běžně používané třídy souborů a adresářů:

- <xref:System.IO.File>- poskytuje statické metody pro vytváření, kopírování, mazání, přesouvání a <xref:System.IO.FileStream> otevírání souborů a pomáhá vytvářet objekt.

- <xref:System.IO.FileInfo>- poskytuje metody instance pro vytváření, kopírování, mazání, přesouvání a <xref:System.IO.FileStream> otevírání souborů a pomáhá vytvářet objekt.

- <xref:System.IO.Directory>- poskytuje statické metody pro vytváření, přesouvání a vytváření výčtu prostřednictvím adresářů a podadresářů.

- <xref:System.IO.DirectoryInfo>- poskytuje metody instance pro vytváření, přesouvání a vytváření výčtů prostřednictvím adresářů a podadresářů.

- <xref:System.IO.Path>- poskytuje metody a vlastnosti pro zpracování adresářových řetězců způsobem napříč platformami.

Při volání metod souborového systému byste měli vždy poskytnout robustní zpracování výjimek. Další informace naleznete v [tématu Zpracování vstupně-va/v chyby](handling-io-errors.md).

Kromě použití těchto tříd mohou uživatelé jazyka Visual Basic používat <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> metody a vlastnosti poskytované třídou pro vstupně-va souboru.

Viz [Postup: Kopírování adresářů](how-to-copy-directories.md), [Postup: Vytvoření výpisu adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))a [Postup: Výčet adresářů a souborů](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Datové proudy

Abstraktní základní <xref:System.IO.Stream> třída podporuje čtení a zápis bajtů. Všechny třídy, které představují <xref:System.IO.Stream> datové proudy dědí z třídy. Třída <xref:System.IO.Stream> a její odvozené třídy poskytují společné zobrazení zdrojů dat a úložišť a izolují programátora od konkrétních podrobností operačního systému a podkladových zařízení.

Datové proudy zahrnují tři základní operace:

- Čtení – přenos dat z datového proudu do datové struktury, například pole bajtů.

- Zápis – přenos dat ze zdroje dat do datového proudu.

- Hledání – dotazování a úprava současné pozice v datovém proudu.

Datový proud může podporovat pouze některé z těchto možností v závislosti na použitém zdroji dat nebo úložišti. Například <xref:System.IO.Pipes.PipeStream> třída nepodporuje hledání. <xref:System.IO.Stream.CanRead%2A>Vlastnosti <xref:System.IO.Stream.CanWrite%2A>, <xref:System.IO.Stream.CanSeek%2A> a stream určují operace, které podporuje datový proud.

Toto jsou některé běžně používané třídy datového proudu:

- <xref:System.IO.FileStream>– pro čtení a zápis do souboru.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>– pro čtení a zápis do souboru v izolovaném úložišti.

- <xref:System.IO.MemoryStream>– pro čtení a zápis do paměti jako záložní úložiště.

- <xref:System.IO.BufferedStream>– pro zlepšení výkonu operací čtení a zápisu.

- <xref:System.Net.Sockets.NetworkStream>– pro čtení a zápis přes síťové zásuvky.

- <xref:System.IO.Pipes.PipeStream>– pro čtení a psaní přes anonymní a pojmenované trubky.

- <xref:System.Security.Cryptography.CryptoStream>– pro propojení datových toků s kryptografickými transformacemi.

Příklad práce s datovými proudy asynchronně naleznete v [tématu Asynchronní vstupně-mail .](asynchronous-file-i-o.md)

## <a name="readers-and-writers"></a>Čtenáři a spisovatelé

Obor <xref:System.IO?displayProperty=nameWithType> názvů také poskytuje typy pro čtení kódovaných znaků z datových proudů a jejich zápis do datových proudů. Datové proudy jsou obvykle navrženy pro bajtový vstup a výstup. Typy čtečky a zapisovače zajišťují převod kódovaných znaků na bajty a zpět, aby datový proud mohl dokončit operaci. Každá třída čtečky a zapisovače je přidružena k `BaseStream` datovému proudu, který lze načíst prostřednictvím vlastnosti třídy.

Toto jsou některé běžně používané třídy čteček a zapisovačů:

- <xref:System.IO.BinaryReader>a <xref:System.IO.BinaryWriter> – pro čtení a zápis primitivních datových typů jako binární hodnoty.

- <xref:System.IO.StreamReader>a <xref:System.IO.StreamWriter> – pro čtení a zápis znaků pomocí hodnoty kódování převést znaky do a z bajtů.

- <xref:System.IO.StringReader>a <xref:System.IO.StringWriter> – pro čtení a zápis znaků do a z řetězců.

- <xref:System.IO.TextReader>a <xref:System.IO.TextWriter> – slouží jako abstraktní základní třídy pro ostatní čtenáře a autory, kteří čtou a zapisují znaky a řetězce, ale ne binární data.

Viz [Postup: Čtení textu ze souboru](how-to-read-text-from-a-file.md), [Postup: Zápis textu do souboru](how-to-write-text-to-a-file.md), [Postup: Čtení znaků z řetězce](how-to-read-characters-from-a-string.md)a [Jak: Zápis znaků do řetězce](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Asynchronní vstupně-va operace

Čtení a zápis velkého množství dat může zatěžovat prostředky. Má-li aplikace nadále reagovat na uživatele, je zapotřebí tyto úkoly provádět asynchronně. Při synchronních vstupně-výstupních operacích je vlákno uživatelského rozhraní zablokováno, dokud není operace náročná na prostředky dokončena.  Při vývoji aplikací pro Windows 8.x Store používejte asynchronní vstupně-va, abyste zabránili vytvoření dojmu, že vaše aplikace přestala fungovat.

Asynchronní členy obsahují `Async` ve svých názvech, <xref:System.IO.Stream.FlushAsync%2A> <xref:System.IO.Stream.ReadAsync%2A>například <xref:System.IO.Stream.WriteAsync%2A> <xref:System.IO.Stream.CopyToAsync%2A>, , a metody. Tyto metody se `async` používají `await` s a klíčová slova.

Další informace naleznete [v tématu Asynchronní soubor V/O](asynchronous-file-i-o.md).

## <a name="compression"></a>Komprese

Kompresí se rozumí proces zmenšení velikosti ukládaného souboru. Dekomprese je proces extrahování obsahu komprimovaného souboru do použitelného formátu. Obor <xref:System.IO.Compression?displayProperty=nameWithType> názvů obsahuje typy pro kompresi a dekompresi souborů a datových proudů.

Následující třídy jsou při kompresi a dekompresi souborů a datových proudů často používány:

- <xref:System.IO.Compression.ZipArchive>– pro vytváření a načítání položek v archivu zip.

- <xref:System.IO.Compression.ZipArchiveEntry>– pro reprezentaci komprimovaného souboru.

- <xref:System.IO.Compression.ZipFile>– pro vytvoření, extrahování a otevření komprimovaného obalu.

- <xref:System.IO.Compression.ZipFileExtensions>– pro vytváření a extrahování položek v komprimovaném balení.

- <xref:System.IO.Compression.DeflateStream>– pro kompresi a dekompresi proudů pomocí algoritmu Deflate.

- <xref:System.IO.Compression.GZipStream>– pro kompresi a dekompresi datových proudů ve formátu gzip data.

Viz [Postup: Komprese a extrahování souborů](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Izolované úložiště

Izolované úložiště je mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty. Úložiště poskytuje virtuální systém souborů izolovaný uživatelem, sestavením a (volitelně) doménou. Izolované úložiště je obzvláště užitečné, nemá-li aplikace oprávnění k přístupu k uživatelským souborům. Lze tak ukládat nastavení nebo soubory aplikace způsobem řízeným zásadami zabezpečení daného počítače.

Izolované úložiště není dostupné pro aplikace pro Windows 8.x Store. místo toho použijte třídy <xref:Windows.Storage?displayProperty=nameWithType> dat aplikace v oboru názvů. Další informace naleznete v [tématu Data aplikace](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Při implementaci izolovaného úložiště jsou běžně používány následující třídy:

- <xref:System.IO.IsolatedStorage.IsolatedStorage>– poskytuje základní třídu pro implementace izolovaného úložiště.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>– poskytuje izolované úložiště, které obsahuje soubory a adresáře.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>- zpřístupní soubor v izolovaném úložišti.

Viz [Izolované úložiště](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Vstupně-nosné operace v aplikacích pro Windows Store

Rozhraní .NET pro aplikace pro Windows 8.x Store obsahuje mnoho typů pro čtení a zápis do datových proudů; Tato sada však nezahrnuje všechny typy vstupně-v.O rozhraní .NET Framework.

Některé důležité rozdíly, které je třeba si uvědomit při používání vstupně-va operací v aplikacích pro Windows 8.x Store:

- Typy specificky související s <xref:System.IO.File>operacemi se soubory, například , <xref:System.IO.FileInfo> <xref:System.IO.Directory> a <xref:System.IO.DirectoryInfo>, nejsou zahrnuty v rozhraní .NET pro aplikace pro Windows 8.x Store. Místo toho použijte typy <xref:Windows.Storage?displayProperty=nameWithType> v oboru názvů prostředí Windows <xref:Windows.Storage.StorageFile> <xref:Windows.Storage.StorageFolder>Runtime, například a .

- Izolované úložiště není k dispozici. místo toho použijte [data aplikace](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Použijte asynchronní metody, <xref:System.IO.Stream.ReadAsync%2A> například a <xref:System.IO.Stream.WriteAsync%2A>, chcete-li zabránit blokování vlákna uživatelského rozhraní.

- Typy <xref:System.IO.Compression.ZipFile> komprese založené na <xref:System.IO.Compression.ZipFileExtensions> cestě a nejsou k dispozici. Místo toho použijte typy <xref:Windows.Storage.Compression?displayProperty=nameWithType> v oboru názvů.

V případě potřeby je možné převádět mezi proudy rozhraní .NET Framework a proudy Windows Runtime. Další informace naleznete v [tématu How to: Convert Between .NET Framework Streams and Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md) or <xref:System.IO.WindowsRuntimeStreamExtensions>.

Další informace o vstupně-nevodíchacích operacích v aplikaci pro Windows 8.x Store najdete v [tématu Úvodní příručka: Čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>Vstupně-no a zabezpečení

Při použití tříd v <xref:System.IO?displayProperty=nameWithType> oboru názvů je nutné dodržovat požadavky na zabezpečení operačního systému, jako jsou seznamy řízení přístupu (ACL) pro řízení přístupu k souborům a adresářům. Tento požadavek je <xref:System.Security.Permissions.FileIOPermission> navíc k veškeré požadavky. Seznamy ACL lze spravovat programově. Další informace naleznete v [tématu How to: Add or Remove Access Control List Entries](how-to-add-or-remove-access-control-list-entries.md).

Výchozí zásady zabezpečení zabraňují internetovým a intranetovým aplikacím v přístupu k souborům na počítači uživatele. Proto při psaní kódu, který bude stažen přes internet nebo intranet, nepoužívejte vstupně-výstupní třídy požadující cestu k fyzickému souboru. Místo toho použijte [izolované úložiště](isolated-storage.md) pro tradiční aplikace rozhraní .NET Framework nebo použijte [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) pro aplikace pro Windows 8.x Store.

Kontrola zabezpečení se provádí pouze při konstrukci datového proudu. Proto neotevírejte datový proud a poté jej nepředávejte méně důvěryhodnému kódu nebo doménám aplikace.

## <a name="related-topics"></a>Související témata

- [Běžné vstupně-v úkoly](common-i-o-tasks.md)\
Poskytuje seznam vstupně-výstupních úkolů přidružených k souborům, adresářům a datovým proudům a odkazuje pro každý úkol na relevantní obsah a příklady.

- [Vstupně-nosný soubor asynchronní](asynchronous-file-i-o.md)\
Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.

- [Izolované úložiště](isolated-storage.md)\
Popisuje mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty.

- [Trubky](pipe-operations.md)\
Popisuje operace anonymních a pojmenovaných kanálů v rozhraní .NET Framework.

- [Soubory mapované v paměti](memory-mapped-files.md)\
Popisuje soubory mapované paměti, které obsahují obsah souborů na disku ve virtuální paměti. Soubory mapované paměti lze použít k úpravě velmi velkých souborů a k vytváření sdílené paměti pro komunikaci mezi procesy.
