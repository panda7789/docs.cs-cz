---
title: "Začínáme s Azure Queue storage pomocí F #"
description: "Azure fronty poskytují spolehlivé, asynchronní zasílání zpráv mezi součástmi aplikace. Cloud zasílání zpráv umožňuje nezávisle škálovat součásti vaší aplikace."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: f5ebdb3f3b50996a397c8420b773178493744d70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Začínáme s Azure Queue storage pomocí F # #

Azure Queue storage poskytuje cloudu zasílání zpráv mezi součástmi aplikace. Při navrhování aplikací pro škálování, součásti aplikace jsou často odpojené, tak, aby bylo možné škálovat nezávisle. Fronty úložiště poskytuje asynchronní zasílání zpráv pro komunikaci mezi součástmi aplikací, zda jsou spuštěny v cloudu, na ploše, na místním serveru nebo na mobilním zařízení. Queue storage také podporuje správu asynchronních úloh a pracovní toky procesu vytváření.

### <a name="about-this-tutorial"></a>O tomto kurzu

Tento kurz ukazuje, jak napsat kód F # pro některé běžné úlohy pomocí Azure Queue storage. Úlohy popsané zahrnují vytváření a odstraňování front a přidávání, čtení a odstraňování front zpráv.

Koncepční přehled služby queue storage, najdete v tématu [v příručce .NET pro úložiště](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Požadavky

Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).
Budete také potřebovat přístupový klíč k úložišti pro tento účet.

## <a name="create-an-f-script-and-start-f-interactive"></a>Vytvoření F # skript a spusťte F # interaktivní

Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #. Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `queues.fsx`, ve vašem vývojovém prostředí F #.

Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.

### <a name="add-namespace-declarations"></a>Přidání deklarace oborů názvů

Přidejte následující `open` příkazů do horní části `queues.fsx` souboru:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Získat připojovací řetězec

Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage. Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).

Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Je to ale **nedoporučuje** skutečných projekty. Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště. Vždycky pečlivě k ochraně klíče účtu úložiště. Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům. Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.

Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru. K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Použití nástroje Azure Configuration Manager není povinné. Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Analýza připojovacího řetězce

Chcete-li analyzovat připojovací řetězec, použijte:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Tato možnost vrátí `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Vytvoření klienta služby front

`CloudQueueClient` Vám umožňuje načíst fronty uložené v rámci Queue storage. Tady je jeden způsob, jak vytvořit klienta služby:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teď jste připravení psát kód, který načítá a zapisuje data do fronty úložiště.

## <a name="create-a-queue"></a>Vytvoření fronty

Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Vložit zprávu do fronty

Pokud chcete vložit zprávu do existující fronty, vytvořte nejdříve novou `CloudQueueMessage`. Pak zavolejte `AddMessage` metoda. A `CloudQueueMessage` můžete vytvořit buď z řetězce (ve formátu UTF-8) nebo `byte` pole takto:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Zobrazení náhledu další zprávy

Můžete prohlížet zprávy ve frontě, bez odebere ji z fronty voláním `PeekMessage` metoda.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Získat další zprávy pro zpracování

Můžete načíst zprávu na popředí fronty pro zpracování voláním `GetMessage` metoda.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Později označuje úspěšné zpracování zprávy pomocí `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Změna obsahu zpráv zařazených ve frontě

Můžete změnit obsah načtené zprávy přímo ve frontě. Pokud zpráva představuje pracovní úlohu, můžete tuto funkci použít k aktualizaci stavu pracovních úloh. Následující kód aktualizuje zprávy ve frontě o nový obsah a nastaví limit viditelnosti na jiné 60 sekund. Uloží stav práce spojený se zprávou a klient získá další minutu, aby pokračovat v práci na zprávě. Tímto způsobem může sledovat vícekrokového pracovní postupy pro zprávy ve frontě, aniž by bylo nutné začít znovu od začátku, pokud se nezdaří krok zpracování z důvodu selhání hardwaru nebo softwaru. Obvykle byste udržovali také počet opakování, a pokud zpráva je více než některé počet opakovat, odstranili byste ji. Je to ochrana proti zprávu, která nevyvolala chyby aplikace pokaždé, když je zpracován.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Zrušte další zprávy z fronty

Váš kód vyřazuje z fronty zpráv z fronty ve dvou krocích. Při volání `GetMessage`, získáte další zprávu ve frontě. Zpráva vrácená metodou `GetMessage` stane neviditelnou pro jakýkoli jiný kód čtení zpráv z této fronty. Ve výchozím nastavení tato zpráva zůstává neviditelná po dobu 30 sekund. K dokončení odebrání zprávy z fronty, musíte také zavolat `DeleteMessage`. Tento dvoukrokový proces odebrání zprávy zaručuje, pokud se váš kód se nepodaří zpracovat zprávu z důvodu selhání hardwaru nebo softwaru, jiná instance vašeho kódu můžete stejnou zprávu získat a zkuste to znovu. Váš kód zavolá metodu `DeleteMessage` pravým po zpracování zprávy.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Asynchronní pracovní postupy použít s běžnými rozhraním API Queue storage

Tento příklad ukazuje způsob použití pracovním postupu asynchronní s běžnými rozhraním API Queue storage.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Další možností pro vyřazování zpráv z fronty

Existují dva způsoby, jak můžete přizpůsobit načítání zpráv z fronty.
Nejprve můžete načíst dávku zpráv (až 32). Druhý můžete nastavit časový limit neviditelnosti delší nebo kratší, aby měl váš kód více nebo méně času na úplné zpracování jednotlivých zpráv. Následující příklad kódu používá `GetMessages` získat 20 zpráv v jednom volání a poté je zpracovává každou zprávu. Také nastaví časový limit neviditelnosti 5 minut pro každou zprávu. Všimněte si, že 5 minut začíná pro všechny zprávy ve stejnou dobu, takže po 5 minutách mít předán od volání `GetMessages`, všechny zprávy, které nebyly odstraněny, opět viditelné.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Získání délky fronty

Můžete získat odhadovaný počet zpráv ve frontě. `FetchAttributes` Metoda požádá službu front o načtení atributů fronty, včetně počtu zpráv. `ApproximateMessageCount` Vlastnost vrací poslední hodnotu načtenou `FetchAttributes` metoda bez volání služby front.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Odstranění fronty

Chcete-li odstranit frontu se všemi zprávami, které v ní, zavolejte `Delete` metoda pro objekt fronty.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Další kroky

Teď, když jste se naučili základy používání služby Queue storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště.

- [Klientská knihovna pro úložiště pro .NET – referenční informace](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [Typ zprostředkovatele úložiště Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog týmu Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/)
- [Konfigurace připojovacích řetězců](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [Referenční dokumentace rozhraní API REST](http://msdn.microsoft.com/library/azure/dd179355)
