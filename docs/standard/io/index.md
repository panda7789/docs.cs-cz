---
title: I/O souborů a proudů
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
ms.openlocfilehash: 6bd0187f831db7fd68272e14c022efb45c8260f2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070822"
---
# <a name="file-and-stream-io"></a>I/O souborů a proudů
Vstupem/výstupem souborů a datových proudů se rozumí přenos dat z úložného média nebo na něj. V rozhraní .NET Framework `System.IO` obory názvů obsahují typy, které umožňují čtení a zápis, synchronně i asynchronně, na soubory a datovými proudy. Tyto obory názvů obsahují také typy provádějící kompresi a dekompresi souborů a typy umožňující komunikaci pomocí kanálů a sériových portů.  
  
 Soubor je uspořádaná a pojmenovaná kolekce bajtů s trvalým úložištěm. Pracujete-li se soubory, pracujete s cestami adresářů, diskovým úložištěm a názvy souborů a adresářů. Naproti tomu datový proud je posloupnost bajtů, kterou lze použít ke čtení nebo zápisu na záložní úložiště, jímž může být jedno nebo více úložných médií (například disky nebo paměť). Stejně jako existuje několik záložních úložišť jiných než disky, existuje několik druhů datových proudů jiných než datové proudy souborů, například proudy sítí, pamětí nebo kanálů.  
  
## <a name="files-and-directories"></a>Soubory a adresáře  
 Můžete použít typy v <xref:System.IO?displayProperty=nameWithType> obor názvů pro interakci se soubory a adresáře. Lze tak například načíst nebo nastavit vlastnosti souborů a adresářů nebo načíst kolekce souborů a adresářů na základě kritérií vyhledávání.  

Cesta konvence pojmenování a způsoby, jak vyjádřit cestu k souboru pro systémy Windows, včetně syntaxi zařízení DOS, podporuje se v .NET Core 1.1 nebo novější a rozhraní .NET Framework 4.6.2 nebo novější, najdete v článku [cesta formáty souborů v systémech Windows](file-path-formats.md). 
  
 Zde jsou některé běžně používané třídy souborů a adresářů:  
  
-   <xref:System.IO.File> – poskytuje statické metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá vytvářet <xref:System.IO.FileStream> objektu.  
  
-   <xref:System.IO.FileInfo> – poskytuje instanční metody pro vytváření, kopírování, odstraňování, přesouvání a otevírání souborů a pomáhá vytvářet <xref:System.IO.FileStream> objektu.  
  
-   <xref:System.IO.Directory> – poskytuje statické metody pro vytváření, přesouvání a vytváření výčtů adresářů a podadresářů.  
  
-   <xref:System.IO.DirectoryInfo> – poskytuje instanční metody pro vytváření, přesouvání a vytváření výčtů adresářů a podadresářů.  
  
