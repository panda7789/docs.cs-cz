---
title: 'Začínáme s Azure Blob storage s využitím F #'
description: Store nestrukturovaných dat v cloudu s využitím úložiště objektů Blob v Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: ea9dc334ec9c2bcd4a80cc501d4b6634da5f64e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44037279"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Začínáme s Azure Blob storage s využitím F # #

Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objektů BLOB. BLOB storage dokáže ukládat jakýkoli druh textu nebo binárních dat, jako je například dokument, soubor médií nebo instalační program aplikace. Úložiště objektů blob se taky označuje jako úložiště objektů.

V tomto článku se dozvíte, jak provádět běžné úlohy pomocí úložiště objektů Blob. Ukázky jsou napsané s využitím F # pomocí klientské knihovny Azure Storage pro .NET. Popsané úkoly popsané v nahrání, výpisu, stahování a odstraňování objektů BLOB.

Koncepční přehled služby blob storage, najdete v části [v příručce .NET pro úložiště objektů blob](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Požadavky

K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account). Pro tento účet také potřebovat přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvořit skript F # a začněte jazyka F # Interactive

Ukázky v tomto článku je možné v F # aplikace nebo skript F #. Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `blobs.fsx`, ve vašem vývojovém prostředí F #.

Dále používat [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` balíčky a reference `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` v pomocí skriptu `#r` směrnice.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte následující `open` příkazy k hornímu okraji `blobs.fsx` souboru:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro účely tohoto kurzu potřebujete připojovací řetězec služby Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).

Pro tento kurz můžete zadat připojovací řetězec ve vašem skriptu, například takto:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Je to ale **ale nedoporučený krok** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Pečlivě vždy chránit váš klíč účtu úložiště. Nedávejte ho jiným uživatelům pevného kódování, nebo ho uložili na soubor s prostým textem, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.

Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce, použijte:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Tím se vrátí `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Vytvořit místní fiktivní data

Než začnete, vytvořte nějaká fiktivní místní data v adresáři skriptu. Později můžete tato data nahrát.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Vytvoření klienta služby Blob service

`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty BLOB uložené v úložišti objektů Blob. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do úložiště objektů Blob.

## <a name="create-a-container"></a>Vytvoření kontejneru

Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Ve výchozím nastavení je nový kontejner privátní, což znamená, že je nutné zadat přístupový klíč úložiště pro objekty BLOB můžete stáhnout z tohoto kontejneru. Pokud chcete zpřístupnit soubory v kontejneru pro všechny uživatele, můžete nastavit kontejner, aby se veřejné, pomocí následujícího kódu:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Kdokoli na Internetu může vidět objekty BLOB ve veřejném kontejneru, ale můžete upravit nebo odstranit jenom v případě, že máte příslušný přístup klíč k účtu nebo sdílený přístupový podpis.

## <a name="upload-a-blob-into-a-container"></a>Nahrání objektu blob do kontejneru

Azure Blob Storage podporuje objekty BLOB bloku a objekty BLOB stránky. Ve většině případů je objekt blob bloku typ k použití doporučuje.

Chcete-li nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a použijte ho k získání odkazu objektu blob bloku. Jakmile budete mít odkaz na objekt blob, můžete nahrát jakýkoli proud dat k němu voláním `UploadFromFile` metody. Tato operace vytvoří objekt blob, pokud nebyla dříve neexistuje, nebo ho přepíše, pokud už existoval.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Výpis objektů BLOB v kontejneru

Seznam objektů BLOB v kontejneru, nejdřív získejte odkaz na kontejner. Pak můžete použít kontejneru `ListBlobs` metodu pro načtení objektů BLOB a/nebo obsažené adresáře. Pro přístup k bohaté sadě vlastností a metod vrácené `IListBlobItem`, musíte vysílat na `CloudBlockBlob`, `CloudPageBlob`, nebo `CloudBlobDirectory` objektu. Pokud je typ neznámý, můžete určit, který typ vysílat kontrolu typu. Následující kód ukazuje, jak načíst a výstup URI pro každou položku v `mydata` kontejneru:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Můžete také název objektů BLOB pomocí informací o cestě v jejich názvy. Tím se vytvoří struktura virtuálního adresáře, kterou můžete organizovat a procházet podle potřeby jako u tradičních systémů souborů. Všimněte si, že struktura adresářů je jenom virtuální - jediné prostředky, které jsou k dispozici v úložišti objektů Blob, jsou kontejnery a objekty BLOB. Však nabízí klientskou knihovnu pro úložiště `CloudBlobDirectory` objektu, který chcete odkazovat na virtuální adresář a zjednodušit tak práci s objekty BLOB, které jsou tímto způsobem uspořádány.

Zvažte například následující sadu objektů BLOB bloku v kontejneru nazvaném `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

Při volání `ListBlobs` kontejneru (viz ukázka výše) se vrátí hierarchický výpis. Pokud obsahuje `CloudBlobDirectory` a `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, v uvedeném pořadí, pak výsledný výstup by měl vypadat nějak takto:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metodu `true`. V takovém případě je každý objekt blob v kontejneru vrácen jako `CloudBlockBlob` objektu. Volání `ListBlobs` vrátit plochým výpisem vypadá takto:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

a v závislosti na aktuální obsah vašeho kontejneru, výsledek vypadat nějak takto:

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>Stažení objektů BLOB

Pokud chcete stáhnout objekty BLOB, nejdřív načtěte odkaz objektu blob a pak zavolat `DownloadToStream` metody. V následujícím příkladu `DownloadToStream` způsob přenosu obsahu objektu blob na objekt datového proudu, který je pak možné zachovat do místního souboru.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Můžete také použít `DownloadToStream` metody ke stahování obsahu objektu blob jako textový řetězec.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Odstranění objektů BLOB

Chcete-li odstranit objekt blob, nejdřív získejte odkaz na objekt blob a poté zavolejte `Delete` metoda na něm.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Seznam objektů blob na stránkách asynchronně

Pokud jsou výpis velkého počtu objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky. Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, takže provádění není blokována během čekání na vrácení velké sady výsledků.

Tento příklad ukazuje plochý výpis objektu blob, ale můžete také provést hierarchický výpis nastavením `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodu `false`.

Ukázka definuje metodu, pomocí `async` bloku. ``let!`` – Klíčové slovo pozastaví spuštění metody ukázky až do dokončení úlohy vytváření seznamu.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Tato rutina asynchronní jsme teď můžete použít následujícím způsobem. Nejprve nahrát fiktivní data (s použitím místní soubor vytvořený dříve v tomto kurzu).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Nyní volání rutiny. Použijete `Async.RunSynchronously` k vynucení provedení asynchronní operace.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zápis do doplňovacího objektu BLOB

Doplňovací objekt blob je optimalizován pro operace připojení, jako je například protokolování. Podobně jako objekt blob bloku doplňovací objekt blob se skládá z bloků, ale při přidání nového bloku pro doplňovací objekt blob se vždy připojí na konec objektu blob. Nelze aktualizovat nebo odstranit existující blok v doplňovacím objektu blob. ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou pro objekt blob bloku.

Každý blok v doplňovacím objektu blob může mít různou velikost až 4 MB, a doplňovací objekt blob může obsahovat maximálně 50 000 bloků. Maximální velikost doplňovacího objektu blob je proto o něco větší než 195 GB (4 MB × 50 000 bloků).

Následující příklad vytvoří nový doplňovací objekt blob a připojí některá data, simulaci jednoduché operace protokolování.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Zobrazit [vysvětlení objektů BLOB bloku, objekty BLOB stránky a doplňovací objekty BLOB](https://msdn.microsoft.com/library/azure/ee691964.aspx) Další informace o rozdílech mezi třemi typy objektů BLOB.

## <a name="concurrent-access"></a>Souběžný přístup

Pro podporu souběžný přístup z více klientům nebo více instancí procesu do objektu blob, můžete použít **značek etag** nebo **zapůjčení**.

* **Značka Etag** – poskytuje způsob, jak zjistit, že objekt blob nebo kontejner byl změněn jiným procesem

* **Zapůjčení** – poskytuje způsob, jak získat exkluzivní, obnovitelné, zapsat nebo odstranit pro určitou dobu přístup k objektu blob

Další informace najdete v tématu [Správa souběžnosti v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Pojmenování kontejnerů

Každý objekt blob ve službě Azure storage se musí nacházet v kontejneru. Kontejner je součástí názvu objektu blob. Například `mydata` je název kontejneru v těchto ukázkových objektů blob identifikátorů URI:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:

1. Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat jenom písmena, číslice a znak spojovníku (-).
1. Každému znaku pomlčky (-) musí být bezprostředně před a následované písmenem nebo číslicí; po sobě jdoucí pomlčky nejsou povolené v názvu kontejneru.
1. Všechna písmena v názvu kontejneru musí obsahovat malá písmena.
1. Názvy kontejnerů musí mít délku 3 až 63 znaků.

Všimněte si, že název kontejneru musí vždy obsahovat malá písmena. Pokud zahrnují písmena velká písmena v názvu kontejneru nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).

## <a name="managing-security-for-blobs"></a>Správa zabezpečení pro objekty BLOB

Ve výchozím nastavení služby Azure Storage zachovává zabezpečení dat omezením přístupu k majiteli účtu, který je ve vlastnictví přístupové klíče účtu. Když budete potřebovat ke sdílení dat objektů blob v účtu úložiště, je potřeba udělat bez narušení zabezpečení přístupové klíče vašeho účtu. Navíc můžete šifrovat data objektů blob abychom měli jistotu, že se jedná o zabezpečený přenos přenosu i ve službě Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Řízení přístupu k datům objektu blob

Ve výchozím nastavení je přístupný pouze vlastník účtu úložiště dat objektů blob v účtu úložiště. Ve výchozím nastavení ověřování požadavků na úložiště objektů Blob vyžaduje přístupový klíč účtu. Můžete však chtít určitá data objektu blob zpřístupnit ostatním uživatelům.

Podrobnosti o tom, jak řídit přístup k úložišti objektů blob najdete v tématu [v .NET průvodci část úložiště objektů blob řízení přístupu na](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>Šifrování dat objektů blob

Azure Storage podporuje šifrování dat objektů blob na straně klienta i na serveru.

Podrobnosti o šifrování dat objektů blob najdete v tématu [v příručce .NET pro úložiště objektů blob v tématu o šifrování](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání Blob storage, použijte tyto odkazy na další informace.

### <a name="tools"></a>Nástroje
- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # typu poskytovatele, který slouží k prozkoumání objektů Blob, tabulky a fronty Azure Storage prostředky a snadno použít operace CRUD s nimi.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) API F # za používání služby Microsoft Azure Table Storage
- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) je bezplatná samostatná aplikace od Microsoftu, která umožňuje vizuálně pracovat s daty Azure Storage ve Windows, OS X a Linux.

### <a name="blob-storage-reference"></a>Odkaz na objekt BLOB úložiště

- [Rozhraní API služby Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Reference k rozhraní REST API služby Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Související vodítka

- [Začínáme se službou Azure Blob Storage v jazyce C#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Přenos dat pomocí nástroje příkazového řádku azcopy ve Windows](/azure/storage/common/storage-use-azcopy)
- [Přenos dat pomocí nástroje příkazového řádku azcopy v Linuxu](/azure/storage/common/storage-use-azcopy-linux)
- [Nakonfigurování připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Blog týmu Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
