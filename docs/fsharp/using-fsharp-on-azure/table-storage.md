---
title: 'Začínáme s Azure Table storage pomocí F #'
description: Ukládejte si strukturovaná data v cloudu pomocí Azure Table storage nebo Azure Cosmos DB.
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 50721ca44bbae5c52984b08a30bc87507fbf063d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Začínáme s Azure Table storage a Cosmos DB tabulky rozhraní API služby Azure pomocí F # # 

Azure Table storage je služba, která ukládá strukturovaná data typu NoSQL v cloudu. Úložiště Table je úložiště klíčů/atributů s návrhem. Protože úložiště Table nemá schéma, je snadné data přizpůsobovat potřebám vaší aplikace měnícím. Přístup k datům je rychlý a nákladově efektivní pro všechny typy aplikací. Table storage je obvykle znamená výrazně nižší náklady než tradiční SQL pro podobné objemy dat.

Úložiště tabulek můžete použít k ukládání flexibilních datových sad, například uživatelských dat pro webové aplikace, adresáře, informace o zařízení a jiný typ metadat, které vaše služba vyžaduje. V tabulce můžete uložit libovolný počet entit a účet úložiště může obsahovat libovolný počet tabulek, až do limitu kapacity účtu úložiště.

Azure Cosmos DB poskytuje rozhraní API tabulky pro aplikace, které jsou napsané pro Azure Table storage a které vyžadují premium možnosti, jako:

- To globální distribuce.
- Vyhrazené propustnost po celém světě.
- Jednociferné milisekundu latence v 99th percentil.
- Zaručit vysoká dostupnost.
- Automatické sekundární indexování.

Aplikace napsané pro Azure Table storage můžete migrovat do databáze Cosmos Azure pomocí rozhraní API tabulky beze změn kódu a využívat možnosti úrovně premium. Rozhraní API tabulka má k dispozici klientské sady SDK pro .NET, Java, Python a Node.js.

Další informace najdete v tématu [Úvod do rozhraní API služby Azure Cosmos DB tabulky](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>O tomto kurzu

Tento kurz ukazuje, jak napsat kód F # pro provést některé běžné úlohy pomocí Azure Table storage nebo Cosmos DB tabulky rozhraní API služby Azure, včetně vytváření a odstraňování tabulek a vkládání, aktualizaci, odstranění a dotazování dat v tabulce.

## <a name="prerequisites"></a>Požadavky

Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account) nebo [účet Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).


## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F # skript a spusťte F # interaktivní

Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #. Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `tables.fsx`, ve vašem vývojovém prostředí F #.

Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva. Provést akci pro `Microsoft.WindowsAzure.ConfigurationManager` k získání Microsoft.Azure oboru názvů.

### <a name="add-namespace-declarations"></a>Přidání deklarace oborů názvů

Přidejte následující `open` příkazů do horní části `tables.fsx` souboru:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Získat připojovací řetězec úložiště Azure

Pokud se připojujete ke službě Azure Storage Table, budete potřebovat připojovací řetězec pro účely tohoto kurzu. Připojovací řetězec můžete zkopírovat z portálu Azure. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Získání připojovacího řetězce Azure Cosmos DB

Pokud se připojujete k databázi Cosmos Azure, budete potřebovat připojovací řetězec pro účely tohoto kurzu. Připojovací řetězec můžete zkopírovat z portálu Azure. Na portálu Azure v účtu Cosmos DB, přejděte na **nastavení** > **připojovací řetězec**a klikněte na tlačítko **kopie** tlačítko Kopírovat primární připojení Řetězec. 

Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, jako v následujícím příkladu:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Je to ale **nedoporučuje** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždycky pečlivě k ochraně klíče účtu úložiště. Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.

Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

