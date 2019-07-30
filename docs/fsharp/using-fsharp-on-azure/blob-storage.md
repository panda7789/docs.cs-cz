---
title: Začínáme se službou Azure Blob Storage s využitím F#
description: Ukládejte nestrukturovaná data v cloudu pomocí služby Azure Blob Storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c8b42339ff1d76f262e956b5e34cc598e0fc855d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630506"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Začínáme s Azure Blob Storage s využitím F\#

Azure Blob Storage je služba, která ukládá nestrukturovaná data v cloudu jako objekty nebo objekty blob. Úložiště objektů BLOB může ukládat jakýkoli typ textu nebo binárních dat, jako je dokument, soubor médií nebo instalační program aplikace. BLOB Storage se také označuje jako úložiště objektů.

V tomto článku se dozvíte, jak provádět běžné úlohy pomocí služby Blob Storage. Ukázky se napíší pomocí F# Azure Storage klientské knihovny pro .NET. Mezi zahrnuté úlohy patří postup při nahrávání, vypsání, stahování a odstraňování objektů BLOB.

Koncepční přehled služby Blob Storage najdete v [průvodci .NET pro úložiště objektů BLOB](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account). Pro tento účet budete potřebovat taky přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s `.fsx` příponou, například `blobs.fsx`ve F# vývojovém prostředí.

