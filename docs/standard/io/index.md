---
title: Souborová služba a datový proud I-O
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
caps.latest.revision: 33
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b420859380d7c3c39a7d85f94df1708d9f26bebc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="file-and-stream-io"></a>I/O souborů a proudů
Vstupem/výstupem souborů a datových proudů se rozumí přenos dat z úložného média nebo na něj. V rozhraní .NET Framework `System.IO` obory názvů obsahují typy, které umožňují čtení a zápis, synchronně i asynchronně, na datové proudy a souborů. Tyto obory názvů obsahují také typy provádějící kompresi a dekompresi souborů a typy umožňující komunikaci pomocí kanálů a sériových portů.  
  
 Soubor je uspořádaná a pojmenovaná kolekce bajtů s trvalým úložištěm. Pracujete-li se soubory, pracujete s cestami adresářů, diskovým úložištěm a názvy souborů a adresářů. Naproti tomu datový proud je posloupnost bajtů, kterou lze použít ke čtení nebo zápisu na záložní úložiště, jímž může být jedno nebo více úložných médií (například disky nebo paměť). Stejně jako existuje několik záložních úložišť jiných než disky, existuje několik druhů datových proudů jiných než datové proudy souborů, například proudy sítí, pamětí nebo kanálů.  
  
## <a name="files-and-directories"></a>Soubory a adresáře  
 Můžete použít typy v <xref:System.IO?displayProperty=nameWithType> obor názvů pro interakci s souborů a adresářů. Lze tak například načíst nebo nastavit vlastnosti souborů a adresářů nebo načíst kolekce souborů a adresářů na základě kritérií vyhledávání.  
  
 Zde jsou některé běžně používané třídy souborů a adresářů:  
  
-   <xref:System.IO.File> -poskytuje statické metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a vám pomůže vytvořit <xref:System.IO.FileStream> objektu.  
  
-   <xref:System.IO.FileInfo> -poskytuje instance metody pro vytvoření, kopírování, odstranění, přesunutí a otevírání souborů a vám pomůže vytvořit <xref:System.IO.FileStream> objektu.  
  
-   <xref:System.IO.Directory> -poskytuje statické metody pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.  
  
-   <xref:System.IO.DirectoryInfo> -poskytuje instance metody pro vytváření, přesunutí a výčet prostřednictvím adresářů a podadresářů.  
  
