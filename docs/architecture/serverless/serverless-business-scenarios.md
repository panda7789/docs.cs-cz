---
title: Ukázkové obchodní scénáře a případy použití pro aplikace bez serveru
description: Přístup k ukázkám, které jsou v rozsahu od zpracování obrazu do mobilních back-endu a ETL, se naučí bez serveru s praktickým přístupem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7024a33f8a7fccd6afa51c126454afedd87cceee
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834300"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Obchodní scénáře bez serveru a případy použití

K dispozici je mnoho případů použití a scénářů pro aplikace bez serveru. Tato kapitola obsahuje ukázky, které ilustrují různé scénáře. Scénáře obsahují odkazy na související dokumentaci a veřejné úložiště zdrojového kódu. Ukázky v této kapitole vám umožní začít pracovat s vlastními vytvářením a implementací řešení bez serveru.

## <a name="analyze-and-archive-images"></a>Analýza a archivace imagí

Tato ukázka demonstruje události bez serveru (Event Grid), pracovní postupy (aplikace logiky) a kód (Azure Functions). Také ukazuje, jak integrovat s jiným prostředkem, v tomto případě Cognitive Services pro analýzu obrázků.

Konzolová aplikace vám umožní předat odkaz na adresu URL na webu. Aplikace publikuje adresu URL jako zprávu služby Event Grid. Paralelně se aplikace funkcí bez serveru a aplikace logiky přihlásí k odběru zprávy. Aplikace funkcí bez serveru serializace image do úložiště objektů BLOB. Také ukládá informace v Azure Table Storage. Metadata uchovávají původní adresu URL obrázku a název obrázku objektu BLOB. Aplikace logiky spolupracuje s rozhraním API Custom Vision k analýze obrázku a vytvoření titulu generovaného počítačem. Titulek je uložen v tabulce metadat.

![Architektura pro analýzu a archivaci imagí](./media/image-processing-example.png)

Samostatná aplikace s jednou stránkou (SPA) volá funkci bez serveru, která umožňuje získat seznam imagí a metadat. Pro každý obrázek volá jinou funkci, která ukládá data imagí z archivu. Konečný výsledek je galerie s automatickými titulky.

![Galerie automatických obrázků](./media/automated-image-gallery.png)