Dále pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo `WindowsAzure.Storage` [NuGet](https://www.nuget.org/) , nainstalujte balíčky a `Microsoft.WindowsAzure.ConfigurationManager` a odkazy `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` a ve vašem skriptu pomocí `#r` direktivy.

### <a name="add-namespace-declarations"></a>Přidat deklarace oboru názvů

Na začátek `open` `blobs.fsx` souboru přidejte následující příkazy:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz potřebujete připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte připojovací řetězec, například:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

To však nedoporučujeme pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Použití Azure Configuration Manager je volitelné. Můžete také použít rozhraní API, jako je `ConfigurationManager` typ .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Vrátí `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Vytvoření některých místních fiktivních dat

Než začnete, vytvořte v adresáři našeho skriptu nějaké fiktivní místní údaje. Později tato data nahrajete.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Vytvoření klienta Blob service

`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty blob uložené v úložišti objektů BLOB. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do úložiště objektů BLOB.

## <a name="create-a-container"></a>Vytvoření kontejneru

Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Ve výchozím nastavení je nový kontejner privátní, což znamená, že je nutné zadat přístupový klíč k úložišti pro stahování objektů BLOB z tohoto kontejneru. Chcete-li zpřístupnit soubory v kontejneru všem uživatelům, můžete nastavit, aby byl kontejner veřejný, a to pomocí následujícího kódu:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Kdokoli na internetu může vidět objekty blob ve veřejném kontejneru, ale můžete je upravit nebo odstranit jenom v případě, že máte příslušný přístupový klíč k účtu nebo sdílený přístupový podpis.

## <a name="upload-a-blob-into-a-container"></a>Nahrání objektu blob do kontejneru

Azure Blob Storage podporuje objekty blob bloku a objekty blob stránky. Ve většině případů je objekt blob bloku doporučeným typem, který se má použít.

Pokud chcete nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a použijte ho k získání odkazu na objekt blob bloku. Jakmile budete mít odkaz na objekt blob, můžete do něj nahrát libovolný datový proud tím, že zavoláte `UploadFromFile` metodu. Tato operace vytvoří objekt blob, pokud předtím neexistoval, nebo ho přepíše, pokud existuje.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Výpis objektů BLOB v kontejneru

Chcete-li zobrazit seznam objektů BLOB v kontejneru, nejprve získejte odkaz na kontejner. Pak můžete pomocí `ListBlobs` metody kontejneru načíst objekty blob nebo adresáře, které jsou v něm obsažené. Chcete-li získat přístup k bohatě vydaným `IListBlobItem`vlastnostem a metodám pro vrácenou hodnotu, je nutné ji přetypovat `CloudBlockBlob`na objekt, `CloudPageBlob`nebo `CloudBlobDirectory` . Pokud je typ neznámý, můžete použít kontrolu typu k určení, které chcete přetypovat na. Následující kód ukazuje, jak načíst a výstupní identifikátor URI pro každou položku v `mydata` kontejneru:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Můžete také pojmenovat objekty BLOB s informacemi o cestě v jejich názvech. Tím se vytvoří struktura virtuálních adresářů, kterou můžete uspořádat a procházet stejným způsobem jako tradiční systém souborů. Všimněte si, že adresářová struktura je pouze virtuální – jediné prostředky, které jsou k dispozici ve službě BLOB Storage, jsou kontejnery a objekty blob. Klientská knihovna pro úložiště ale nabízí `CloudBlobDirectory` objekt, který odkazuje na virtuální adresář a zjednodušuje proces práce s objekty blob, které jsou tímto způsobem uspořádány.

Zvažte například následující sadu objektů blob bloku v kontejneru s názvem `photos`:

*photo1.jpg*\
*2015/architektura/Description. txt*\
*2015/architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/architecture/photo6.jpg*\
*2016/architektura/Description. txt*\
*2016/photo7.jpg*\

Při volání `ListBlobs` na kontejner (jako ve výše uvedené ukázce) se vrátí hierarchický výpis. Pokud obsahuje oba `CloudBlobDirectory` i `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, pak výsledný výstup vypadá podobně jako tento:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metody na `true`. V tomto případě se každý objekt BLOB v kontejneru vrátí jako `CloudBlockBlob` objekt. Volání, které `ListBlobs` vrátí plochý seznam, vypadá takto:

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

Pokud chcete stáhnout objekty blob, nejdřív načtěte odkaz na objekt BLOB `DownloadToStream` a pak zavolejte metodu. Následující příklad používá `DownloadToStream` metodu pro přenos obsahu objektu blob do objektu streamu, který pak můžete zachovat do místního souboru.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Pomocí `DownloadToStream` metody můžete také stáhnout obsah objektu BLOB jako textový řetězec.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Odstranit objekty blob

Pokud chcete odstranit objekt blob, nejdřív Získejte odkaz na objekt BLOB a pak `Delete` na něj volejte metodu.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Asynchronní výpis objektů blob na stránkách

Pokud uvádíte velký počet objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete zobrazit seznam objektů blob na stránkách výsledků. Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, aby se při čekání na vrácení velké sady výsledků neblokovalo provádění.

Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis `useFlatBlobListing` nastavením parametru `ListBlobsSegmentedAsync` metody na `false`.

Ukázka definuje asynchronní metodu pomocí `async` bloku. ``let!`` Klíčové slovo pozastaví provádění ukázkové metody, dokud není dokončena úloha výpisu.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Tuto asynchronní rutinu teď můžeme použít následujícím způsobem. Nejdřív nahrajete některá fiktivní data (pomocí místního souboru vytvořeného dříve v tomto kurzu).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Nyní zavolejte rutinu. Použijete `Async.RunSynchronously` k vynucení provedení asynchronní operace.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zápis do doplňovací instance BLOB

Doplňovací objekt BLOB je optimalizovaný pro operace připojení, jako je například protokolování. Podobně jako objekt blob bloku se doplňovací objekt BLOB skládá z bloků, ale když přidáte nový blok do připojeného objektu blob, vždy se připojí ke konci objektu BLOB. Existující blok nelze aktualizovat ani odstranit v doplňovacím objektu BLOB. ID bloku pro doplňovací objekt BLOB nejsou vystavena, protože jsou pro objekt blob bloku.

Každý blok pro doplňovací objekt BLOB může mít jinou velikost, maximálně 4 MB, a doplňovací objekt BLOB může obsahovat maximálně 50 000 bloků. Maximální velikost přidávajících objektů BLOB je proto mírně větší než 195 GB (bloky o velikosti 4 MB X 50 000).

Následující příklad vytvoří nový doplňovací objekt BLOB a připojí k němu nějaká data a simuluje jednoduchou operaci protokolování.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Další informace o rozdílech mezi třemi typy objektů BLOB najdete v tématu porozumění objektům blob [bloku, objektům blob stránky a doplňovacím](https://msdn.microsoft.com/library/azure/ee691964.aspx) objektům blob.

## <a name="concurrent-access"></a>Souběžný přístup

Aby bylo možné podporovat souběžný přístup k objektu BLOB z více klientů nebo instancí více procesů, můžete použít **značky ETag** nebo zapůjčení.

* **Značka ETag** – poskytuje způsob, jak zjistit, že objekt BLOB nebo kontejner byl upraven jiným procesem.

* **Zapůjčení** – poskytuje způsob, jak získat přístup výhradního, obnovitelného, zápisu nebo odstranění objektu BLOB po určitou dobu.

Další informace najdete v tématu [Správa souběžnosti v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Pojmenování kontejnerů

Každý objekt BLOB ve službě Azure Storage se musí nacházet v kontejneru. Kontejner tvoří část názvu objektu BLOB. Například `mydata` je název kontejneru v těchto identifikátorech URI ukázkových objektů BLOB:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Název kontejneru musí být platný název DNS, který splňuje následující pravidla pro pojmenování:

1. Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat jenom písmena, číslice a spojovníky (-).
1. Každý znak spojovníku (-) musí bezprostředně předcházet a musí následovat písmeno nebo číslo. po sobě jdoucí pomlčky nejsou v názvech kontejnerů povolené.
1. Všechna písmena v názvu kontejneru musí být malá.
1. Názvy kontejnerů musí mít délku 3 až 63 znaků.

Všimněte si, že název kontejneru musí být vždy malými písmeny. Pokud zahrnete velké písmeno v názvu kontejneru nebo jinak porušuje pravidla pojmenování kontejnerů, může se zobrazit chyba 400 (chybný požadavek).

## <a name="managing-security-for-blobs"></a>Správa zabezpečení pro objekty blob

Ve výchozím nastavení Azure Storage udržuje vaše data zabezpečená omezením přístupu k vlastníkovi účtu, který je držitelem přístupových klíčů k účtu. Pokud potřebujete sdílet data objektů BLOB v účtu úložiště, je důležité to udělat bez narušení zabezpečení přístupových klíčů k účtu. Kromě toho můžete šifrovat data objektů blob, abyste zajistili, že jsou zabezpečená přenášená přes vodič a v Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Řízení přístupu k datům objektu BLOB

Ve výchozím nastavení jsou data objektů BLOB v účtu úložiště dostupná jenom pro vlastníka účtu úložiště. Ověřování požadavků na úložiště objektů BLOB vyžaduje standardně přístupový klíč účtu. Můžete však chtít zpřístupnit určitá data objektů BLOB ostatním uživatelům.

### <a name="encrypting-blob-data"></a>Šifrování dat objektů BLOB

Azure Storage podporuje šifrování dat objektů BLOB v klientovi i na serveru.

## <a name="next-steps"></a>Další postup

Teď, když jste se naučili základy služby Blob Storage, můžete získat další informace pomocí těchto odkazů.

### <a name="tools"></a>Nástroje

- [F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Poskytovatel F# typu, který se dá použít k prozkoumání prostředků blob, Table a Queue Azure Storage a snadné použití operací CRUD na nich.

- [FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# Rozhraní API pro používání služby Microsoft Azure Table Storage

- [Průzkumník služby Microsoft Azure Storage (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Bezplatná samostatná aplikace od Microsoftu, která umožňuje vizuálně pracovat s Azure Storagemi daty ve Windows, OS X a Linux.

### <a name="blob-storage-reference"></a>Odkaz na úložiště objektů BLOB

- [Rozhraní API pro Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Referenční informace pro službu Azure Storage Services REST API](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Související příručky

- [Začínáme s využitím Azure Blob Storage vC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Přenos dat pomocí nástroje příkazového řádku AzCopy ve Windows](/azure/storage/common/storage-use-azcopy)
- [Přenos dat pomocí nástroje příkazového řádku AzCopy v systému Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Konfigurace připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Blog týmu Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Rychlý start: Vytvoření objektu BLOB v úložišti objektů pomocí .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
