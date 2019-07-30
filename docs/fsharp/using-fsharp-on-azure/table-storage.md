---
title: Začínáme se službou Azure Table Storage s využitím F#
description: Ukládání strukturovaných dat v cloudu pomocí služby Azure Table Storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: c8ab2d61048523ac52f305c7bd035c73ca0d3f60
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630465"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Začínáme s úložištěm Azure Table a Azure Cosmos DB rozhraní API pro tabulky pomocí jazyka F\#

Azure Table Storage je služba, která ukládá strukturovaná NoSQL data v cloudu. Table Storage je úložiště klíčů/atributů s návrhem bez schématu. Vzhledem k tomu, že je tabulka úložiště bez schématu, je snadné přizpůsobit data, jak jsou potřeby vaší aplikace vyvíjet. Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací. Služba Table Storage je obvykle výrazně nižší, než tradiční SQL pro podobné objemy dat.

Tabulkové úložiště můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresářů, informací o zařízení a dalších typů metadat, které vaše služba vyžaduje. V tabulce můžete ukládat libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, a to až do limitu kapacity účtu úložiště.

Azure Cosmos DB poskytuje rozhraní API pro tabulky pro aplikace napsané pro službu Azure Table Storage, které vyžadují prémiové funkce, jako například:

- Globální distribuce klíč.
- Vyhrazená propustnost po celém světě.
- Latence v řádu milisekund na 99. percentilu.
- Záruka vysoké dostupnosti.
- Automatické sekundární indexování.

Pomocí rozhraní API tabulky je možné migrovat aplikace napsané pro Azure Table Storage beze změn kódu na službu Azure Cosmos DB a využít tak prémiové funkce. Rozhraní API tabulky má klientské sady SDK dostupné pro .NET, Java, Python a Node.js.

