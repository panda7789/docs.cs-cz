---
title: 'Začínáme s Azure File storage pomocí F #'
description: Ukládejte data souborů v cloudu s Azure File storage a připojte svou cloudovou sdílenou z Azure virtuálního počítače (VM) nebo z lokální aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Začínáme s Azure File storage pomocí F # #

Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [zpráva bloku protokol Server (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Podporuje SMB 2.1 i protokol SMB 3.0. S Azure File storage můžete migrovat starší aplikace, které spoléhají na sdílené složky Azure rychle a bez nákladných přepisů. Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo z lokálních klientů můžou připojit sdílenou složku v cloudu, stejně, jako desktopová aplikace připojí typickou sdílenou složku SMB. Libovolný počet součásti aplikace lze připojit a současně získat přístup ke sdílené složce úložiště.

Koncepční přehled úložiště file, najdete v tématu [v příručce .NET pro úložiště file](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Požadavky

Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Budete také potřebovat přístupový klíč k úložišti pro tento účet.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F # skript a spusťte F # interaktivní

Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #. Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `files.fsx`, ve vašem vývojovém prostředí F #.

Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.

### <a name="add-namespace-declarations"></a>Přidání deklarace oborů názvů

Přidejte následující `open` příkazů do horní části `files.fsx` souboru:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získat připojovací řetězec

Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).

Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Je to ale **nedoporučuje** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždycky pečlivě k ochraně klíče účtu úložiště. Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.

Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

Chcete-li analyzovat připojovací řetězec, použijte:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Tato možnost vrátí `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Vytvoření klienta služby souboru

`CloudFileClient` Typ umožňuje programu používat soubory uložené v úložišti File. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Teď jste připravení psát kód, který načítá a zapisuje data do úložiště File.

## <a name="create-a-file-share"></a>Vytvoření sdílené složky

Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Vytvoření kořenového adresáře a podadresáři

Zde můžete získat kořenový adresář a získat podadresář kořenu. Můžete vytvořit i, pokud ještě neexistují.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Uložte text jako soubor

Tento příklad ukazuje, jak nahrát text jako soubor.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Stáhněte soubor do místní kopii souboru

Zde si stáhnout soubor právě vytvořili, připojování obsah do místního souboru.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Nastavit maximální velikost sdílené složky

Následující příklad ukazuje, jak zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku. `FetchAttributes` musí být volána k naplnění sdílené složky `Properties`, a `SetProperties` rozšíří místní změny do úložiště Azure File.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílené složky

Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro konkrétní soubor. Můžete také vytvořit zásady sdíleného přístupu ve sdílené složce ke správě sdílených přístupových podpisů. Vytvoření zásady sdíleného přístupu se doporučuje, protože tím nabízí způsob odvolání SAS, pokud by měl být dojde k ohrožení.

Zde vytvoříte sdílenou přístup zásad ve sdílené složce a poté tuto zásadu použít k omezení pro SAS na souboru ve sdílené složce.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Další informace o vytváření a použití sdílených přístupových podpisů najdete v tématu [pomocí sdíleného přístupového podpisy (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [vytvoření a použití SAS s úložištěm Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopírování souborů

Soubor můžete zkopírovat do jiného souboru nebo do objektu blob, nebo objekt blob do souboru. Pokud kopírujete objekt blob do souboru nebo souboru do objektu blob, můžete *musí* použít sdílený přístupový podpis (SAS) k ověření zdroje objektu, i když kopírujete v rámci stejného účtu úložiště.

### <a name="copy-a-file-to-another-file"></a>Zkopírujte soubor do jiného souboru

Zde zkopírujte soubor do jiného souboru ve stejné sdílené složce. Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření sdíleným klíčem.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Zkopírujte soubor do objektu blob

Zde vytvoříte soubor a zkopírujte jej do objektu BLOB ve stejném účtu úložiště. Můžete vytvořit SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Stejným způsobem můžete kopírovat objekt blob do souboru. Pokud je zdrojový objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.

## <a name="troubleshooting-file-storage-using-metrics"></a>Řešení potíží s úložištěm File pomocí metrik

Azure Storage Analytics podporuje metriky pro úložiště souborů. S údaji z metriky můžete sledovat žádosti a diagnostikovat problémy.

Metriky pro úložiště File můžete povolit [portálu Azure](https://portal.azure.com), nebo můžete provést z F # takto:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Další kroky

Viz tyto odkazy na další informace o Azure File storage.

### <a name="conceptual-articles-and-videos"></a>Koncepční články a videa

- [Azure Files Storage: hladký cloudový systém souborů protokolu SMB pro Windows a Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak používat Azure File Storage s Linuxem](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Podpora nástrojů pro úložiště File

- [Použití Azure PowerShell s Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Postup použití nástroje AzCopy s Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Použití Azure CLI s Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Odkaz

- [Klientská knihovna pro úložiště pro .NET – referenční informace](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Referenční dokumentace rozhraní API služby REST souboru](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Příspěvky blogu

- [Úložiště Azure File je nyní obecně k dispozici](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Uvnitř Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Představujeme službu Microsoft Azure File](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Nastavení trvalých připojení k Microsoft Azure Files](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