-   <xref:System.IO.Path> – poskytuje metody a vlastnosti pro zpracování řetězců adresářů způsobem napříč platformami.  
  
 Vždy byste měli poskytnout robustní zpracování při volání metody systému souborů výjimek. Další informace najdete v tématu [vstupně-výstupních operací zpracování chyb](handling-io-errors.md).
 
 Kromě použití těchto tříd, uživatelé jazyka Visual Basic můžete použít metody a vlastnosti poskytované třídou <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> třídy pro soubor vstupně-výstupních operací.  
  
 Naleznete v tématu [postupy: kopírování adresářů](../../../docs/standard/io/how-to-copy-directories.md), [jak: Create a Directory Listing](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), a [postupy: vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Datové proudy  
 Abstraktní základní třída <xref:System.IO.Stream> podporuje čtení a zápis bajtů. Dědí všechny třídy, které představují datové proudy <xref:System.IO.Stream> třídy. <xref:System.IO.Stream> Třída a odvozené třídy poskytují běžné zobrazení datových zdrojů a úložišť a izolují programátora od konkrétních podrobností operačního systému a použitých zařízení.  
  
 Datové proudy zahrnují tři základní operace:  
  
-   Čtení – přenos dat z datového proudu do datové struktury, například pole bajtů.  
  
-   Zápis – přenos dat ze zdroje dat do datového proudu.  
  
-   Hledání – dotazování a úprava současné pozice v datovém proudu.  
  
 Datový proud může podporovat pouze některé z těchto možností v závislosti na použitém zdroji dat nebo úložišti. Například <xref:System.IO.Pipes.PipeStream> třída nepodporuje vyhledávání. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, A <xref:System.IO.Stream.CanSeek%2A> vlastnosti datového proudu určují operace, které podporuje datového proudu.  
  
 Toto jsou některé běžně používané třídy datového proudu:  
  
-   <xref:System.IO.FileStream> – pro čtení a zápis do souboru.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – pro čtení a zápis do souboru v izolovaném úložišti.  
  
-   <xref:System.IO.MemoryStream> – pro čtení a zápis do paměti jako záložního úložiště.  
  
-   <xref:System.IO.BufferedStream> – pro zvýšení výkonu pro čtení a zápisu operace.  
  
-   <xref:System.Net.Sockets.NetworkStream> – pro čtení a zápis přes síťové sokety.  
  
-   <xref:System.IO.Pipes.PipeStream> – pro čtení a zápis přes anonymní a pojmenované kanály.  
  
-   <xref:System.Security.Cryptography.CryptoStream> – pro propojení datových proudů na kryptografické transformace.  
  
 Příklad asynchronní práce s datovými proudy naleznete v tématu [asynchronní vstupně-výstupní operace souboru](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Čtečky a zapisovače  
 <xref:System.IO?displayProperty=nameWithType> Názvů také obsahuje typy pro čtení kódovaných znaků z datových proudů a jejich zápis do datových proudů. Datové proudy jsou obvykle navrženy pro bajtový vstup a výstup. Typy čtečky a zapisovače zajišťují převod kódovaných znaků na bajty a zpět, aby datový proud mohl dokončit operaci. Každá třída čtečky nebo zapisovače je přidružena k datovému proudu, které se dají získat pomocí třídy `BaseStream` vlastnost.  
  
 Toto jsou některé běžně používané třídy čteček a zapisovačů:  
  
-   <xref:System.IO.BinaryReader> a <xref:System.IO.BinaryWriter> – pro čtení a zápis primitivních datových typů jako binárních hodnot.  
  
-   <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> – pro čtení a zápis znaků pomocí kódovací hodnoty pro převod znaků do a z bajtů.  
  
-   <xref:System.IO.StringReader> a <xref:System.IO.StringWriter> – pro čtení a zápis znaků do a z řetězce.  
  
-   <xref:System.IO.TextReader> a <xref:System.IO.TextWriter> – slouží jako abstraktní základní třída pro jiné čtečky a zapisovače, které čtou a zapisují znaky a řetězce, ale nikoli binární data.  
  
 Naleznete v tématu [postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md), [postupy: zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md), [postupy: čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md), a [postupy: zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Asynchronní vstupně-výstupní operace  
 Čtení a zápis velkého množství dat může zatěžovat prostředky. Má-li aplikace nadále reagovat na uživatele, je zapotřebí tyto úkoly provádět asynchronně. Při synchronních vstupně-výstupních operacích je vlákno uživatelského rozhraní zablokováno, dokud není operace náročná na prostředky dokončena.  Použít asynchronní vstupně-výstupní operace při vývoji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacím zabránit dojmu, že vaše aplikace přestala fungovat.  
  
 Asynchronní členy obsahují `Async` v jejich názvy, například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> metody. Používejte tyto metody s `async` a `await` klíčová slova.  
  
 Další informace najdete v tématu [asynchronní vstupně-výstupní operace souboru](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Komprese  
 Kompresí se rozumí proces zmenšení velikosti ukládaného souboru. Dekomprese je proces extrahování obsahu komprimovaného souboru do použitelného formátu. <xref:System.IO.Compression?displayProperty=nameWithType> Obor názvů obsahuje typy pro kompresi a dekompresi souborů a datových proudů.  
  
 Následující třídy jsou při kompresi a dekompresi souborů a datových proudů často používány:  
  
-   <xref:System.IO.Compression.ZipArchive> – pro vytváření a získávání záznamů v archívu zip.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> – pro reprezentaci komprimovaného souboru.  
  
-   <xref:System.IO.Compression.ZipFile> – pro vytváření, extrahování a otevírání komprimovaného balíku.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> – pro vytváření a extrahování záznamů v komprimovaném balíku.  
  
-   <xref:System.IO.Compression.DeflateStream> – pro kompresi a dekompresi datových proudů algoritmem Deflate.  
  
-   <xref:System.IO.Compression.GZipStream> – pro kompresi a dekompresi datových proudů v datovém formátu gzip.  
  
 Zobrazit [postupy: komprimování a extrahování souborů](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Izolované úložiště  
 Izolované úložiště je mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty. Úložiště poskytuje virtuální systém souborů izolovaný uživatelem, sestavením a (volitelně) doménou. Izolované úložiště je obzvláště užitečné, nemá-li aplikace oprávnění k přístupu k uživatelským souborům. Lze tak ukládat nastavení nebo soubory aplikace způsobem řízeným zásadami zabezpečení daného počítače.  
  
 Izolované úložiště není k dispozici pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace; místo toho použít třídy aplikačních dat v [Windows.Storage](/uwp/api/Windows.Storage) oboru názvů. Další informace najdete v tématu [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) Windows Dev Center.  
  
 Při implementaci izolovaného úložiště jsou běžně používány následující třídy:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> – poskytuje základní třídu pro implementace izolovaného úložiště.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – poskytuje oblast izolovaného úložiště, který obsahuje soubory a adresáře.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – zpřístupňuje soubor uvnitř izolovaného úložiště.  
  
 Zobrazit [izolované úložiště](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Vstupně-výstupní operace v aplikacích pro Windows Store  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Obsahuje celou řadu typů pro čtení a zápis datových proudů, ale tato sada neobsahuje všechny typy rozhraní .NET Framework vstupně-výstupních operací.  
  
 Některé důležité rozdíly při používání vstupně-výstupních operací v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace:  
  
-   Typy výslovně související s operacemi se soubory, jako například <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> a <xref:System.IO.DirectoryInfo>, nejsou součástí [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Místo toho použít typy v [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) obor názvů [!INCLUDE[wrt](../../../includes/wrt-md.md)], jako například [StorageFile](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) a [StorageFolder](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Izolované úložiště není k dispozici. Místo toho použijte [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Použití asynchronních metod, jako například <xref:System.IO.Stream.ReadAsync%2A> a <xref:System.IO.Stream.WriteAsync%2A>, chcete-li zabránit zablokování vlákna uživatelského rozhraní.  
  
-   Na základě cest kompresní typy <xref:System.IO.Compression.ZipFile> a <xref:System.IO.Compression.ZipFileExtensions> nejsou k dispozici. Místo toho použít typy v [Windows.Storage.Compression](https://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) oboru názvů.  
  
 V případě potřeby je možné převádět mezi proudy rozhraní .NET Framework a proudy Windows Runtime. Další informace najdete v tématu [postupy: převod mezi streamy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) nebo [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 Další informace o vstupně-výstupních operací v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v článku [rychlý start: čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>Vstupně-výstupní operace a zabezpečení  
 Při použití třídy v <xref:System.IO?displayProperty=nameWithType> obor názvů, je třeba dodržovat požadavky zabezpečení operačního systému jako je například seznamy řízení přístupu (ACL) pro řízení přístupu k souborům a adresářům. Tento požadavek je <xref:System.Security.Permissions.FileIOPermission> požadavky. Seznamy ACL lze spravovat programově. Další informace najdete v tématu [postupy: přidávání a odebírání položek seznamu řízení přístupu](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Výchozí zásady zabezpečení zabraňují internetovým a intranetovým aplikacím v přístupu k souborům na počítači uživatele. Proto při psaní kódu, který bude stažen přes internet nebo intranet, nepoužívejte vstupně-výstupní třídy požadující cestu k fyzickému souboru. Místo toho použijte [izolované úložiště](../../../docs/standard/io/isolated-storage.md) pro tradiční aplikace rozhraní .NET Framework, nebo použijte [data aplikací](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 Kontrola zabezpečení se provádí pouze při konstrukci datového proudu. Proto neotevírejte datový proud a poté jej nepředávejte méně důvěryhodnému kódu nebo doménám aplikace.  
  
## <a name="related-topics"></a>Související témata  
  
-   [Obecné vstupně-výstupní úlohy](../../../docs/standard/io/common-i-o-tasks.md)  
  
 Poskytuje seznam vstupně-výstupních úkolů přidružených k souborům, adresářům a datovým proudům a odkazuje pro každý úkol na relevantní obsah a příklady.  
  
-   [Asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 Popisuje výhody výkonu a základní operace asynchronních vstupně-výstupních operací.  
  
-   [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
  
 Popisuje mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty.  
  
-   [Pojmenované kanály](../../../docs/standard/io/pipe-operations.md)  
  
 Popisuje operace anonymních a pojmenovaných kanálů v rozhraní .NET Framework.  
  
-   [Soubory mapované paměti](../../../docs/standard/io/memory-mapped-files.md)  
  
 Popisuje soubory mapované paměti, které obsahují obsah souborů na disku ve virtuální paměti. Soubory mapované paměti lze použít k úpravě velmi velkých souborů a k vytváření sdílené paměti pro komunikaci mezi procesy.