Chcete-li analyzovat připojovací řetězec, použijte:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Tento příkaz vrátí `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Vytvoření klienta služby Table

`CloudTableClient` Vám umožňuje načíst tabulky a entity ve službě Table storage. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teď jste připravení psát kód, který načítá a zapisuje data do úložiště tabulek.

### <a name="create-a-table"></a>Umožňuje vytvořit tabulku

Tento příklad ukazuje, jak vytvořit tabulku, pokud ještě neexistuje:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Přidání entity do tabulky

Entita musí mít typ, který dědí z `TableEntity`. Můžete rozšířit `TableEntity` v jakýmkoli způsobem se vám líbí, ale typ vašeho *musí* mít konstruktor bez parametrů. Pouze vlastnosti, které oba `get` a `set` jsou uložené v Azure Table.

Klíč entity oddílu a řádku entity jednoznačně identifikují entitu v tabulce. Entity se stejným klíčem oddílu můžete zadat dotaz rychleji než ty, které se různé klíče oddílů, ale používání různých klíčů oddílů umožňuje větší škálovatelnost paralelních operací.

Tady je příklad `Customer` používající `lastName` jako klíč oddílu a `firstName` jako klíč řádku.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Nyní přidejte `Customer` do tabulky. Chcete-li tak učinit, vytvořte `TableOperation` , která se spouští v tabulce. V tomto případě vytvoříte `Insert` operaci.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Vložení dávky entit

Do tabulky pomocí jednoho zápisu operace můžete vložit dávku entit. Dávkové operace umožňují kombinovat operací do jednoho spuštění, ale mají určitá omezení:

- Můžete provádět aktualizace, odstranění a vložení v rámci jedné dávkové operace.
- Dávková operace může obsahovat až 100 entit.
- Všechny entity v rámci dávkové operace musí mít stejný klíč oddílu.
- I když je možné provést dotaz v rámci dávkové operace, musí být ale jediná operace v dávce.

Zde je kód, který kombinuje dvě vloží do dávkové operace:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Načtení všech entit v oddílu

Dotaz na tabulku pro všechny entity v oddílu, použijte `TableQuery` objektu. Zde můžete filtr pro entity kde "Smith" je klíč oddílu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Nyní vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Načtení rozsahu entit v oddílu

Pokud nechcete, aby k dotazování všechny entity v oddílu, můžete zadat rozsah kombinací filtru klíče oddílu s filtrem klíče řádku. Tady můžete použít dva filtry k získání všech entit v oddílu "Smith" kde klíč řádku (jméno) začíná písmenem starší než "M" abecedy.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Nyní vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Načtení jedné entity

Můžete napsat dotaz pro načtení jedné konkrétní entity. Tady můžete použít `TableOperation` k určení zákazníka "Ben Smith". Místo kolekce, můžete se vrátit `Customer`. V dotazu zadat klíč oddílu a klíč řádku je nejrychlejší způsob, jak načíst jednu entitu ze služby Table.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Nyní vytisknout výsledky:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a>Nahrazení entity

Pokud chcete entitu aktualizovat, načtěte ji ze služby Table, upravte objekt entity a potom uložte změny zpět k tabulce služby pomocí `Replace` operaci. To způsobí, že entita, která má být plně nahradí na serveru, pokud se entita na serveru se změnil od načtení, v takovém případě se operace nezdaří. Je toto selhání zabrání vaší aplikaci v nechtěném přepsání změny z jiných zdrojů.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Vložení nebo nahrazení entity

V některých případech nevíte, zda entita existuje v tabulce. A pokud ano, aktuální hodnoty v ní uloženy už nejsou potřeba. Můžete použít `InsertOrReplace` vytvořit entitu, nebo ho nahradit, pokud existuje, bez ohledu na jeho stav.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Dotaz na podmnožinu vlastností entity

Dotaz na tabulku můžete načíst jenom několik z entity, místo všechny z nich. Tento postup volá projekce, může zlepšit výkon dotazů, hlavně pro velké entity. Zde můžete vrátit pouze e-mailových adres, pomocí `DynamicTableEntity` a `EntityResolver`. Všimněte si, že projekci nepodporuje emulátor místního úložiště, takže tento kód spustí pouze v případě, že používáte účet služby Table.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Načtení entit na stránkách asynchronně

Pokud načítáte velký počet entit a chcete je zpracovat, protože jsou načítány místo čekání mají všechny vrátí, můžete použít segmentovaného dotazu. Zde vracet výsledky na stránkách pomocí pracovním postupu asynchronní tak, aby provádění není blokován, zatímco čekáte pro velké sady výsledků vrátit.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Je teď spustit tento výpočet synchronně:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Odstranění entity

Entitu můžete po jejím načtení odstranit. Stejně jako u aktualizaci entity se to nezdaří, pokud entity došlo ke změně vzhledem k tomu, že jste jej získali.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Odstranění tabulky

Odstranit tabulku z účtu úložiště. Tabulka, která byla odstraněna není k dispozici pro určitou dobu po odstranění byla znovu vytvořena.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání služby Table storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště a rozhraní API služby Azure DB Cosmos tabulky.

- [Úvod do Azure Cosmos DB tabulky API](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Klientská knihovna pro úložiště pro .NET – referenční informace](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Typ zprostředkovatele úložiště Azure](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog týmu Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/)
- [Konfigurace připojovacích řetězců](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Začínáme s Azure Table Storage v rozhraní .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
