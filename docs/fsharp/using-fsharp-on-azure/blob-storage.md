---
title: "Začínáme s Azure Blob storage pomocí F #"
description: "Ukládání nestrukturovaných dat v cloudu s Azure Blob storage."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 92e26aff605d3bed89e388dd3616a2a9a3a96081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Začínáme s Azure Blob storage pomocí F # #

Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objekty nebo objekty BLOB. Úložiště objektů BLOB můžete ukládat jakýkoli typ textu nebo binárních dat, jako je například dokument, soubor média nebo instalační program aplikace. Úložiště objektů blob se také označuje jako úložiště objektů.

Tento článek ukazuje, jak provádět běžné úlohy pomocí úložiště objektů Blob. Ukázky jsou napsané v F # pomocí klientské knihovny pro úložiště Azure pro .NET. Úlohy popsané zahrnovat nahrát, seznam, stažení a odstranění objektů BLOB.

Koncepční přehled úložiště objektů blob, najdete v tématu [v příručce .NET pro úložiště objektů blob](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Požadavky

Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account). Pro tento účet je také nutné přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F # skript a spusťte F # interaktivní

Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #. Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `blobs.fsx`, ve vašem vývojovém prostředí F #.

Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` balíčky a reference `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` v pomocí skriptu `#r` – direktiva.

### <a name="add-namespace-declarations"></a>Přidání deklarace oborů názvů

Přidejte následující `open` příkazů do horní části `blobs.fsx` souboru:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získat připojovací řetězec

Pro účely tohoto kurzu potřebujete připojovací řetězec službě Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).

Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, například takto:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Je to ale **nedoporučuje** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždycky pečlivě k ochraně klíče účtu úložiště. Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.

Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

Chcete-li analyzovat připojovací řetězec, použijte:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Tento příkaz vrátí `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Vytvořit některé místní fiktivní data

Než začnete, vytvořte některé fiktivní místní data v adresáři naše skriptu. Později nahrajete tato data.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Vytvoření klienta služby objektů Blob

`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty BLOB uložené v úložišti objektů Blob. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Teď jste připravení psát kód, který načítá a zapisuje data do úložiště objektů Blob.

## <a name="create-a-container"></a>Vytvoření kontejneru

Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Ve výchozím nastavení je nový kontejner privátní, což znamená, že musíte zadat přístupový klíč k úložišti ke stažení z tohoto kontejneru objektů BLOB. Pokud chcete, aby soubory v kontejneru dostupné pro všechny uživatele, můžete nastavit kontejner, aby se veřejné, pomocí následujícího kódu:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Kdokoli na Internetu může vidět objekty BLOB ve veřejném kontejneru, ale můžete upravit nebo odstranit pouze v případě, že máte přístupový klíč odpovídající účtu nebo sdílený přístupový podpis.

## <a name="upload-a-blob-into-a-container"></a>Nahrát objekt blob do kontejneru

Úložiště objektů Blob Azure podporuje objekty BLOB bloku a objekty BLOB stránky. Ve většině případů je objekt blob bloku typ k použití doporučuje.

Chcete-li nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a umožňuje vám získat odkaz na objekt blob bloku. Až budete mít odkaz na objekt blob, můžete nahrát jakýkoli proud dat k němu voláním `UploadFromFile` metoda. Tato operace vytvoří objekt blob, pokud nebyla dříve neexistuje, nebo ho přepíše, pokud existuje.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Seznam objektů BLOB v kontejneru

Pro zobrazení seznamu objektů BLOB v kontejneru, nejdřív získejte odkaz na kontejner. Pak můžete použít kontejneru `ListBlobs` metoda pro načtení objektů BLOB a/nebo obsažené adresáře. Pro přístup k bohaté sadě vlastností a metod vrácené `IListBlobItem`, musíte vysílat na `CloudBlockBlob`, `CloudPageBlob`, nebo `CloudBlobDirectory` objektu. Pokud je typ neznámý, můžete použít kontrolu typu zjistíte, které vysílat. Následující kód ukazuje, jak načíst a získat výstup URI pro každou položku v `mydata` kontejneru:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Můžete také objekty BLOB název informace o cestě jejich názvy. Tím se vytvoří struktura virtuálního adresáře, který můžete uspořádat a procházení, stejně jako u tradičních systémů souborů. Všimněte si, že strukturu adresáře je pouze virtuální – jenom prostředky, které jsou k dispozici v úložišti objektů Blob jsou kontejnery a objekty BLOB. Však nabízí Klientská knihovna pro úložiště `CloudBlobDirectory` objekt, který má odkazovat na virtuální adresář a zjednodušit tak práci s objekty BLOB, které jsou tímto způsobem uspořádány.

Zvažte například následující sadu objektů BLOB bloku v kontejneru nazvaném `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015 nebo Architektura/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg* 
 *2016/architecture/description.txt*
*2016/photo7.jpg*

Při volání `ListBlobs` do kontejneru (viz ukázka výše) se vrátí hierarchický výpis. Pokud obsahuje oba `CloudBlobDirectory` a `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, v uvedeném pořadí, pak výsledný výstup vypadá podobně jako tento:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metodu `true`. V takovém případě je každý objekt blob v kontejneru vrácen jako `CloudBlockBlob` objektu. Volání `ListBlobs` vrátit plochým výpisem vypadá takto:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

a v závislosti na aktuální obsah vašeho kontejneru, výsledky vypadat například takto:

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

## <a name="download-blobs"></a>Stáhnout objekty BLOB

Pokud chcete stáhnout objekty BLOB, nejdřív načtěte odkaz na objekt blob a potom zavolejte `DownloadToStream` metoda. Následující příklad používá `DownloadToStream` způsob přenosu obsahu objektu blob na objekt proudu, který potom můžete zachovat do místního souboru.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Můžete také `DownloadToStream` metoda pro stažení obsahu objektu blob jako textový řetězec.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Odstranění objektů BLOB

