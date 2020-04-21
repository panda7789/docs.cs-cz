---
title: Začínáme se službou Azure File Storage s využitím F#
description: Ukládejte data souborů do cloudu pomocí Azure File Storage a připojte svou cloudovou sdílenou složku z virtuálního počítače Azure nebo z lokální aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739589"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Začínáme s úložištěm souborů Azure pomocí F\#

Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [protokol SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Podporují se SMB 2.1 i SMB 3.0. S Azure File Storage můžete rychle a bez nákladných přepisů migrovat starší aplikace, které spoléhají na sdílené složky, do Azure. Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo spuštěné z lokálních klientů můžou připojit sdílenou složku v cloudu stejným způsobem, jako desktopová aplikace připojí typickou sdílenou složku SMB. Potom může sdílenou složku File Storage připojit a používat libovolný počet aplikací.

Koncepční přehled úložiště souborů naleznete [v průvodci .NET pro ukládání souborů](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Požadavky

Chcete-li použít tuto [příručku,](https://docs.microsoft.com/azure/storage/storage-create-storage-account)musíte nejprve vytvořit účet úložiště Azure .
Budete také potřebovat přístupový klíč úložiště pro tento účet.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření skriptu Jazyka F# a interaktivního spuštění jazyka F#

Ukázky v tomto článku lze použít v aplikaci F# nebo skript F#. Chcete-li vytvořit skript F#, `.fsx` vytvořte soubor `files.fsx`s příponou, například ve vývojovém prostředí F#.

Dále použijte [správce balíčků,](package-management.md) jako je [Paket](https://fsprojects.github.io/Paket/) `WindowsAzure.Storage` nebo [NuGet](https://www.nuget.org/) k instalaci `#r` balíčku a odkaz `WindowsAzure.Storage.dll` ve skriptu pomocí směrnice.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte do horní části souboru `files.fsx` následující příkazy `open`:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Budete potřebovat připojovací řetězec Azure Storage pro tento kurz. Další informace o připojovacích řetězcích naleznete v [tématu Konfigurace připojovacích řetězců úložiště](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).

Pro účely kurzu zadáte připojovací řetězec do skriptu takto:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

To se však **nedoporučuje** u skutečných projektů. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí portálu Azure, pokud se domníváte, že byl ohrožen.

Pro skutečné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést takto:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je `ConfigurationManager` například typ rozhraní .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

Chcete-li analyzovat připojovací řetězec, použijte:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Tím se `CloudStorageAccount`vrátí .

### <a name="create-the-file-service-client"></a>Vytvoření klienta služby Soubor

Tento `CloudFileClient` typ umožňuje programově používat soubory uložené v úložišti souborů. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Nyní jste připraveni k zápisu kódu, ze kterého jsou čtena data a zapisují data do úložiště souborů.

## <a name="create-a-file-share"></a>Vytvoření sdílené složky

Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Vytvoření kořenového adresáře a podadresáře

Zde získáte kořenový adresář a získat podadresář kořenového adresáře. Můžete vytvořit obojí, pokud již neexistují.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Nahrání textu jako souboru

Tento příklad ukazuje, jak nahrát text jako soubor.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Stažení souboru do místní kopie souboru

Zde si stáhnete právě vytvořený soubor a připojíte obsah k místnímu souboru.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Nastavení maximální velikosti sdílené složky

Dole uvedený příklad ukazuje, jak můžete zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku. `FetchAttributes`musí být volána k `Properties`naplnění `SetProperties` sdílené složky a k šíření místních změn v úložišti souborů Azure.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílenou složku

Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro jednotlivé soubory. Můžete taky vytvořit sdílené zásady přístupu pro sdílenou složku ke správě sdílených přístupových podpisů. Vytvoření sdílených zásad přístupu se doporučuje, protože se tím nabízí způsob odvolání SAS v případě narušení jeho integrity nebo důvěryhodnosti.

Zde vytvoříte zásady sdíleného přístupu ve sdílené složce a pak tuto zásadu použijete k poskytnutí omezení pro SAS v souboru ve sdílené složce.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Další informace o vytváření a používání sdílených přístupových podpisů najdete v tématech [Použití sdílených přístupových podpisů (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) a [Vytvoření a použití SAS se službou Blob Storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopírování souborů

Soubor můžete zkopírovat do jiného souboru nebo do objektu blob nebo do objektu blob do souboru. Pokud kopírujete objekt blob do souboru nebo soubor do objektu blob, *musíte* k ověření zdrojového objektu použít sdílený přístupový podpis (SAS), a to i v případě, že kopírujete v rámci stejného účtu úložiště.

### <a name="copy-a-file-to-another-file"></a>Kopírování souboru do jiného souboru

Zde zkopírujete soubor do jiného souboru ve stejné sdílené složce. Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření Sdíleným klíčem.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopírování souboru do objektu blob

Zde vytvoříte soubor a zkopírujete ho do objektu blob ve stejném účtu úložiště. Vytvoříte SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Stejným způsobem můžete kopírovat objekt blob do souboru. Pokud je zdrojovým objektem objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.

## <a name="troubleshooting-file-storage-using-metrics"></a>Řešení problémů s úložištěm File pomocí metrik

Azure Storage Analytics podporuje metriky pro úložiště souborů. S údaji z metriky můžete sledovat žádosti a diagnostikovat potíže.

Metriky úložiště souborů můžete povolit z [webu Azure Portal](https://portal.azure.com), nebo to můžete udělat z F#, takto:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Další kroky

Další informace o úložišti souborů Azure najdete v těchto odkazech.

### <a name="conceptual-articles-and-videos"></a>Koncepční články a videa

- [Azure Files Storage: hladký cloudový souborový systém SMB pro Windows a Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak používat Azure File Storage s Linuxem](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Podpora nástrojů pro úložiště File

- [Použití Azure Powershell s Azure Storage](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [Použití nástroje AzCopy s Microsoft Azure Storage](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [Vytváření, stahování a vytváření objektů BLOB s rozhraním příkazového příkazového příkazu Azure](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>Odkaz

- [Klientská knihovna úložiště pro odkaz .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [REST API služby File – referenční informace](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Příspěvky na blozích

- [Úložiště Azure File je nyní dostupné pro veřejnost](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Uvnitř Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Představujeme službu Microsoft Azure File](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Nastavení trvalých připojení k Microsoft Azure Files](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
