---
title: Začínáme se službou Azure Table Storage s využitím F#
description: Ukládání strukturovaných dat v cloudu pomocí služby Azure Table Storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 23f5e40e1d9b3d5a0ee27d675362930ef86e90c5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935590"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Začínáme s Azure Table Storage a Azure Cosmos DB rozhraní API pro tabulky pomocí F\#

Azure Table Storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu. Table Storage je úložiště klíčů/atributů s návrhem bez schématu. Vzhledem k tomu, že je Table Storage bez schématu, je snadné data přizpůsobovat měnícím se potřebám vaší aplikace. Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací. Využívání úložiště Table Storage obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.

Úložiště Table Storage můžete používat k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresářů, informací o zařízení a dalších typů metadat, které vaše služba vyžaduje. V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.

Azure Cosmos DB poskytuje rozhraní API pro tabulky pro aplikace napsané pro službu Azure Table Storage, které vyžadují prémiové funkce, jako například:

- Globální distribuci na klíč
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

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `tables.fsx`ve vašem F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve vašem skriptu pomocí direktivy `#r`. Udělejte to znovu pro `Microsoft.WindowsAzure.ConfigurationManager`, abyste získali obor názvů Microsoft. Azure.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte do horní části souboru `tables.fsx` následující příkazy `open`:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Získání připojovacího řetězce Azure Storage

Pokud se připojujete k Azure Storage Table service, budete pro tento kurz potřebovat připojovací řetězec. Připojovací řetězec můžete zkopírovat z Azure Portal. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Získání připojovacího řetězce Azure Cosmos DB

Pokud se připojujete k Azure Cosmos DB, budete pro tento kurz potřebovat připojovací řetězec. Připojovací řetězec můžete zkopírovat z Azure Portal. V Azure Portal v účtu Cosmos DB přejděte na **nastavení** > **připojovací řetězec**a kliknutím na tlačítko **Kopírovat** zkopírujte primární připojovací řetězec.

V tomto kurzu do skriptu zadejte připojovací řetězec, podobně jako v následujícím příkladu:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Vrátí `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Vytvoření klienta služby Table service

Třída `CloudTableClient` umožňuje načíst tabulky a entity v úložišti tabulek. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teď můžete napsat kód, který bude číst data z Table Storage a bude je tam také zapisovat.

### <a name="create-a-table"></a>Vytvoření tabulky

Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Přidání entity do tabulky

Entita musí mít typ, který dědí z `TableEntity`. `TableEntity` můžete roztáhnout jakýmkoli způsobem, ale váš typ *musí* mít konstruktor bez parametrů. V tabulce Azure jsou uloženy pouze vlastnosti `get` i `set`.

Klíč oddílu a řádku entity jednoznačně identifikují entitu v tabulce. Na entity se stejným klíčem oddílu je možné se (v porovnání s těmi, které mají různé klíče oddílů) rychleji dotazovat, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.

Tady je příklad `Customer`, který používá `lastName` jako klíč oddílu a `firstName` jako klíč řádku.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Nyní do tabulky přidejte `Customer`. Provedete to tak, že vytvoříte `TableOperation`, která se spustí v tabulce. V tomto případě vytvoříte operaci `Insert`.

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

Chcete-li zadat dotaz na tabulku pro všechny entity v oddílu, použijte objekt `TableQuery`. Tady můžete filtrovat entity, kde "Smith" je klíč oddílu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Načtení rozsahu entit v oddílu

Pokud nechcete, aby se zadával dotaz na všechny entity v oddílu, můžete zadat rozsah nakombinováním filtru klíče oddílu s filtrem klíče řádku. Tady použijete dva filtry k získání všech entit v oddílu "Smith", kde klíč řádku (jméno) začíná písmenem "M" v abecedě.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Načtení jedné entity

Můžete napsat dotaz pro načtení jedné konkrétní entity. Tady můžete pomocí `TableOperation` zadat zákazníka "Robert Smith". Místo kolekce se vrátí `Customer`. Zadání klíče oddílu a klíče řádku v dotazu představuje nejrychlejší způsob, jak z Table service načíst jednu entitu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Nyní se tisknou výsledky:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Nahrazení entity

Chcete-li aktualizovat entitu, načtěte ji z Table service, upravte objekt entity a uložte změny zpět do Table service pomocí operace `Replace`. Tím dojde k tomu, že se entita na serveru úplně nahradí, pokud se entita na serveru od načtení nezměnila, a v takovém případě se operace nezdařila. Tato chyba je zabránit tomu, aby aplikace nechtěně přepsala změny z jiných zdrojů.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Vložení nebo nahrazení entity

V některých případech nevíte, zda entita v tabulce existuje. A pokud k tomu dojde, aktuální hodnoty, které jsou v něm uložené, už nejsou potřeba. Pomocí `InsertOrReplace` můžete vytvořit entitu, nebo ji nahradit, pokud existuje, bez ohledu na její stav.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Dotaz na podmnožinu vlastností entity

Dotaz na tabulku může načíst jenom několik vlastností z entity místo všech. Tato technika s názvem projekce může zlepšit výkon dotazů, zejména u velkých entit. Tady vrátíte jenom e-mailové adresy, které používají `DynamicTableEntity` a `EntityResolver`. Poznámka: Projekci nepodporuje emulátor místního úložiště, takže tento kód bude možné spustit pouze v případě, že používáte účet služby Table service.

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

## <a name="next-steps"></a>Další kroky

Teď, když jste se seznámili se základy úložiště tabulek, postupujte podle těchto odkazů a získejte další informace o složitějších úlohách úložiště a Azure Cosmos DB rozhraní API pro tabulky.

- [Úvod do rozhraní Table API služby Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Klientská knihovna Storage pro .NET – referenční informace](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Poskytovatel typu Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog týmu Azure Storage](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [Konfigurace připojovacích řetězců](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
