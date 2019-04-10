---
title: Začínáme s Azure Table storage pomocíF#
description: Store strukturovaných dat v cloudu pomocí služby Azure Table storage nebo Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 54c777acd454e4f675175b814675c185e41ad9a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086699"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Začínáme s Azure Table storage a Azure Cosmos DB Table API pomocí F\#

Azure Table storage je služba, která ukládá strukturovaná data NoSQL v cloudu. Úložiště Table je úložiště klíčů/atributů s návrhem. Vzhledem k tomu, že je Table storage bez schématu, je snadné data přizpůsobovat měnícím potřebám vaší aplikace. Přístup k datům je rychlý a cenově výhodný pro všechny typy aplikací. Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.

Table storage můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresářů, informací o zařízení a jiný typ metadat, které vaše služba vyžaduje. V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.

Azure Cosmos DB poskytuje rozhraní API tabulky pro aplikace napsané pro službu Azure Table storage a, které vyžadují prémiové funkce jako například:

- Globální distribuce na klíč.
- Vyhrazená propustnost po celém světě.
- Latence v řádu milisekund na 99. percentilu.
- Záruka vysoké dostupnosti.
- Automatické sekundární indexování.

Pomocí rozhraní API tabulky je možné migrovat aplikace napsané pro Azure Table Storage beze změn kódu na službu Azure Cosmos DB a využít tak prémiové funkce. Rozhraní API tabulky má klientské sady SDK dostupné pro .NET, Java, Python a Node.js.

