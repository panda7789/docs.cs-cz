---
title: Začínáme se službou Azure Blob Storage s využitím F#
description: Ukládejte nestrukturovaná data v cloudu pomocí služby Azure Blob Storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 90ec0d63b11ad00c53a1740211e9a6509582e863
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935508"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Začínáme s Azure Blob Storage s využitím F\#

Úložiště objektů blob v Azure je služba, která ukládá nestrukturovaná data v cloudu jako objekty nebo objekty blob. Do Blob storage se dá ukládat jakýkoli druh textu nebo binárních dat, jako je dokument, soubor médií nebo instalátor aplikace. Blob storage se také nazývá úložiště objektů.

V tomto článku se dozvíte, jak provádět běžné úlohy pomocí služby Blob Storage. Ukázky se napíší pomocí F# Azure Storage klientské knihovny pro .NET. Mezi zahrnuté úlohy patří postup při nahrávání, vypsání, stahování a odstraňování objektů BLOB.

Koncepční přehled služby Blob Storage najdete v [průvodci .NET pro úložiště objektů BLOB](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account). Pro tento účet budete potřebovat taky přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `blobs.fsx`ve vašem F# vývojovém prostředí.

Dále použijte [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , k instalaci balíčků `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` a odkazování `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` ve vašem skriptu pomocí direktivy `#r`.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte do horní části souboru `blobs.fsx` následující příkazy `open`:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz potřebujete připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte připojovací řetězec, například:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Vrátí `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Vytvoření některých místních fiktivních dat

Než začnete, vytvořte v adresáři našeho skriptu nějaké fiktivní místní údaje. Později tato data nahrajete.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Vytvoření klienta služby Blob service

Typ `CloudBlobClient` umožňuje načíst kontejnery a objekty blob uložené v úložišti objektů BLOB. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Teď můžete napsat kód, který bude číst data z Blob storage a bude je tam také zapisovat.

## <a name="create-a-container"></a>Vytvoření kontejneru

Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Ve výchozím nastavení je nový kontejner privátní, což znamená, že ke stažení objektů blob z tohoto kontejneru musíte zadat přístupový klíč úložiště. Když chcete, aby soubory v kontejneru byly k dispozici všem uživatelům, můžete jej pomocí následujícího kódu nastavit jako veřejný:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Kdokoli na Internetu může vidět objekty blob ve veřejném kontejneru, upravit nebo odstranit je ale můžete jenom v případě, že máte příslušný přístupový klíč k účtu nebo sdílený přístupový podpis.

## <a name="upload-a-blob-into-a-container"></a>Nahrání objektu blob do kontejneru

Úložiště objektů blob v Azure podporuje objekty blob bloku a objekty blob stránky. Ve většině případů je objekt blob bloku doporučeným typem, který se má použít.

Když chcete nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a použijte ho k získání odkazu objektu blob bloku. Jakmile budete mít odkaz na objekt blob, můžete do něj nahrát libovolný datový proud zavoláním metody `UploadFromFile`. Tato operace vytvoří objekt blob, pokud předtím neexistoval, nebo ho přepíše, pokud existuje.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Zobrazí seznam objektů blob v kontejneru

Pokud chcete mít seznam objektů blob v kontejneru, nejdřív získejte odkaz na kontejner. Pak můžete použít metodu `ListBlobs` kontejneru k načtení objektů BLOB a adresářů v ní. Chcete-li získat přístup k bohatě se sadou vlastností a metod vrácených `IListBlobItem`, je nutné ji přetypovat na objekt `CloudBlockBlob`, `CloudPageBlob`nebo `CloudBlobDirectory`. Pokud je typ neznámý, můžete použít kontrolu typu a zjistit, na který typ vysílat. Následující kód ukazuje, jak načíst a získat výstup URI pro každou položku v `mydata` kontejneru:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Můžete také pojmenovat objekty BLOB s informacemi o cestě v jejich názvech. Tím se vytvoří struktura virtuálního adresáře, kterou můžete organizovat a měnit podle potřeby jako u tradičních systémů souborů. Všimněte si, že struktura adresářů je jenom virtuální - jediné prostředky, které jsou dostupné v úložišti objektů Blob,  jsou kontejnery a objekty blob. Klientská knihovna pro úložiště ale nabízí objekt `CloudBlobDirectory`, který odkazuje na virtuální adresář a zjednodušuje proces práce s objekty blob, které jsou tímto způsobem uspořádány.

Můžete zvolit například následující sadu objektů blob bloku v kontejneru nazvaném `photos`:

*photo1.jpg*\
*2015/architektura/Description. txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architektura/Description. txt*\
*2016/photo7.jpg*\

Při volání `ListBlobs` na kontejneru (jako ve výše uvedené ukázce) se vrátí hierarchický výpis. Pokud obsahuje `CloudBlobDirectory` i `CloudBlockBlob` objektů, které představují adresáře a objekty BLOB v kontejneru, pak výsledný výstup vypadá podobně jako tento:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Volitelně můžete nastavit parametr `UseFlatBlobListing` metody `ListBlobs` na `true`. V takovém případě se každý objekt BLOB v kontejneru vrátí jako objekt `CloudBlockBlob`. Volání `ListBlobs` k vrácení nestrukturovaného seznamu vypadá takto:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

a v závislosti na aktuálním obsahu vašeho kontejneru vypadá výsledek takto:

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

## <a name="download-blobs"></a>Stáhnout objekty blob

Chcete-li stáhnout objekty blob, načtěte nejprve odkaz na objekt BLOB a potom zavolejte metodu `DownloadToStream`. Následující příklad používá metodu `DownloadToStream` k přenosu obsahu objektu blob do objektu streamu, který pak můžete zachovat do místního souboru.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Pomocí metody `DownloadToStream` můžete také stáhnout obsah objektu BLOB jako textový řetězec.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Odstraňovat objekty blob

Pokud chcete odstranit objekt blob, nejdřív Získejte odkaz na objekt BLOB a pak na něj volejte metodu `Delete`.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Asynchronní zobrazení seznamu objektů blob na stránkách

Když provádíte výpis velkého počtu objektů blob nebo chcete mít přehled o počtu výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky. Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně tak, aby čekání na vrácení velké sady výsledků neblokovalo provádění.

Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis nastavením parametru `useFlatBlobListing` `ListBlobsSegmentedAsync` metody na `false`.

Ukázka definuje asynchronní metodu pomocí `async`ho bloku. Klíčové slovo ``let!`` pozastaví provádění ukázkové metody, dokud není dokončena úloha výpisu.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Tuto asynchronní rutinu teď můžeme použít následujícím způsobem. Nejdřív nahrajete některá fiktivní data (pomocí místního souboru vytvořeného dříve v tomto kurzu).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Nyní zavolejte rutinu. Použijete `Async.RunSynchronously` k vynucení provedení asynchronní operace.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zápis do doplňovacího objektu blob

Doplňovací objekt blob je optimalizován pro operace připojení, například protokolování. Podobně jako objekt blob bloku se doplňovací objekt blob skládá z bloků, ale když chcete do doplňovacího objektu blob připojit nový blok, je připojen vždy na konec objektu blob. Existující blok v doplňovacím objektu blob se nedá aktualizovat ani odstranit. ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou určená pro objekt blob bloku.

Každý blok v doplňovacím objektu blob může mít různou velikost až do 4 MB, každý doplňovací objekt blob může obsahovat maximálně 50 000 bloků. Maximální velikost doplňovacího objektu blob je proto o něco větší než 195 GB (4 MB × 50 000 bloků).

Následující příklad vytvoří nový doplňovací objekt BLOB a připojí k němu nějaká data a simuluje jednoduchou operaci protokolování.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Další informace o rozdílech mezi třemi typy objektů blob získáte v části [ Vysvětlení objektů blob bloku, objektů blob stránky a doplňovacích objektů blob](https://msdn.microsoft.com/library/azure/ee691964.aspx).

## <a name="concurrent-access"></a>Souběžný přístup

Aby bylo možné podporovat souběžný přístup k objektu BLOB z více klientů nebo instancí více procesů, můžete použít **značky ETag** nebo **zapůjčení**.

- **Značka ETag** – poskytuje způsob, jak zjistit, že objekt BLOB nebo kontejner byl upraven jiným procesem.

- **Zapůjčení** – poskytuje způsob, jak získat přístup výhradního, obnovitelného, zápisu nebo odstranění objektu BLOB po určitou dobu.

Další informace najdete v tématu [Správa souběžnosti v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Pojmenování kontejnerů

Každý objekt blob v úložišti Azure se musí nacházet v kontejneru. Kontejner je součástí názvu objektu blob. Třeba `mydata` je název kontejneru v těchto identifikátorech URI ukázkových objektů blob:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:

1. Názvy kontejnerů musí začínat písmenem nebo číslicí a smí obsahovat jenom písmena, číslice a pomlčky (-).
1. Bezprostředně před a za každým znakem pomlčky (-) se musí nacházet písmeno nebo číslice. Názvy kontejnerů nesmí obsahovat po sobě jdoucí pomlčky.
1. Název kontejneru musí být psaný malými písmeny.
1. Názvy kontejnerů musí mít délku 3 až 63 znaků.

Upozorňujeme, že název kontejneru musí být psaný malými písmeny. Pokud v názvu kontejneru napíšete velké písmeno nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).

## <a name="managing-security-for-blobs"></a>Správa zabezpečení pro objekty blob

Úložiště Azure ve výchozím nastavení zajišťuje ochranu dat omezením přístupu k majiteli účtu, který vlastní klíče pro přístup k účtu. Když budete chtít sdílet data objektu blob na svém účtu úložiště, je důležité zajistit, aby nedošlo k ohrožení zabezpečení vašich klíčů pro přístup k účtu. Navíc můžete šifrovat data objektů blob tak, aby byl zaručen jejich zabezpečený přenos přes síť nebo úložiště Azure.

### <a name="controlling-access-to-blob-data"></a>Kontrola přístupu k datům objektu blob

Ve výchozím nastavení jsou data objektu blob ve vašem účtu úložiště dostupná pouze majiteli účtu úložiště. Ve výchozím nastavení vyžaduje ověřování požadavků na Blob storage přístupový klíč účtu. Můžete však chtít zpřístupnit určitá data objektů BLOB ostatním uživatelům.

### <a name="encrypting-blob-data"></a>Šifrování dat objektů blob

Azure Storage podporuje šifrování dat objektů BLOB v klientovi i na serveru.

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání Blob storage, podívejte se na následující odkazy a získejte další informace.

### <a name="tools"></a>Nástroje

- [F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Poskytovatel F# typu, který se dá použít k prozkoumání prostředků blob, Table a Queue Azure Storage a snadné použití operací CRUD na nich.

- [FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# Rozhraní API pro používání služby Microsoft Azure Table Storage

- [Průzkumník služby Microsoft Azure Storage (mase)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Bezplatná samostatná aplikace od Microsoftu, která umožňuje vizuálně pracovat s Azure Storagemi daty ve Windows, OS X a Linux.

### <a name="blob-storage-reference"></a>Odkazy Blob storage

- [Rozhraní API služby Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Referenční informace k rozhraní REST API služby Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Související příručky

- [Začínáme s využitím Azure Blob Storage vC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Přenos dat pomocí nástroje příkazového řádku AzCopy ve Windows](/azure/storage/common/storage-use-azcopy)
- [Přenos dat pomocí nástroje příkazového řádku AzCopy v systému Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Nakonfigurování připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Blog týmu Azure Storage](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [Rychlý Start: použití .NET k vytvoření objektu BLOB v úložišti objektů](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
