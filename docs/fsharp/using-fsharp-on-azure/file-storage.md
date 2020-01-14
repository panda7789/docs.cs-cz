---
title: Začínáme se službou Azure File Storage s využitím F#
description: Ukládejte data souborů do cloudu pomocí Azure File Storage a připojte svou cloudovou sdílenou složku z virtuálního počítače Azure nebo z lokální aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: d58417e1e3161b958754e01423136a9cdd6a08a6
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935618"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Začínáme se službou Azure File Storage s využitím F\#

Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [protokol SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Podporují se SMB 2.1 i SMB 3.0. S Azure File Storage můžete rychle a bez nákladných přepisů migrovat starší aplikace, které spoléhají na sdílené složky, do Azure. Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo spuštěné z lokálních klientů můžou připojit sdílenou složku v cloudu stejným způsobem, jako desktopová aplikace připojí typickou sdílenou složku SMB. Potom může sdílenou složku File Storage připojit a používat libovolný počet aplikací.

Koncepční přehled služby File Storage najdete v [příručce .NET pro File Storage](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Pro tento účet budete taky potřebovat přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `files.fsx`ve vašem F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve vašem skriptu pomocí direktivy `#r`.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte do horní části souboru `files.fsx` následující příkazy `open`:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz budete potřebovat připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte svůj připojovací řetězec, například:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Tato akce vrátí `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Vytvoření klienta souborové služby

Typ `CloudFileClient` umožňuje programově používat soubory uložené v úložišti souborů. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do úložiště souborů.

## <a name="create-a-file-share"></a>Vytvoření sdílené složky

Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Vytvoření kořenového adresáře a podadresáře

Tady získáte kořenový adresář a získáte podadresáře kořenové složky. Pokud ještě neexistují, vytvořte je.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Odeslat text jako soubor

Tento příklad ukazuje, jak nahrát text jako soubor.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Stažení souboru do místní kopie souboru

Zde si můžete stáhnout soubor, který jste právě vytvořili, a připojit obsah k místnímu souboru.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Nastavení maximální velikosti sdílené složky

Dole uvedený příklad ukazuje, jak můžete zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku. aby bylo možné naplnit `Properties`sdílené složky a `SetProperties` rozšířit místní změny do služby Azure File Storage, je třeba volat `FetchAttributes`.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílenou složku

Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro jednotlivé soubory. Můžete taky vytvořit sdílené zásady přístupu pro sdílenou složku ke správě sdílených přístupových podpisů. Vytvoření sdílených zásad přístupu se doporučuje, protože se tím nabízí způsob odvolání SAS v případě narušení jeho integrity nebo důvěryhodnosti.

Tady vytvoříte zásadu sdíleného přístupu pro sdílenou složku a potom pomocí této zásady zadáte omezení pro SAS k souboru ve sdílené složce.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Další informace o vytváření a používání sdílených přístupových podpisů najdete v tématech [Použití sdílených přístupových podpisů (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [Vytvoření a použití SAS se službou Blob Storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopírování souborů

Soubor můžete zkopírovat do jiného souboru nebo do objektu BLOB nebo objektu blob do souboru. Pokud kopírujete objekt blob do souboru nebo soubor do objektu blob, *musíte* k ověření zdrojového objektu použít sdílený přístupový podpis (SAS), a to i v případě, že provádíte kopírování v rámci stejného účtu úložiště.

### <a name="copy-a-file-to-another-file"></a>Kopírování souboru do jiného souboru

Sem zkopírujete soubor do jiného souboru ve stejné sdílené složce. Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření Sdíleným klíčem.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopírování souboru do objektu blob

Tady vytvoříte soubor a zkopírujete ho do objektu BLOB ve stejném účtu úložiště. Vytvoříte SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Stejným způsobem můžete kopírovat objekt blob do souboru. Pokud je zdrojovým objektem objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.

## <a name="troubleshooting-file-storage-using-metrics"></a>Řešení problémů s úložištěm File pomocí metrik

Analýza úložiště Azure podporuje metriky pro úložiště souborů. S údaji z metriky můžete sledovat žádosti a diagnostikovat potíže.

Metriky pro službu File Storage můžete povolit na webu [Azure Portal](https://portal.azure.com), nebo můžete to udělat F# takto:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Další kroky

Další informace o úložišti Azure File jsou dostupné na těchto odkazech.

### <a name="conceptual-articles-and-videos"></a>Koncepční články a videa

- [Azure Files Storage: hladký cloudový souborový systém SMB pro Windows a Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Používání Azure File Storage s Linuxem](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Podpora nástrojů pro úložiště File

- [Použití Azure Powershell s Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Použití nástroje AzCopy s Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Použití Azure CLI s Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Odkaz

- [Klientská knihovna Storage pro .NET – referenční informace](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [REST API služby File – referenční informace](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blogové příspěvky

- [Úložiště Azure File je nyní dostupné pro veřejnost](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Uvnitř Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Představujeme službu Microsoft Azure File](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Nastavení trvalých připojení k Microsoft Azure Files](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