Další informace najdete v tématu [Úvod do služby Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>O tomto kurzu

Tento kurz ukazuje, jak napsat F# kód pro některé běžné úlohy pomocí služby Azure Table storage nebo rozhraní Azure Cosmos DB Table API, včetně vytváření a odstraní tabulka a vložení, aktualizace, odstranění nebo dotazování tabulkových dat.

## <a name="prerequisites"></a>Požadavky

K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account) nebo [účtu služby Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skript a spustit F# interaktivní

Ukázky v tomto článku můžete použít buď F# aplikace nebo F# skriptu. Vytvoření F# skript, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`v vaše F# vývojové prostředí.

Pak pomocí [Správce balíčků](package-management.md) jako [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a odkaz na `WindowsAzure.Storage.dll` ve skriptu pomocí `#r`směrnice. Proveďte znovu `Microsoft.WindowsAzure.ConfigurationManager` zajistí Microsoft.Azure oboru názvů.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte následující `open` příkazy k hornímu okraji `tables.fsx` souboru:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Získání připojovacího řetězce služby Azure Storage

Pokud se připojujete ke službě Azure Storage Table, budete potřebovat připojovací řetězec pro účely tohoto kurzu. Váš připojovací řetězec můžete zkopírovat z portálu Azure portal. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Získání připojovacího řetězce služby Azure Cosmos DB

Pokud se připojujete ke službě Azure Cosmos DB, budete potřebovat připojovací řetězec pro účely tohoto kurzu. Váš připojovací řetězec můžete zkopírovat z portálu Azure portal. Na webu Azure Portal, v účtu služby Cosmos DB, přejděte na **nastavení** > **připojovací řetězec**a klikněte na tlačítko **kopírování** tlačítko zkopírujte primární připojovací Řetězec. 

Pro tento kurz zadejte svůj připojovací řetězec ve vašem skriptu, jako v následujícím příkladu:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Je to ale **ale nedoporučený krok** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.

Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce, použijte:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Tím se vrátí `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Vytvoření klienta služby Table service

`CloudTableClient` Třída vám umožňuje načítat tabulky a entity ve službě Table storage. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teď můžete napsat kód, který bude číst data z Table Storage a bude je tam také zapisovat.

### <a name="create-a-table"></a>Vytvoření tabulky

Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Přidání entity do tabulky

Entita musí mít typ, který dědí z `TableEntity`. Můžete rozšířit `TableEntity` v libovolné způsobem, který vám vyhovuje, ale váš typ *musí* mít konstruktor bez parametrů. Pouze vlastnosti, které mají obě `get` a `set` jsou uložené v tabulce Azure.

Entity oddílu a klíčem řádku jednoznačně identifikují entitu v tabulce. Entity se stejným klíčem oddílu můžete dotazovat rychleji než ty, které mají různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.

Tady je příklad `Customer` , která používá `lastName` jako klíč oddílu a `firstName` jako klíč řádku.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Nyní přidejte `Customer` do tabulky. Chcete-li tak učinit, vytvořte `TableOperation` , který se spustí v tabulce. V tomto případě vytvoříte `Insert` operace.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Vložení dávky entit

Do tabulky pomocí operace zápisu jednoho můžete vložit dávku entit. Povolit dávkové operace můžete kombinovat operací do jedné provádění, ale mají určitá omezení:

- Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.
- Dávková operace může obsahovat až 100 entit.
- Všechny entity v dávkové operaci musí mít stejný klíč oddílu.
- I když je možné provést dotaz v dávkové operaci, musí být ale jediná operace v dávce.

Zde je kód, který spojuje dvě vloží do dávkové operace:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Načtení všech entit v oddílu

Chcete-li dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu. Zde filtrovat pro entity, kde "Macek" je klíč oddílu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Nyní můžete vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Načtení rozsahu entit v oddílu

Pokud nechcete, aby se zadával dotaz na všechny entity v oddílu, můžete zadat rozsah nakombinováním filtru klíče oddílu s filtrem klíče řádku. Zde použijete dva filtry k získání všech entit v oddílu "Macek" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Nyní můžete vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Načtení jedné entity

Můžete napsat dotaz pro načtení jedné konkrétní entity. Zde raději použijte `TableOperation` k určení zákazníka "Ben Smith". Místo kolekce, které získáte zpět `Customer`. Zadání klíče oddílu a klíč řádku v dotazu je nejrychlejší způsob, jak načíst jednu entitu ze služby Table service.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Nyní můžete vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Nahrazení entity

Jak aktualizovat entitu, načtěte ji ze služby Table service, upravte objekt entity a potom uložte změny zpět do tabulky pomocí služby `Replace` operace. To způsobí entita, která má být na serveru plně nahradí, pokud má entita na serveru od načtení, v takovém případě se operace nezdaří. Tato chyba je zabránit aplikaci v nechtěném přepsání změny z jiných zdrojů.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Vložení nebo nahrazení entity

V některých případech nevíte, jestli entita existuje v tabulce. A pokud ano, aktuální hodnoty uložené v ní už nejsou potřeba. Můžete použít `InsertOrReplace` vytvořit entitu, nebo pokud existuje, bez ohledu na jeho stavu, nahraďte ho.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Dotaz na podmnožinu vlastností entity

Tabulkový dotaz může načíst jenom několik z entity místo všechny z nich. Tato technika, říká projekce, může zlepšit výkon dotazů, zejména u velkých entit. Tady, vrátí pouze e-mailové adresy, které používají `DynamicTableEntity` a `EntityResolver`. Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód se spustí pouze v případě, že používáte účet služby Table Service.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Asynchronní načítání entit na stránkách

Pokud načítáte velký počet entit a chcete pro jejich zpracování, jak jsou načítány, spíše než čekat na jejich všechny k vrácení, můžete pomocí segmentovaného dotazu. Tady vracet výsledky na stránkách s použitím asynchronního pracovního postupu tak, aby spuštění není blokován, zatímco čekáte pro velké sady výsledků k vrácení.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Můžete teď tento výpočet synchronnímu provádění:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Odstranění entity

Entitu můžete po jejím načtení odstranit. Stejně jako u aktualizaci entity, to se nezdaří, pokud entita se nezměnila, protože jste získali.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Odstranění tabulky

Můžete odstranit tabulku z účtu úložiště. Tabulku, která byla odstraněna, nebude možné po odstranění nějakou dobu znovu vytvořit.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání služby Table storage, na následujících odkazech najdete informace o složitějších úlohách úložiště a rozhraní Azure Cosmos DB Table API.

- [Úvod do služby Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Klientská knihovna pro úložiště pro .NET – referenční informace](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Typ zprostředkovatele služby Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog týmu Azure Storage](https://blogs.msdn.com/b/windowsazurestorage/)
- [Konfigurace připojovacích řetězců](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Začínáme s Azure Table Storage v rozhraní .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