Úplné úložiště a pokyny pro sestavení aplikace logiky jsou k dispozici zde: [připevnit Event gridu](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Mobilní klient pro různé platformy pomocí Xamarin. Forms a Functions

Podívejte se, jak implementovat jednoduchou službu Azure bez serveru na webovém portálu Azure nebo v aplikaci Visual Studio. Sestavte klienta pomocí Xamarin. Forms, který běží v Androidu, iOS a Windows. Aplikace se pak rozpraví na použití JavaScript Object Notation (JSON) jako komunikačního média mezi serverem a mobilními klienty pomocí back-endu bez serveru.

Další informace najdete v tématu [implementace jednoduché funkce Azure pomocí klienta Xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generování fotky s rozpoznáváním imagí bez serveru

Ukázka používá Azure Functions a Microsoft Cognitive Services Custom Vision Service k vygenerování fotomozaika ze vstupní image. Model se vyškole pro rozpoznávání imagí. Po nahrání se obrázek rozpoznává a hledá v Bingu. Původní obrázek se přeloží pomocí výsledků hledání.

![Fotka a mozaika Orlandu očí](./media/orlando-eye-both.png)

Model můžete například proškolit pomocí Orlanduch orientačních bodů, jako je Orlandu oči. Custom Vision rozpozná obrázek oka Orlandu a funkce vytvoří fotografii složenou z výsledků hledání obrázků Bingu pro "Orlandu oči".

Další informace najdete v tématu [Azure Functionse generátoru Photo Mosaic](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrace stávající aplikace do cloudu

Jak je popsáno v předchozích kapitolách, je běžné využívat N-vrstvou architekturu pro hostování vaší aplikace v místním prostředí. I když migrace prostředků "tak, jak jsou" pomocí virtuálních počítačů, představuje nejméně rizikové cesty ke cloudu, mnoho společností zvolí možnost použít příležitost k refaktorování svých aplikací. Naštěstí refaktoringu nemusí být úsilím "vše-nebo-Nothing". Je možné, že svou aplikaci migrujete a pak postupného nahradíte komponenty pomocí cloudových nativních protějšků.

Aplikace používá funkci proxy serveru Azure Functions k povolení refaktoringu koncového bodu ze starší verze místního kódu na koncový bod bez serveru.

![Architektura migrace](./media/migration-architecture.png)

Proxy poskytuje jeden koncový bod rozhraní API, který se aktualizuje, aby se přesměrovaly jednotlivé požadavky při jejich přesunu na funkce bez serveru.

Můžete si prohlédnout video, které projde celou migrací: [zvednutí a posunutí s Azure Functions bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102). Přístup k ukázkovému kódu: [Přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analyzovat soubor CSV a vložit do databáze

Extrakce, transformace a načítání (ETL) je společná obchodní funkce, která integruje různé systémy. Tradiční přístupy často zahrnují nastavení vyhrazených serverů FTP a pak nasazují naplánované úlohy pro účely analýzy souborů a jejich překladu pro použití v podniku. Architektura bez serveru usnadňuje práci, protože Trigger se může aktivovat při odeslání souboru. Azure Functions řeší úkoly, jako je ETL, prostřednictvím ideálního složení malých částí kódu, které se zaměřují na konkrétní problém.

![Snímek obrazovky, který zobrazuje proces analýzy sdíleného svazku clusteru.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Informace o zdrojovém a praktickém laboratorním prostředí najdete v článku [Import testovacího prostředí CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Zkrácení odkazů a sledování metrik

Propojte zkrácené nástroje, které původně pomohly kódovat adresy URL v krátkých příspěvcích na Twitteru, aby odpovídaly limitu 140 Zvětšily se tak, aby zahrnovaly několik způsobů použití, nejčastěji ke sledování všech kliknutí pro analýzy. Scénář připojení je zcela aplikace bez serveru, která spravuje vazby a metriky sestav.

Azure Functions slouží k obsluze jednostránkové aplikace (SPA), která umožňuje vložení dlouhé adresy URL a generování krátkých adres URL. Adresy URL jsou označeny pro sledování položek, jako jsou kampaně (témata) a středníky (například sociální sítě, na které jsou odkazy odesílány). Krátký kód je uložený v Azure Table Storage jako klíč, s dlouhou adresou URL jako s hodnotou. Po kliknutí na krátký odkaz vyhledá jiná funkce dlouhou adresu URL, pošle přesměrování a umístí informace o události do fronty. Jiná funkce Azure zpracuje frontu a umístí tyto informace do Azure Cosmos DB.

![Architektura zkratek propojení](./media/link-shortener-architecture.png)

Pak můžete vytvořit řídicí panel Power BI, abyste získali přehled o shromažďovaných datech. Na back-endu Application Insights poskytuje důležité metriky. Telemetrie zahrnuje, jak dlouho trvá, než se průměrný uživatel přesměruje a jak dlouho trvá přístup k Azure Table Storage.

![Příklad Power BI](./media/power-bi-example.png)

Úplné úložiště propojení s pokyny najdete tady: [zkrácení adresy URL bez serveru](https://github.com/jeremylikness/serverless-url-shortener). O zjednodušené verzi si můžete přečíst tady: [Azure Storage pro aplikace .NET bez serveru v řádu minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Ověření připojení zařízení pomocí příkazů pro odeslání

Ukázka se skládá z IoT Hub Azure a funkce Azure Functions. Nová zpráva v IoT Hub aktivuje funkci Azure Functions. Kód bez serveru odesílá stejný obsah zprávy zpátky do zařízení, které ho odeslalo. Projekt má veškerý kód a konfiguraci nasazení potřebné pro řešení.

Další informace najdete v tématu věnovaném nástroji [Azure IoT Hub příkazového testu](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Doporučené materiály

* [Generátor Azure Functions Photo Mosaic](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT Hub – příkazy pro odesílání](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Azure Storage pro aplikace .NET bez serveru v řádu minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
* [Přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [Import testovacího prostředí CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Připevnit Event gridu](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Implementace jednoduché funkce Azure Functions s klientem Xamarin. Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Přezvednutí a posunutí s využitím Azure Functions bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Zkrácení adresy URL bez serveru](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Předchozí](orchestration-patterns.md)@no__t – 1 –[Další](serverless-conclusion.md)