-   <xref:System.IO.Path> -poskytuje metody a vlastnosti pro zpracování řetězců adresářů způsobem napříč platformami.  
  
 Kromě použití těchto tříd, uživatelé jazyka Visual Basic můžete použít metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> třídu pro vstupně-výstupní.  
  
 Najdete v části [postupy: kopírování adresářů](../../../docs/standard/io/how-to-copy-directories.md), [postupy: vytvoření adresářů](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), a [postupy: výčet adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Datové proudy  
 Abstraktní základní třída <xref:System.IO.Stream> podporuje čtení a zápisu bajtů. Dědí všechny třídy, které představují datové proudy <xref:System.IO.Stream> třídy. <xref:System.IO.Stream> Třídy a jejich odvozené třídy poskytují běžné zobrazení zdroje dat a úložiště a izolovat programátorů z konkrétní podrobnosti základní zařízení a operační systém.  
  
 Datové proudy zahrnují tři základní operace:  
  
-   Čtení – přenos dat z datového proudu do datové struktury, například pole bajtů.  
  
-   Zápis – přenos dat ze zdroje dat do datového proudu.  
  
-   Hledání – dotazování a úprava současné pozice v datovém proudu.  
  
 Datový proud může podporovat pouze některé z těchto možností v závislosti na použitém zdroji dat nebo úložišti. Například <xref:System.IO.Pipes.PipeStream> třída nepodporuje vyhledávání. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, A <xref:System.IO.Stream.CanSeek%2A> vlastnosti datového proudu zadejte operace, které podporuje datového proudu.  
  
 Toto jsou některé běžně používané třídy datového proudu:  
  
-   <xref:System.IO.FileStream> – pro čtení a zápis do souboru.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – pro čtení a zápis do souboru v izolovaném úložišti.  
  
-   <xref:System.IO.MemoryStream> – pro čtení a zápis do paměti jako úložiště zálohování.  
  
-   <xref:System.IO.BufferedStream> – pro zlepšení výkonu pro čtení a zápisu operace.  
  
-   <xref:System.Net.Sockets.NetworkStream> – pro čtení a zápis prostřednictvím sítě soketů.  
  
-   <xref:System.IO.Pipes.PipeStream> – pro čtení a zápis přes anonymní a pojmenované kanály.  
  
-   <xref:System.Security.Cryptography.CryptoStream> – pro propojení datové proudy kryptografické transformace.  
  
 Příklad práce s datovými proudy asynchronně, naleznete v části [asynchronní vstup-výstup souboru](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Čtečky a zapisovače  
 <xref:System.IO?displayProperty=nameWithType> Názvů také obsahuje typy pro čtení kódování znaků z proudů a jejich zápis do datových proudů. Datové proudy jsou obvykle navrženy pro bajtový vstup a výstup. Typy čtečky a zapisovače zajišťují převod kódovaných znaků na bajty a zpět, aby datový proud mohl dokončit operaci. Každá třída čtení a zápis je přidružen datový proud, který se dají získat pomocí metody třídy `BaseStream` vlastnost.  
  
 Toto jsou některé běžně používané třídy čteček a zapisovačů:  
  
-   <xref:System.IO.BinaryReader> a <xref:System.IO.BinaryWriter> – pro čtení a zápis primitivní datové typy jako binární hodnoty.  
  
-   <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter> – pro čtení a zápis znaků pomocí kódování hodnotu převést znaky na a z bajtů.  
  
-   <xref:System.IO.StringReader> a <xref:System.IO.StringWriter> – pro čtení a zápis znaků do a z řetězců.  
  
-   <xref:System.IO.TextReader> a <xref:System.IO.TextWriter> – sloužit jako abstraktní základní třídy pro další čtení a zápis, které pro čtení a zápis znaky a řetězce, ale není binární data.  
  
 V tématu [postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md), [postupy: zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md), [postupy: čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md), a [postupy: zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Asynchronní vstupně-výstupní operace  
 Čtení a zápis velkého množství dat může zatěžovat prostředky. Má-li aplikace nadále reagovat na uživatele, je zapotřebí tyto úkoly provádět asynchronně. Při synchronních vstupně-výstupních operacích je vlákno uživatelského rozhraní zablokováno, dokud není operace náročná na prostředky dokončena.  Použít asynchronní vstupně-výstupních operací při vývoji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, aby se zabránilo vytváření dojem, že aplikace přestane fungovat.  
  
 Asynchronní členy obsahovat `Async` v jejich názvy, například <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, a <xref:System.IO.Stream.WriteAsync%2A> metody. Pomocí těchto metod s `async` a `await` klíčová slova.  
  
 Další informace najdete v tématu [asynchronní vstup-výstup souboru](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Komprese  
 Kompresí se rozumí proces zmenšení velikosti ukládaného souboru. Dekomprese je proces extrahování obsahu komprimovaného souboru do použitelného formátu. <xref:System.IO.Compression?displayProperty=nameWithType> Obor názvů obsahuje typy pro kompresi a dekompresi soubory a proudy.  
  
 Následující třídy jsou při kompresi a dekompresi souborů a datových proudů často používány:  
  
-   <xref:System.IO.Compression.ZipArchive> – pro vytváření a načítání položek v archivu zip.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> – pro představující komprimovaný soubor.  
  
-   <xref:System.IO.Compression.ZipFile> – pro vytváření, extrahování a otevírání zkomprimovaného balíčku.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> – pro vytváření a extrahování položky v zkomprimovaného balíčku.  
  
-   <xref:System.IO.Compression.DeflateStream> – pro kompresi a dekompresi datových proudů pomocí algoritmu Deflate.  
  
-   <xref:System.IO.Compression.GZipStream> – pro kompresi a dekompresi datových proudů ve formátu gzip data.  
  
 V tématu [postupy: komprimování a extrahování souborů](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Izolované úložiště  
 Izolované úložiště je mechanismus pro ukládání dat poskytující izolaci a bezpečnost definováním standardizovaných způsobů asociace kódu s uloženými daty. Úložiště poskytuje virtuální systém souborů izolovaný uživatelem, sestavením a (volitelně) doménou. Izolované úložiště je obzvláště užitečné, nemá-li aplikace oprávnění k přístupu k uživatelským souborům. Lze tak ukládat nastavení nebo soubory aplikace způsobem řízeným zásadami zabezpečení daného počítače.  
  
 Izolované úložiště není k dispozici pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace; místo toho použijte aplikaci datové třídy v [Windows.Storage](/uwp/api/Windows.Storage) oboru názvů. Další informace najdete v tématu [data aplikací](/previous-versions/windows/apps/hh464917(v=win.10)) ve službě Windows Dev Center.  
  
 Při implementaci izolovaného úložiště jsou běžně používány následující třídy:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> – poskytuje základní třídu pro implementace izolovaného úložiště.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – poskytuje oblast izolovaného úložiště, který obsahuje soubory a adresáře.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> -zveřejňuje soubor v izolovaném úložišti.  
  
 V tématu [izolované úložiště](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Vstupně-výstupní operace v aplikacích pro Windows Store  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Obsahuje mnoho typů pro čtení a zápis do datových proudů; však tato sada neobsahuje všechny typy rozhraní .NET Framework vstupně-výstupních operací.  
  
 Několik důležitých rozdílů si uvědomit, při použití vstupně-výstupních operací v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace:  
  
-   Typy související s operací se soubory, jako například <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> a <xref:System.IO.DirectoryInfo>, nejsou součástí [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Místo toho použít typy v [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) obor názvů [!INCLUDE[wrt](../../../includes/wrt-md.md)], jako například [StorageFile](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) a [StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Izolované úložiště není k dispozici. Místo toho použijte [data aplikací](/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Použít asynchronní metody, jako například <xref:System.IO.Stream.ReadAsync%2A> a <xref:System.IO.Stream.WriteAsync%2A>, aby se zabránilo blokování vlákna uživatelského rozhraní.  
  
-   Typy na základě cesty komprese <xref:System.IO.Compression.ZipFile> a <xref:System.IO.Compression.ZipFileExtensions> nejsou k dispozici. Místo toho použít typy v [Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) oboru názvů.  
  
 V případě potřeby je možné převádět mezi proudy rozhraní .NET Framework a proudy Windows Runtime. Další informace najdete v tématu [postupy: převod mezi rozhraní .NET Framework datové proudy a datové proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) nebo [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 Další informace o vstupně-výstupních operací v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, najdete v části [rychlý start: čtení a zápis souborů](/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>Vstupně-výstupní operace a zabezpečení  
 Při použití třídy v <xref:System.IO?displayProperty=nameWithType> obor názvů, je třeba postupovat podle požadavky na zabezpečení operačního systému jako seznamy řízení přístupu (ACL) pro řízení přístupu k souborů a adresářů. Tento požadavek je kromě žádné <xref:System.Security.Permissions.FileIOPermission> požadavky. Seznamy ACL lze spravovat programově. Další informace najdete v tématu [postupy: Přidání nebo odebrání položek seznamu řízení přístupu](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Výchozí zásady zabezpečení zabraňují internetovým a intranetovým aplikacím v přístupu k souborům na počítači uživatele. Proto při psaní kódu, který bude stažen přes internet nebo intranet, nepoužívejte vstupně-výstupní třídy požadující cestu k fyzickému souboru. Místo toho použijte [izolované úložiště](../../../docs/standard/io/isolated-storage.md) pro tradiční aplikací rozhraní .NET Framework, nebo použijte [data aplikací](/previous-versions/windows/apps/hh464917(v=win.10)) pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
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
