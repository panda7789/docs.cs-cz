---
title: Začínáme se službou Azure Queue Storage s využitím F#
description: Fronty Azure Queue poskytují spolehlivý asynchronní přenos zpráv mezi součástmi aplikace. Cloudový přenos zpráv umožňuje nezávislé škálování součástí vaší aplikace.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 841068ac91aecc53811359e27d984907569a2c6d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935498"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Začínáme s úložištěm Azure Queue pomocí jazyka F\#

Úložiště Azure Queue zajišťuje cloudový přenos zpráv mezi součástmi aplikace. Při navrhování aplikací pro škálování ve větším měřítku jsou jednotlivé součásti aplikací často nepropojené, aby je bylo možné škálovat nezávisle. Queue Storage zajišťuje asynchronní přenos zpráv pro komunikaci mezi součástmi aplikace bez ohledu na to, jestli běží v cloudu, na desktopu, na místním serveru nebo na mobilním zařízení. Queue Storage také podporuje správu asynchronních úloh a pracovní postupy procesů sestavování buildů.

### <a name="about-this-tutorial"></a>O tomto kurzu

V tomto kurzu se dozvíte F# , jak napsat kód pro některé běžné úlohy pomocí služby Azure Queue Storage. Mezi zahrnuté úlohy patří vytváření a odstraňování front a přidávání, čtení a odstraňování zpráv fronty.

Koncepční přehled služby Queue Storage najdete v [příručce .NET pro úložiště Queue](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Požadavky

Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Pro tento účet budete taky potřebovat přístupový klíč k úložišti.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F# skriptu a spuštění F# Interactive

Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu. Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `queues.fsx`ve vašem F# vývojovém prostředí.

V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve vašem skriptu pomocí direktivy `#r`.

### <a name="add-namespace-declarations"></a>Přidání deklarací oboru názvů

Přidejte do horní části souboru `queues.fsx` následující příkazy `open`:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Získání připojovacího řetězce

Pro tento kurz budete potřebovat připojovací řetězec Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).

V tomto kurzu do skriptu zadáte svůj připojovací řetězec, například:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

To však **nedoporučujeme** pro skutečné projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždy klíč účtu úložiště pečlivě chraňte. Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům. Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.

Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru. Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

K analýze připojovacího řetězce použijte:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Tato akce vrátí `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Vytvoření klienta Služby front

Třída `CloudQueueClient` umožňuje načítat fronty uložené v úložišti front. Tady je jeden ze způsobů, jak vytvořit klienta služby:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teď můžete napsat kód, který bude číst data z Queue Storage a bude je tam také zapisovat.

## <a name="create-a-queue"></a>Umožňuje vytvořit frontu.

Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Vložení zprávy do fronty

Chcete-li vložit zprávu do existující fronty, vytvořte nejprve novou `CloudQueueMessage`. Dále zavolejte metodu `AddMessage`. `CloudQueueMessage` lze vytvořit buď pomocí řetězce (ve formátu UTF-8), nebo pole `byte`, například takto:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Zobrazení náhledu další zprávy

Můžete prohlížet zprávy před frontou, aniž byste je odebrali z fronty, voláním metody `PeekMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Získat další zprávu ke zpracování

Zprávu můžete načíst na začátku fronty ke zpracování voláním metody `GetMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Později označíte úspěšné zpracování zprávy pomocí `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Změna obsahu zpráv zařazených ve frontě

Obsah načtené zprávy můžete změnit na místě ve frontě. Pokud zpráva představuje pracovní úlohu, mohli byste tuto funkci použít k aktualizaci stavu pracovních úloh. Následující kód aktualizuje zprávy ve frontě o nový obsah a prodlouží časový limit viditelnosti na 60 sekund. Uloží se tím stav práce spojený se zprávou a klient získá další minutu, aby mohl pokračovat ve zpracování zprávy. Tímto způsobem může sledovat vícekrokového pracovní postupy pro zprávy ve frontě, aniž by bylo nutné v případě, že krok zpracování z důvodu selhání hardwaru nebo softwaru selže, začít znovu od začátku. Obvykle byste zachovali počet opakování i v případě, že se zpráva znovu pokusí o více než pár časů, takže byste ji odstranili. Je to ochrana proti tomu, aby zpráva při každém pokusu o zpracování nevyvolala chyby aplikace.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Vyřazení další zprávy z fronty

Váš kód vyřazuje zprávy z fronty ve dvou krocích. Když zavoláte `GetMessage`, dostanete další zprávu ve frontě. Zpráva vrácená z `GetMessage` bude neviditelná pro jakýkoliv jiný kód, který čte zprávy z této fronty. Ve výchozím nastavení tato zpráva zůstává neviditelná po dobu 30 sekund. Chcete-li dokončit odebrání zprávy z fronty, je nutné také volat `DeleteMessage`. Tento dvoukrokový proces odebrání zprávy zaručuje, aby v případě, že se vašemu kódu nepodaří zprávu zpracovat z důvodu selhání hardwaru nebo softwaru, mohla stejnou zprávu získat jiná instance vašeho kódu a bylo možné to zkusit znovu. Váš kód volá `DeleteMessage` hned po zpracování zprávy.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Použití asynchronních pracovních postupů s rozhraními API služby Common Queue Storage

Tento příklad ukazuje, jak použít asynchronní pracovní postup s běžnými rozhraními API služby Queue Storage.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Další možnosti pro zprávy o zrušení fronty

Načítání zpráv z fronty si můžete přizpůsobit dvěma způsoby.
Za prvé si můžete načíst dávku zpráv (až 32). Za druhé si můžete nastavit delší nebo kratší časový limit neviditelnosti, aby měl váš kód více nebo méně času na úplné zpracování jednotlivých zpráv. Následující příklad kódu používá `GetMessages` k získání 20 zpráv v jednom volání a pak zpracovává každou zprávu. Také se pro každou zprávu nastaví časový limit neviditelnosti 5 minut. Všimněte si, že 5 minut začne u všech zpráv současně, takže po uplynutí 5 minut od volání `GetMessages`se všechny zprávy, které nebyly odstraněny, opět zobrazí.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Získání délky fronty

Podle potřeby můžete získat odhadovaný počet zpráv ve frontě. Metoda `FetchAttributes` požádá Služba front o načtení atributů fronty, včetně počtu zpráv. Vlastnost `ApproximateMessageCount` vrací poslední hodnotu získanou metodou `FetchAttributes` bez volání Služba front.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Odstranění fronty

Pokud chcete odstranit frontu a všechny zprávy, které jsou v ní obsažené, zavolejte metodu `Delete` u objektu Queue.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání služby Queue Storage, podívejte se na následujících odkazech na další informace o složitějších úlohách úložiště.

- [Rozhraní API služby Azure Storage pro .NET](/dotnet/api/overview/azure/storage)
- [Poskytovatel typu Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog týmu Azure Storage](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [Nakonfigurování připojovacích řetězců Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Referenční informace k rozhraní REST API služby Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
