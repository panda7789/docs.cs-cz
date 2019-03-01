---
title: Začínáme s Azure File storage pomocíF#
description: Store souborová data v cloudu s Azure File storage a připojte svou cloudovou sdílenou z virtuálního počítače Azure (VM) nebo z aplikace v místním systémem Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fa6dadc863bb9116cfac5afd7cd22a724bc7afe2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969593"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Začínáme s Azure File storage s využitím F\#

Azure File storage je služba, která nabízí sdílené složky v cloudu s využitím standardu [zprávy bloku SMB (Server) protokol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Podporují se SMB 2.1 i SMB 3.0. S Azure File Storage můžete rychle a bez nákladných přepisů migrovat starší aplikace, které spoléhají na sdílené složky, do Azure. Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo spuštěné z lokálních klientů můžou připojit sdílenou složku v cloudu stejným způsobem, jako desktopová aplikace připojí typickou sdílenou složku SMB. Potom může sdílenou složku File Storage připojit a používat libovolný počet aplikací.

Koncepční přehled služby file storage, najdete v tématu [v příručce .NET pro službu file storage](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Požadavky

K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account).
Budete také potřebovat přístupový klíč k úložišti pro tento účet.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skript a spustit F# interaktivní

Ukázky v tomto článku můžete použít buď F# aplikace nebo F# skriptu. Vytvoření F# skript, vytvořte soubor s `.fsx` příponu, třeba `files.fsx`v vaše F# vývojové prostředí.

Pak pomocí [Správce balíčků](package-management.md) jako [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a odkaz na `WindowsAzure.Storage.dll` ve skriptu pomocí `#r`směrnice.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte následující `open` příkazy k hornímu okraji `files.fsx` souboru:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro účely tohoto kurzu budete potřebovat připojovací řetězec služby Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).

Pro tento kurz zadáte svůj připojovací řetězec ve vašem skriptu, například takto:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Je to ale **ale nedoporučený krok** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.

Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce, použijte:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Vrátí `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Vytvoření klienta služby souborů

`CloudFileClient` Typ umožňuje programově pomocí souborů uložených ve službě File storage. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do služby File storage.

## <a name="create-a-file-share"></a>Vytvoření sdílené složky

Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Vytvoření kořenového adresáře a podadresáře

Tady získáte do kořenového adresáře a podadresáře kořenové. Můžete vytvořit oba, pokud ještě neexistují.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Uložit text do souboru

Tento příklad ukazuje, jak nahrát text do souboru.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Stáhnout soubor do místní kopii souboru

Tady si stáhnout soubor právě vytvořili, přidávání obsahu do místního souboru.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Nastavení maximální velikosti sdílené složky

Následující příklad ukazuje, jak zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku. `FetchAttributes` k naplnění sdílené složky se musí volat `Properties`, a `SetProperties` místní změny do služby Azure File storage.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílenou složku

Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo konkrétní soubor. Můžete také vytvořit zásady sdíleného přístupu ve sdílené složce ke správě sdílených přístupových podpisů. Vytvoření zásad sdíleného přístupu se doporučuje, protože se tím nabízí způsob odvolání SAS v případě narušení jeho integrity.

Tady vytvoříte sdílené zásady ve sdílené složce přístup a pak tuto zásadu použít k omezení pro SAS na souboru ve sdílené složce.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Další informace o vytváření a používání sdílených přístupových podpisů najdete v tématu [použití sdílených přístupových podpisů (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [vytvoření a použití SAS s úložištěm objektů Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopírování souborů

Soubor můžete zkopírovat do jiného souboru nebo do objektu blob nebo objekt blob do souboru. Pokud kopírujete objekt blob do souboru nebo souboru do objektu blob, které *musí* pomocí sdíleného přístupového podpisu (SAS) k ověření zdroje objektu, i když kopírujete v rámci stejného účtu úložiště.

### <a name="copy-a-file-to-another-file"></a>Kopírování souboru do jiného souboru

Tady zkopírujte soubor do jiného souboru ve stejné sdílené složce. Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete použít ověření sdíleným klíčem ke kopírování.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopírování souboru do objektu blob

Tady vytvoříte soubor a zkopírujte ho do objektu blob ve stejném účtu úložiště. Vytvoření SAS pro zdrojový soubor, který službu používá k ověření přístupu ke zdrojovému souboru během operace kopírování.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Stejným způsobem můžete kopírovat objekt blob do souboru. Pokud zdrojový objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob během operace kopírování.

## <a name="troubleshooting-file-storage-using-metrics"></a>Řešení potíží s úložištěm File pomocí metrik

Azure Storage Analytics podporuje metriky pro File storage. S údaji z metriky můžete sledovat žádosti a diagnostikovat problémy.

Metriky pro File storage můžete povolit [webu Azure Portal](https://portal.azure.com), nebo to můžete provést z F# tímto způsobem:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Další kroky

Naleznete pod následujícími odkazy pro další informace o službě Azure File storage.

### <a name="conceptual-articles-and-videos"></a>Koncepční články a videa

- [Azure Files Storage: hladký cloudový systém souborů protokolu SMB pro Windows a Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak používat Azure File Storage s Linuxem](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Podpora nástrojů pro File storage

- [Použití Azure Powershellu s Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Použití nástroje AzCopy s Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Použití Azure CLI s Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Odkaz

- [Klientská knihovna Storage pro .NET – referenční informace](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Odkaz na soubor rozhraní REST API služby](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blogové příspěvky

- [Azure File storage je teď obecně dostupná](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Uvnitř Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Představujeme službu Microsoft Azure File](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Nastavení trvalých připojení k Microsoft Azure Files](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
