---
title: Začínáme s Azure Queue storage pomocíF#
description: Fronty Azure Queue poskytují spolehlivý asynchronní přenos zpráv mezi součástmi aplikace. Cloudový přenos zpráv umožňuje nezávislé škálování součástí vaší aplikace.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 58a46dfe905a32be77a13d11df8f0544546ea0ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756374"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Začínáme s Azure Queue storage s využitím F\#

Úložiště Azure Queue zajišťuje cloudový přenos zpráv mezi součástmi aplikace. Při navrhování aplikací pro škálování, komponenty aplikace bývají často oddělené, tak, aby se mohly škálovat nezávisle. Queue storage zajišťuje asynchronní přenos zpráv pro komunikaci mezi komponentami aplikace, ať už jsou spuštěné v cloudu, v klientských počítačích, na místním serveru nebo na mobilním zařízení. Queue storage také podporuje správu asynchronních úloh a vytváření pracovních postupů pro procesy.

### <a name="about-this-tutorial"></a>O tomto kurzu

Tento kurz ukazuje, jak napsat F# kód pro některé běžné úlohy pomocí Azure Queue storage. Úlohy popsané patří vytváření a odstraňování front a přidávání, čtení a odstraňování front zpráv.

Koncepční přehled služby queue storage, najdete v tématu [v příručce .NET pro úložiště fronty](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Požadavky

K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account).
Budete také potřebovat přístupový klíč k úložišti pro tento účet.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skript a spustit F# interaktivní

Ukázky v tomto článku můžete použít buď F# aplikace nebo F# skriptu. Vytvoření F# skript, vytvořte soubor s `.fsx` příponu, třeba `queues.fsx`v vaše F# vývojové prostředí.

Pak pomocí [Správce balíčků](package-management.md) jako [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a odkaz na `WindowsAzure.Storage.dll` ve skriptu pomocí `#r`směrnice.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte následující `open` příkazy k hornímu okraji `queues.fsx` souboru:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro účely tohoto kurzu budete potřebovat připojovací řetězec služby Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).

Pro tento kurz zadáte svůj připojovací řetězec ve vašem skriptu, například takto:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Je to ale **ale nedoporučený krok** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.

Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce, použijte:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Vrátí `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Vytvoření klienta služby front

`CloudQueueClient` Třída umožňuje načíst fronty uložené v rámci Queue storage. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Nyní jste připraveni napsat kód, který čte data z a zapisuje data do fronty úložiště.

## <a name="create-a-queue"></a>Vytvoření fronty

Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Vložit zprávu do fronty

Chcete-li vložit zprávu do existující fronty, vytvořte nejdřív nový `CloudQueueMessage`. Pak zavolejte `AddMessage` metody. A `CloudQueueMessage` lze vytvořit buď z řetězce (ve formátu UTF-8) nebo `byte` pole, například takto:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Zobrazení náhledu další zprávy

Můžete prohlížet zprávy ve frontě, bez odebrání z fronty, voláním `PeekMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Získat další zprávy pro zpracování

Můžete získat zprávu na začátku fronty pro zpracování voláním `GetMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Později označují úspěšné zpracování zprávy s použitím `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Změna obsahu zpráv zařazených ve frontě

Můžete změnit obsah načtených zpráv na místě ve frontě. Pokud zpráva představuje pracovní úlohu, můžete tuto funkci použít k aktualizaci stavu pracovních úloh. Následující kód aktualizuje zprávy ve frontě o nový obsah a nastaví časový limit viditelnosti na jiné 60 sekund. Uloží stav práce spojený se zprávou a klient získá další minutu chcete pokračovat v práci na zprávu. Tímto způsobem může sledovat vícekrokového pracovní postupy zprávy ve frontě, aniž by bylo nutné začít znovu od začátku, pokud se nezdaří krok zpracování z důvodu selhání hardwaru nebo softwaru. Obvykle byste udržovali také hodnotu počtu opakování, a pokud zpráva je více než několik počet, kolikrát opakovat, odstranili byste ji. Je to ochrana proti zprávu, která nevyvolala chyby aplikace pokaždé, když se zpracovává.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Zrušit další zprávy z fronty

Váš kód zrušení fronty zpráv z fronty ve dvou krocích. Při volání `GetMessage`, získáte další zprávu ve frontě. Zpráva vrácená metodou `GetMessage` stane neviditelnou pro jakýkoli jiný kód přečte zprávy z této fronty. Ve výchozím nastavení tato zpráva zůstává neviditelná po dobu 30 sekund. K dokončení odebrání zprávy z fronty, musíte také zavolat `DeleteMessage`. Tento dvoukrokový proces odebrání zprávy zaručuje, že pokud váš kód se nepodaří zpracovat zprávu z důvodu selhání hardwaru nebo softwaru, jiná instance vašeho kódu můžete získat stejná zpráva a zkuste to znovu. Váš kód zavolá `DeleteMessage` hned po zpracování zprávy.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Použití asynchronní pracovní postupy s běžnými rozhraním API Queue storage

Tento příklad ukazuje způsob použití asynchronního pracovního postupu s běžnými rozhraním API Queue storage.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Další možností pro vyřazování zpráv z fronty

Existují dva způsoby, jak můžete přizpůsobit načtení zprávy z fronty.
Nejprve můžete načíst dávku zpráv (až 32). Za druhé můžete nastavit časový limit neviditelnosti delší nebo kratší, umožňuje váš kód více nebo méně času na úplné zpracování jednotlivých zpráv. Následující příklad kódu používá `GetMessages` 20 zpráv v jednom volání a poté zpracuje každou zprávu. Také nastaví časový limit neviditelnosti 5 minut pro každou zprávu. Všimněte si, že začíná pro všechny zprávy ve stejnou dobu, tak po mít 5 minut předané od posledního volání `GetMessages`, všechny zprávy, které nebyly odstraněny, opět viditelné.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Získání délky fronty

Můžete získat odhadovaný počet zpráv ve frontě. `FetchAttributes` Metoda požádá službu front o načtení atributů fronty, včetně počtu zpráv. `ApproximateMessageCount` Vlastnost vrací poslední hodnotu načtenou `FetchAttributes` metody, bez volání služby front.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Odstranění fronty

Chcete-li odstranit frontu se všemi zprávami, které v ní, zavolejte `Delete` metodu na objekt fronty.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání služby Queue storage, použijte tyto odkazy na další informace o složitějších úlohách úložiště.

- [Rozhraní API služby Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Typ zprostředkovatele služby Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog týmu Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Nakonfigurování připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Reference k rozhraní REST API služby Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