Chcete-li odstranit objekt blob, nejdřív získejte odkaz na objekt blob a potom volejte `Delete` metoda na něm.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Seznam objektů blob na stránkách asynchronně

Pokud provádíte výpis velkého počtu objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky. Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, tak, aby čekání na vrácení velké sady výsledků neblokovalo provádění.

Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis nastavením `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodu `false`.

Ukázka definuje asynchronní metodu, pomocí `async` bloku. ``let!`` – Klíčové slovo pozastaví spuštění metody ukázky až do dokončení úlohy vytváření seznamu.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Tato rutina asynchronní jsme teď můžete použít takto. Nejprve nahrát fiktivní data (pomocí místního souboru v tomto kurzu vytvořili).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Nyní volání rutiny. Používáte ``Async.RunSynchronously`` vynutit provedení asynchronní operace.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zápis do doplňovacího objektu BLOB

Doplňovací objekt blob je optimalizován pro operace připojení, například protokolování. Podobně jako objekt blob bloku doplňovací objekt blob se skládá z bloků, ale při přidání nového bloku pro doplňovací objekt blob, je připojen vždy na konec objektu blob. Nelze aktualizovat nebo odstranit existující blok v doplňovacím objektu blob. ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou pro objekt blob bloku.

Každý blok v doplňovacím objektu blob může mít různou velikost, až do maximálního počtu 4 MB volného místa, a doplňovací objekt blob může obsahovat maximálně 50 000 bloků. Maximální velikost doplňovacího objektu BLOB je proto něco větší než 195 GB (4 MB × 50 000 bloků).

Následující příklad vytvoří nový doplňovací objekt blob a připojí některá data, simulaci jednoduché operace protokolování.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

V tématu [objekty BLOB bloku pochopení, objekty BLOB stránky a doplňovacích objektů blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Další informace o rozdílech mezi třemi typy objektů BLOB.

## <a name="concurrent-access"></a>Souběžný přístup

Chcete-li podporovat souběžný přístup do objektu blob z více klientů nebo více instancí procesu, můžete použít **značky etag binárním rozsáhlým** nebo **zapůjčení**.

* **Značka Etag** -poskytuje způsob, jak zjistit, že objektu blob nebo kontejneru byl změněn jiným procesem

* **Zapůjčení** -poskytuje způsob, jak získat exkluzivní, obnovitelné, zápisu nebo odstranit přístupu do objektu blob pro v časovém intervalu

Další informace najdete v tématu [Správa souběžnost v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Názvy kontejnerů

Každý objekt blob v úložišti Azure se musí nacházet v kontejneru. Kontejner je součástí názvu objektu blob. Například `mydata` je název kontejneru v těchto ukázkových objektů blob identifikátory URI:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:

1. Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat pouze písmena, číslice a pomlčky (-) znaků.
1. Každý znak pomlčka (-) musí být okamžitě a následnou písmenem nebo číslicí; po sobě jdoucí pomlčky nejsou povolené v názvech kontejneru.
1. Všechna písmena název kontejneru musí být malé.
1. Názvy kontejnerů musí mít délku 3 až 63 znaků.

Všimněte si, že název kontejneru musí být vždy malá písmena. Pokud název kontejneru zahrnout velké písmeno nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).

## <a name="managing-security-for-blobs"></a>Správa zabezpečení pro objekty BLOB

Ve výchozím nastavení Azure Storage zajišťuje ochranu dat omezením přístupu k majiteli účtu, který je vlastníkem přístupové klíče účtu. Když potřebujete sdílet data objektu blob ve vašem účtu úložiště, je důležité, aby nedošlo k ohrožení zabezpečení klíče pro přístup k účtu. Navíc můžete šifrovat data objektů blob k zajištění, že se jedná o zabezpečený přenos přes síť nebo ve službě Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Řízení přístupu k datům objektu blob

Ve výchozím nastavení jsou data objektu blob ve vašem účtu úložiště je dostupné pouze majiteli účtu úložiště. Ve výchozím nastavení ověřování požadavků na úložiště objektů Blob vyžaduje přístupový klíč účtu. Můžete však určitá data objektu blob zpřístupnit ostatním uživatelům.

Podrobnosti o tom, jak řídit přístup do úložiště objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob na řízení přístupu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>Šifrování dat objektů blob

Úložiště Azure podporuje šifrování dat objektů blob na straně klienta i na serveru.

Podrobnosti na šifrování dat objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob v šifrování](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání Blob storage, postupujte podle následujících odkazech na další informace.

### <a name="tools"></a>Nástroje
- [F # AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) F # – zprostředkovatel typu používanou prozkoumat prostředky Blob, tabulky a fronty Azure Storage a snadno použít operace CRUD s nimi.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) k F # rozhraní API pro používání služby Microsoft Azure Table Storage
- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) je samostatná aplikace, volná, od společnosti Microsoft, který umožňuje vizuálně pracovat s daty Azure Storage ve Windows, OS X a Linux.

### <a name="blob-storage-reference"></a>Odkaz na objekt BLOB úložiště

- [Klientská knihovna pro úložiště pro .NET – referenční informace](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [Referenční dokumentace rozhraní API REST](http://msdn.microsoft.com/library/azure/dd179355)

### <a name="related-guides"></a>Související příručky

- [Začínáme s Azure Blob Storage v jazyce C#](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [Přenos dat pomocí nástroje příkazového řádku azcopy](/azure/storage/storage-use-azcopy)
- [Konfigurace připojovacích řetězců](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [Blog týmu Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/)
