---
title: Vstupně-výstupní operace se soubory a datovým proudem – .NET
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 889271ca41fb84b44757adfffc61ffbfbc0a03a8
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204799"
---
# <a name="file-and-stream-io"></a>I/O souborů a proudů

Vstupem/výstupem souborů a datových proudů se rozumí přenos dat z úložného média nebo na něj. V .NET Framework `System.IO` obory názvů obsahují typy, které umožňují čtení a zápis, jak synchronně, tak asynchronně, na datových proudech a souborech. Tyto obory názvů obsahují také typy provádějící kompresi a dekompresi souborů a typy umožňující komunikaci pomocí kanálů a sériových portů.

Soubor je uspořádaná a pojmenovaná kolekce bajtů s trvalým úložištěm. Pracujete-li se soubory, pracujete s cestami adresářů, diskovým úložištěm a názvy souborů a adresářů. Naproti tomu datový proud je posloupnost bajtů, kterou lze použít ke čtení nebo zápisu na záložní úložiště, jímž může být jedno nebo více úložných médií (například disky nebo paměť). Stejně jako existuje několik záložních úložišť jiných než disky, existuje několik druhů datových proudů jiných než datové proudy souborů, například proudy sítí, pamětí nebo kanálů.

## <a name="files-and-directories"></a>Soubory a adresáře

Můžete použít typy v oboru názvů <xref:System.IO?displayProperty=nameWithType> pro interakci se soubory a adresáři. Lze tak například načíst nebo nastavit vlastnosti souborů a adresářů nebo načíst kolekce souborů a adresářů na základě kritérií vyhledávání.

Pro konvence pojmenovávání cest a způsoby, jak vyjádřit cestu k souborům pro systémy Windows, včetně syntaxe zařízení DOS podporované v .NET Core 1,1 a novějších a .NET Framework 4.6.2 a novějších verzích, najdete v tématu [formáty cest souborů v systémech Windows](file-path-formats.md).

Zde jsou některé běžně používané třídy souborů a adresářů:

- <xref:System.IO.File> – poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá vytvořit objekt <xref:System.IO.FileStream>.

- <xref:System.IO.FileInfo> – poskytuje metody instance pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá vytvořit objekt <xref:System.IO.FileStream>.

- <xref:System.IO.Directory> – poskytuje statické metody pro vytváření, přesouvání a vytváření výčtu adresářů a podadresářů.

- <xref:System.IO.DirectoryInfo> – poskytuje metody instance pro vytváření, přesouvání a vytváření výčtu adresářů a podadresářů.

- <xref:System.IO.Path> – poskytuje metody a vlastnosti pro zpracování řetězců adresáře v rámci způsobu pro různé platformy.

Při volání metod systému souborů byste měli vždy poskytovat robustní zpracování výjimek. Další informace najdete v tématu [zpracování vstupně-výstupních chyb](handling-io-errors.md).

Kromě použití těchto tříd mohou uživatelé Visual Basic použít metody a vlastnosti poskytované třídou <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> pro vstupně-výstupní operace se soubory.

