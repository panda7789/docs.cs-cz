---
title: Začínáme se službou Azure File Storage s využitím F#
description: Ukládejte data souborů v cloudu pomocí služby Azure File Storage a připojte svoji cloudovou sdílenou složku z virtuálního počítače Azure (VM) nebo z místní aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 9c25ab930abcbe7b358ae63c709aba4e97aed3be
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423866"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Začínáme se službou Azure File Storage s využitím F\#

Azure File Storage je služba, která nabízí sdílené složky v cloudu pomocí standardního [protokolu SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Podporovány jsou protokoly SMB 2,1 a SMB 3,0. Pomocí služby Azure File Storage můžete migrovat starší aplikace, které spoléhají na sdílené složky do Azure, rychle a bez nákladných přepisů. Aplikace spuštěné ve virtuálních počítačích Azure nebo cloudových službách nebo z místních klientů můžou připojit sdílenou složku v cloudu, stejně jako desktopová aplikace připojí typickou sdílenou složku SMB. Libovolný počet komponent aplikace pak může současně připojit a přistupovat ke sdílenému úložišti souborů.

Koncepční přehled služby File Storage najdete v [příručce .NET pro File Storage](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Pro tento účet budete taky potřebovat přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `files.fsx`ve vašem F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve svém skriptu pomocí direktivy `#r`.

### <a name="add-namespace-declarations"></a>Přidat deklarace oboru názvů

Do horní části `files.fsx` souboru přidejte následující příkazy `open`:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz budete potřebovat připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte svůj připojovací řetězec, například:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy buďte opatrní, abyste chránili klíč účtu úložiště. Vyhněte se distribuci jiným uživatelům, pevným kódováním nebo uložením v souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Použití Azure Configuration Manager je volitelné. Můžete také použít rozhraní API, jako je .NET Framework typ `ConfigurationManager`.

### <a name="parse-the-connection-string"></a>Analyzovat připojovací řetězec

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

Níže uvedený příklad ukazuje, jak kontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku. aby bylo možné naplnit `Properties`sdílené složky a `SetProperties` rozšířit místní změny do služby Azure File Storage, je třeba volat `FetchAttributes`.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Generování sdíleného přístupového podpisu pro soubor nebo sdílení souborů

Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro jednotlivé soubory. Můžete také vytvořit zásady sdíleného přístupu pro sdílenou složku pro správu podpisů sdíleného přístupu. Doporučuje se vytvořit zásadu sdíleného přístupu, protože poskytuje způsob, jak odvolat SAS, pokud by měla být ohrožená.

Tady vytvoříte zásadu sdíleného přístupu pro sdílenou složku a potom pomocí této zásady zadáte omezení pro SAS k souboru ve sdílené složce.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Další informace o vytváření a používání sdílených přístupových podpisů najdete v tématech [použití sdílených přístupových podpisů (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [Vytvoření a použití SAS s úložištěm objektů BLOB](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopírovat soubory

Soubor můžete zkopírovat do jiného souboru nebo do objektu BLOB nebo objektu blob do souboru. Pokud kopírujete objekt blob do souboru nebo soubor do objektu blob, *musíte* k ověření zdrojového objektu použít sdílený přístupový podpis (SAS), a to i v případě, že provádíte kopírování v rámci stejného účtu úložiště.

### <a name="copy-a-file-to-another-file"></a>Kopírování souboru do jiného souboru

Sem zkopírujete soubor do jiného souboru ve stejné sdílené složce. Vzhledem k tomu, že tato operace kopírování kopíruje mezi soubory ve stejném účtu úložiště, můžete k provedení kopie použít ověřování pomocí sdíleného klíče.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopírování souboru do objektu BLOB

Tady vytvoříte soubor a zkopírujete ho do objektu BLOB ve stejném účtu úložiště. Vytvoříte SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Objekt blob můžete zkopírovat do souboru stejným způsobem. Pokud je zdrojový objekt objekt blob, pak vytvořte SAS pro ověření přístupu k tomuto objektu BLOB během operace kopírování.

## <a name="troubleshooting-file-storage-using-metrics"></a>Řešení potíží s úložištěm souborů pomocí metrik

Analýza úložiště Azure podporuje metriky pro úložiště souborů. S daty metrik můžete sledovat požadavky a diagnostikovat problémy.

Metriky pro službu File Storage můžete povolit na webu [Azure Portal](https://portal.azure.com), nebo můžete to udělat F# takto:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Další kroky

Další informace o službě Azure File Storage najdete v těchto odkazech.

### <a name="conceptual-articles-and-videos"></a>Koncepční články a videa

- [Úložiště souborů Azure: bezproblémový cloudový systém souborů SMB pro Windows a Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak používat Azure File Storage se systémem Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Podpora nástrojů pro úložiště souborů

- [Použití Azure PowerShell s Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Jak používat AzCopy s Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Použití rozhraní příkazového řádku Azure s Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Odkaz

- [Klientská knihovna pro úložiště – referenční informace pro .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Odkaz na REST API souborové služby](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Příspěvky na blogu

- [Služba Azure File Storage je teď všeobecně dostupná.](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [V rámci Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Představení Microsoft Azure souborové služby](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Trvalé připojení k souborům Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