Další informace najdete v tématu [Úvod do Azure Cosmos DB rozhraní API pro tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>O tomto kurzu

V tomto kurzu se dozvíte F# , jak napsat kód, který provede některé běžné úlohy pomocí služby Azure Table storage nebo Azure Cosmos DB rozhraní API pro tabulky, včetně vytváření a odstraňování tabulky a vkládání, aktualizace, odstraňování a dotazování na data tabulky.

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet služby Azure Storage](/azure/storage/storage-create-storage-account) nebo [účet Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s `.fsx` příponou, například `tables.fsx`ve F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo `WindowsAzure.Storage` [NuGet](https://www.nuget.org/) , nainstalujte `#r` balíček a odkazujte `WindowsAzure.Storage.dll` ve svém skriptu pomocí direktivy. Udělejte to znovu `Microsoft.WindowsAzure.ConfigurationManager` , aby se získal obor názvů Microsoft. Azure.

### <a name="add-namespace-declarations"></a>Přidat deklarace oboru názvů

Na začátek `open` `tables.fsx` souboru přidejte následující příkazy:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Získání připojovacího řetězce Azure Storage

Pokud se připojujete k Azure Storage Table service, budete pro tento kurz potřebovat připojovací řetězec. Připojovací řetězec můžete zkopírovat z Azure Portal. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Získání připojovacího řetězce Azure Cosmos DB

Pokud se připojujete k Azure Cosmos DB, budete pro tento kurz potřebovat připojovací řetězec. Připojovací řetězec můžete zkopírovat z Azure Portal. V Azure Portal v účtu Cosmos DB přejděte na **Nastavení** > **připojovací řetězec**a kliknutím na tlačítko **Kopírovat** zkopírujte primární připojovací řetězec. 

V tomto kurzu do skriptu zadejte připojovací řetězec, podobně jako v následujícím příkladu:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

To však nedoporučujeme pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Použití Azure Configuration Manager je volitelné. Můžete také použít rozhraní API, jako je `ConfigurationManager` typ .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Vrátí `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Vytvoření klienta služby Table service

`CloudTableClient` Třída umožňuje načíst tabulky a entity v úložišti tabulek. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teď můžete napsat kód, který bude číst data z Table Storage a bude je tam také zapisovat.

### <a name="create-a-table"></a>Vytvoření tabulky

Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Přidání entity do tabulky

Entita musí mít typ, který dědí z `TableEntity`. Můžete se roztáhnout `TableEntity` jakýmkoli způsobem, ale váš typ *musí* mít konstruktor bez parametrů. V tabulce Azure jsou uloženy `get` pouze `set` vlastnosti, které mají obojí a.

Klíč oddílu a řádku entity jednoznačně identifikují entitu v tabulce. Na entity se stejným klíčem oddílu se dá zadávat dotaz rychleji než u různých klíčů oddílů, ale pomocí různých klíčů oddílu můžete dosáhnout větší škálovatelnosti paralelních operací.

Tady je příklad `Customer` , který `lastName` používá jako klíč oddílu a `firstName` jako klíč řádku.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Nyní přidejte `Customer` do tabulky. Provedete to tak, `TableOperation` že vytvoříte objekt, který se spustí v tabulce. V tomto případě vytvoříte `Insert` operaci.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Vložení dávky entit

Do tabulky můžete vložit dávku entit pomocí jediné operace zápisu. Dávkové operace umožňují kombinovat operace do jednoho spuštění, ale mají určitá omezení:

- V rámci stejné dávkové operace můžete provádět aktualizace, odstraňování a vkládání.
- Dávková operace může zahrnovat až 100 entit.
- Všechny entity v dávkové operaci musí mít stejný klíč oddílu.
- I když je možné provést dotaz v dávkové operaci, musí být jedinou operací v dávce.

Zde je nějaký kód, který kombinuje dvě vložení do dávkové operace:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Načtení všech entit v oddílu

Chcete-li zadat dotaz na tabulku pro všechny entity v oddílu, `TableQuery` použijte objekt. Tady můžete filtrovat entity, kde "Smith" je klíč oddílu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Načtení rozsahu entit v oddílu

Pokud nechcete, aby se zadával dotaz na všechny entity v oddílu, můžete zadat rozsah nakombinováním filtru klíče oddílu s filtrem klíče řádku. Tady použijete dva filtry k získání všech entit v oddílu "Smith", kde klíč řádku (jméno) začíná písmenem "M" v abecedě.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Načtení jedné entity

Můžete napsat dotaz pro načtení jedné konkrétní entity. Zde můžete použít `TableOperation` k určení zákazníka "Robert Smith". Místo kolekce se vrátí `Customer`. Zadání klíče oddílu a klíče řádku v dotazu představuje nejrychlejší způsob, jak z Table service načíst jednu entitu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Nahrazení entity

Chcete-li aktualizovat entitu, načtěte ji z Table Service, upravte objekt entity a uložte změny zpět do Table Service pomocí `Replace` operace. Tím dojde k tomu, že se entita na serveru úplně nahradí, pokud se entita na serveru od načtení nezměnila, a v takovém případě se operace nezdařila. Tato chyba je zabránit tomu, aby aplikace nechtěně přepsala změny z jiných zdrojů.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Vložení nebo nahrazení entity

V některých případech nevíte, zda entita v tabulce existuje. A pokud k tomu dojde, aktuální hodnoty, které jsou v něm uložené, už nejsou potřeba. Pomocí `InsertOrReplace` můžete vytvořit entitu, nebo ji nahradit, pokud existuje, bez ohledu na její stav.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Dotaz na podmnožinu vlastností entity

Dotaz na tabulku může načíst jenom několik vlastností z entity místo všech. Tato technika s názvem projekce může zlepšit výkon dotazů, zejména u velkých entit. Tady vrátíte jenom e-mailové `DynamicTableEntity` adresy `EntityResolver`pomocí a. Všimněte si, že projekce není podporována v emulátoru místního úložiště, takže tento kód bude spuštěn pouze v případě, že používáte účet na Table service.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Asynchronní načítání entit na stránkách

Pokud čtete velký počet entit a chcete je zpracovat tak, jak jsou načteny, aniž byste čekali na jejich vrácení, můžete použít segmentický dotaz. Tady vrátíte výsledky na stránkách pomocí asynchronního pracovního postupu, aby se při čekání na vrácení velké sady výsledků neblokovalo provádění.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Tento výpočet teď spustíte synchronně:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Odstranění entity

Entitu můžete po načtení odstranit. Stejně jako u aktualizace entity se to nepovede, pokud se entita od jejího načtení změnila.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Odstranění tabulky

Tabulku můžete odstranit z účtu úložiště. Tabulku, která byla odstraněna, nebude možné po odstranění nějakou dobu znovu vytvořit.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Další postup

Teď, když jste se seznámili se základy úložiště tabulek, postupujte podle těchto odkazů a získejte další informace o složitějších úlohách úložiště a Azure Cosmos DB rozhraní API pro tabulky.

- [Úvod do rozhraní Table API služby Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Klientská knihovna Storage pro .NET – referenční informace](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Poskytovatel typu Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog týmu Azure Storage](https://blogs.msdn.com/b/windowsazurestorage/)
- [Konfigurace připojovacích řetězců](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Začínáme s využitím Azure Table Storage v .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