Informace najdete v tématech [Postup: kopírování adresářů](how-to-copy-directories.md), [Postupy: vytvoření výpisu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))a [Postup: zobrazení výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Datové proudy

Abstraktní základní třída <xref:System.IO.Stream> podporuje čtení a zápis bajtů. Všechny třídy, které reprezentují datové proudy, dědí z třídy <xref:System.IO.Stream>. Třída <xref:System.IO.Stream> a její odvozené třídy poskytují běžné zobrazení zdrojů dat a úložišť a izoluje programátora od konkrétních podrobností o operačním systému a základních zařízeních.

Datové proudy zahrnují tři základní operace:

- Čtení – přenos dat z datového proudu do datové struktury, například pole bajtů.

- Zápis – přenos dat ze zdroje dat do datového proudu.

- Hledání – dotazování a úprava současné pozice v datovém proudu.

Datový proud může podporovat pouze některé z těchto možností v závislosti na použitém zdroji dat nebo úložišti. Například třída <xref:System.IO.Pipes.PipeStream> nepodporuje hledání. Vlastnosti <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>a <xref:System.IO.Stream.CanSeek%2A> datového proudu určují operace, které datový proud podporuje.

Toto jsou některé běžně používané třídy datového proudu:

- <xref:System.IO.FileStream> – pro čtení a zápis do souboru.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – pro čtení a zápis do souboru v izolovaném úložišti.

- <xref:System.IO.MemoryStream> – pro čtení a zápis do paměti jako záložní úložiště.

- <xref:System.IO.BufferedStream> – pro zlepšení výkonu operací čtení a zápisu.

- <xref:System.Net.Sockets.NetworkStream> – pro čtení a zápis přes síťové sokety.

- <xref:System.IO.Pipes.PipeStream> – pro čtení a zápis přes anonymní a pojmenované kanály.

- <xref:System.Security.Cryptography.CryptoStream> – pro propojení datových proudů s kryptografickými transformacemi.

Příklad práce s datovými proudy lze asynchronně zobrazit v tématu [asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Čtenáři a zapisovače

Obor názvů <xref:System.IO?displayProperty=nameWithType> také poskytuje typy pro čtení kódovaných znaků z datových proudů a jejich zápis do datových proudů. Datové proudy jsou obvykle navrženy pro bajtový vstup a výstup. Typy čtečky a zapisovače zajišťují převod kódovaných znaků na bajty a zpět, aby datový proud mohl dokončit operaci. Každá třída čtecího modulu a zapisovače je přidružena ke streamu, který lze načíst prostřednictvím vlastnosti `BaseStream` třídy.

Toto jsou některé běžně používané třídy čteček a zapisovačů:

- <xref:System.IO.BinaryReader> a <xref:System.IO.BinaryWriter> – pro čtení a zápis primitivních datových typů jako binárních hodnot.

- <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> – pro čtení a zápis znaků pomocí hodnoty kódování pro převod znaků do a z bajtů.

- <xref:System.IO.StringReader> a <xref:System.IO.StringWriter> – pro čtení a zápis znaků do řetězců a z.

- <xref:System.IO.TextReader> a <xref:System.IO.TextWriter> – slouží jako abstraktní základní třídy pro jiné čtenáře a zapisovače, které čtou a zapisují znaky a řetězce, ale ne binární data.

Viz [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md), [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md), [Postupy: čtení znaků z řetězce](how-to-read-characters-from-a-string.md)a [Postupy: zápis znaků do řetězce](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Asynchronní vstupně-výstupní operace

Čtení a zápis velkého množství dat může zatěžovat prostředky. Má-li aplikace nadále reagovat na uživatele, je zapotřebí tyto úkoly provádět asynchronně. Při synchronních vstupně-výstupních operacích je vlákno uživatelského rozhraní zablokováno, dokud není operace náročná na prostředky dokončena.  Použijte asynchronní vstupně-výstupní operace při vývoji aplikací pro Windows 8. x Store, abyste zabránili vytváření dojmu o tom, že vaše aplikace přestala fungovat.

Asynchronní členové obsahují `Async` v jejich názvech, jako jsou metody <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>a <xref:System.IO.Stream.WriteAsync%2A>. Tyto metody můžete použít s klíčovými slovy `async` a `await`.

Další informace najdete v tématu [asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md).

## <a name="compression"></a>Komprese

Kompresí se rozumí proces zmenšení velikosti ukládaného souboru. Dekomprese je proces extrahování obsahu komprimovaného souboru do použitelného formátu. Obor názvů <xref:System.IO.Compression?displayProperty=nameWithType> obsahuje typy pro komprimaci a dekompresi souborů a datových proudů.

Následující třídy jsou při kompresi a dekompresi souborů a datových proudů často používány:

- <xref:System.IO.Compression.ZipArchive> – pro vytváření a načítání položek v archivu zip.

- <xref:System.IO.Compression.ZipArchiveEntry> – pro reprezentaci komprimovaného souboru.

- <xref:System.IO.Compression.ZipFile> – pro vytváření, extrakci a otevírání komprimovaného balíčku.

- <xref:System.IO.Compression.ZipFileExtensions> – pro vytváření a extrahování položek v komprimovaném balíčku.

- <xref:System.IO.Compression.DeflateStream> – pro komprimaci a dekompresi datových proudů pomocí algoritmu deflate.

- <xref:System.IO.Compression.GZipStream> – pro komprimaci a dekompresi datových proudů v datovém formátu gzip.

Viz [Postup: komprimace a extrakce souborů](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Izolované úložiště

Izolované úložiště je mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty. Úložiště poskytuje virtuální systém souborů izolovaný uživatelem, sestavením a (volitelně) doménou. Izolované úložiště je obzvláště užitečné, nemá-li aplikace oprávnění k přístupu k uživatelským souborům. Lze tak ukládat nastavení nebo soubory aplikace způsobem řízeným zásadami zabezpečení daného počítače.

Izolované úložiště není k dispozici pro aplikace Windows 8. x Store. místo toho použijte aplikační datové třídy v oboru názvů <xref:Windows.Storage?displayProperty=nameWithType>. Další informace najdete v tématu [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Při implementaci izolovaného úložiště jsou běžně používány následující třídy:

- <xref:System.IO.IsolatedStorage.IsolatedStorage> – poskytuje základní třídu pro implementace izolovaného úložiště.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – poskytuje izolovanou oblast úložiště obsahující soubory a adresáře.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – zpřístupní soubor v izolovaném úložišti.

Viz [izolované úložiště](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Vstupně-výstupní operace v aplikacích pro Windows Store

[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] obsahuje mnoho typů pro čtení a zápis do datových proudů; Tato sada ale neobsahuje všechny .NET Framework vstupně-výstupních typech.

Některé důležité rozdíly při používání vstupně-výstupních operací v aplikacích pro Store ve Windows 8. x:

- Typy, které se konkrétně týkají operací se soubory, například <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> a <xref:System.IO.DirectoryInfo>, nejsou součástí [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Místo toho použijte typy v oboru názvů <xref:Windows.Storage?displayProperty=nameWithType> prostředí Windows Runtime, například <xref:Windows.Storage.StorageFile> a <xref:Windows.Storage.StorageFolder>.

- Izolované úložiště není k dispozici; místo toho použijte [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Použijte asynchronní metody, například <xref:System.IO.Stream.ReadAsync%2A> a <xref:System.IO.Stream.WriteAsync%2A>, k zabránění blokování vlákna uživatelského rozhraní.

- Typy komprese založené na cestách <xref:System.IO.Compression.ZipFile> a <xref:System.IO.Compression.ZipFileExtensions> nejsou k dispozici. Místo toho použijte typy v oboru názvů <xref:Windows.Storage.Compression?displayProperty=nameWithType>.

V případě potřeby je možné převádět mezi proudy rozhraní .NET Framework a proudy Windows Runtime. Další informace naleznete v tématu [How to: Convert Between .NET Framework Streams and prostředí Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md) or <xref:System.IO.WindowsRuntimeStreamExtensions>.

Další informace o vstupně-výstupních operacích v aplikaci Windows 8. x Store najdete v tématu [rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>I/O a zabezpečení

Pokud používáte třídy v oboru názvů <xref:System.IO?displayProperty=nameWithType>, musíte dodržovat požadavky na zabezpečení operačního systému, jako jsou seznamy řízení přístupu (ACL), abyste mohli řídit přístup k souborům a adresářům. Tento požadavek se týká i všech <xref:System.Security.Permissions.FileIOPermission> požadavků. Seznamy ACL lze spravovat programově. Další informace najdete v tématu [Postup: Přidání nebo odebrání položek seznamu Access Control](how-to-add-or-remove-access-control-list-entries.md).

Výchozí zásady zabezpečení zabraňují internetovým a intranetovým aplikacím v přístupu k souborům na počítači uživatele. Proto při psaní kódu, který bude stažen přes internet nebo intranet, nepoužívejte vstupně-výstupní třídy požadující cestu k fyzickému souboru. Místo toho použijte [izolované úložiště](isolated-storage.md) pro tradiční .NET Framework aplikace nebo použijte [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) pro aplikace Windows 8. x Store.

Kontrola zabezpečení se provádí pouze při konstrukci datového proudu. Proto neotevírejte datový proud a poté jej nepředávejte méně důvěryhodnému kódu nebo doménám aplikace.

## <a name="related-topics"></a>Příbuzná témata

- [Běžné vstupně-výstupní úlohy](common-i-o-tasks.md)\
Poskytuje seznam vstupně-výstupních úkolů přidružených k souborům, adresářům a datovým proudům a odkazuje pro každý úkol na relevantní obsah a příklady.

- [Asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md)\
Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.

- [Izolované úložiště](isolated-storage.md)\
Popisuje mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty.

- \ [kanálů](pipe-operations.md)
Popisuje operace anonymních a pojmenovaných kanálů v rozhraní .NET Framework.

- [Soubory mapované v paměti](memory-mapped-files.md)\
Popisuje soubory mapované paměti, které obsahují obsah souborů na disku ve virtuální paměti. Soubory mapované paměti lze použít k úpravě velmi velkých souborů a k vytváření sdílené paměti pro komunikaci mezi procesy.
