---
title: Ukázka obchodní scénáře a případy použití pro aplikace bez serveru
description: Zjistěte, bez serveru pomocí praktických přístup díky přístupu do ukázky, které v rozsahu od zpracování obrázků a mobilní back-EndY, kanály ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c38d1c6c4e04f3fa38946c97af5d94758b3ed6f7
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404902"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Bez serveru obchodní scénáře a případy použití

Existuje mnoho případy použití a scénáře pro aplikace bez serveru. Tato kapitola obsahuje ukázky, které demonstrují různé scénáře. Scénáře zahrnují odkazy na související dokumentaci a veřejných úložišť zdrojového kódu. Příklady v této kapitole umožňují snadno začít vlastními silami, vytváření a implementaci řešení bez serveru.

## <a name="analyze-and-archive-images"></a>Analýza a archivní úrovně imagí

Tato ukázka demonstruje bez serveru událostí (Event Grid), pracovní postupy (aplikace logiky) a kódu (funkce Azure). Také ukazuje, jak zajistit integraci s jiným prostředkem ve tomto případu služeb Cognitive Services pro analýzu obrázků.

Konzolová aplikace umožňuje předání odkazem na adresu URL na webu. Aplikace publikuje adresy URL jako zpráva event grid. Aplikace bez serveru function app a aplikaci logiky předplatit paralelně, zprávy. Aplikace bez serveru funkcí serializuje obrázku do blob storage. Také ukládá informace ve službě Azure Table Storage. Metadata ukládá původní adresa URL obrázku a název objektu blob obrázku. Aplikace logiky komunikuje s vlastní rozhraní API pro zpracování obrazu k analýze image a vytvořte počítačem generované titulek. Popisek je uložena v tabulce metadat.

![Analýza a archivní úrovně Architektura bitové kopie](./media/image-processing-example.png)

Samostatné jednostránkové aplikaci (SPA) volá funkci bez serveru k získání seznamu imagí a metadata. Pro každý obrázek volá jinou funkci, která poskytuje data bitové kopie z archivu. Konečný výsledek je Galerie s automatických popisků.

![Automatizované image Galerie](./media/automated-image-gallery.png)

Úplné úložiště a pokyny k sestavení aplikace logiky najdete tady: [Event grid připevnit](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>– Multiplatformního mobilního klienta pomocí Xamarin.Forms a funkce

Zjistit, jak implementovat jednoduché funkci Azure Functions na webovém portálu Azure nebo v sadě Visual Studio. Vytvoření klienta s Xamarin.Forms, která běží na Android, iOS a Windows. Aplikace se pak vylepšili o zápis JSON (JavaScript Object) jako médium komunikace mezi serverem a mobilní klienty s bez serveru back-end.

Další informace najdete v tématu [implementace jednoduchou funkci Azure s klientem Xamarin.Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generovat mosaic fotky na základě rozpoznávání obrázků bez serveru

Ukázka používá Azure Functions a Microsoft Cognitive Services Custom Vision Service k vygenerování mosaic fotografií ze vstupního obrázku. Model se trénuje rozpoznat bitové kopie. Po nahrání obrázku rozpozná bitovou kopii a hledá s Bingem. Původní bitové kopie je opětovně zkomponovat, pomocí seznamu výsledků.

![Orlando oka fotografii a která](./media/orlando-eye-both.png)

Můžete například trénování modelu pomocí památek Orlando, jako je například oka Orlando. Custom Vision rozpozná obrázek oka Orlando, a funkce vytvoří mosaic fotografii skládá z Bingu výsledky hledání obrázků pro "Orlando očí."

Další informace najdete v tématu [Azure Functions fotografii mosaic generátor](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrovat existující aplikace do cloudu

Jak je popsáno v předchozích kapitol, je běžné a využívat N-vrstvou architekturu pro hostování aplikací na místní. I když migrace prostředků "tak jak jsou" pomocí virtuálních počítačů je minimální rizikové cestou ke cloudu, mnoho společností se rozhodnete použít příležitost k refaktorování svých aplikací. Naštěstí refaktoring nemusí být "rigidní" úsilí. Ve skutečnosti je možné migrovat aplikace pak piecemeal nahradit komponenty cloud nativní protějšky.

Aplikace používá funkci proxy služby Azure Functions umožňuje refaktoring koncového bodu ze starší verze místních kódu bez serveru koncový bod.

![Architektura migrace](./media/migration-architecture.png)

Proxy server poskytuje jeden koncový bod rozhraní API, která se aktualizovala na přesměrování jednotlivých požadavků, jak se přesunout do funkce bez serveru.

Můžete zobrazit video, které vás provede celou migrace: [Lift and shift s využitím Azure functions bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102). Přístup k vzorového kódu: [přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analyzovat soubor CSV a vložit do databáze

Extrakce, transformace a načítání (ETL) je běžné obchodní funkce, která integruje různé systémy. Tradiční přístupy často zahrnuje nastavení vyhrazené servery FTP a nasazení naplánované úlohy, které chcete analyzovat soubory a překládat je pro použití v podniku. Architektura bez serveru usnadňuje úlohy, protože aktivační událost může aktivovat při nahrání souboru. Azure Functions probere úkoly, jako jsou ETL prostřednictvím jeho ideální složení malé části kódu, které se soustředí na konkrétní problém.

![Architektura ETL](./media/csvimport.png)

Zdrojový kód a praktických cvičení, naleznete v tématu [CSV importovat lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Zkraťte odkazy a sledujte metriky

Odkaz zkrácením nástroje původně pomohla kódování adresy URL v krátkých twitterové příspěvky tak, aby vyhovovaly limitu 140 znaků. Jejich podporu jsme kvůli zahrnuje několik využití, nejčastěji sledovat kliknutí pro analýzu. Scénář odkazu zkracování adres je aplikace úplně bez serveru, která sestavy metrik a spravuje odkazy.

Služba Azure Functions se používají k předávání jedné stránce aplikace (SPA), která umožňuje vložit dlouhé adresy URL a generovat krátké adresy URL. Adresy URL jsou označené můžete sledovat třeba kampaně (témata) a média (například sociálními sítěmi, které odkazy jsou odeslány do). Krátký kód je uložen ve službě Azure Table Storage jako klíč s dlouhé adresy URL jako hodnotu. Po kliknutí na krátký odkaz, jiné funkci vyhledá dlouhé adresy URL, odešle přesměrování a umístí informace o události do fronty. Jiná služba Azure Function požadavky ve frontě zpracovává a umístí informace do služby Azure Cosmos DB.

![Architektura zkracování adres odkaz](./media/link-shortener-architecture.png)

Potom můžete vytvořit řídicí panel Power BI k získání přehledu o shromážděná data. Na back-endu Application Insights poskytuje důležité metriky. Telemetrická data zahrnují jak dlouho trvá průměrná uživatele pro přesměrování a dobu potřebnou pro přístup k Azure Table Storage.

![Příklad Power BI](./media/power-bi-example.png)

Úložiště zkracování adres se úplné propojení s pokyny je k dispozici tady: [bez serveru URL shortener](https://github.com/jeremylikness/serverless-url-shortener). Informace o zjednodušenou verzi: [Azure Storage pro .NET aplikace bez serveru v minutách](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Ověřte připojení zařízení pomocí odeslání příkazu ping

Ukázka se skládá z centra IoT Azure a funkce Azure functions. Funkce Azure Functions se aktivuje novou zprávu ve službě IoT Hub. Kód bez serveru pošle stejná zpráva obsahu zpět do zařízení, která ji odeslala. Projekt má všechny kódu a nasazení konfigurace potřebná pro řešení.

Další informace najdete v tématu [ping služby Azure IoT Hub](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Azure Functions fotografii mosaic generátor](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Azure Storage pro .NET aplikace bez serveru v minutách](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [Přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [Import CSV testovacího prostředí](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Event grid připevnit](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Implementace jednoduchého funkce Azure Functions s klientem Xamarin.Forms](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Výtah a posunout s využitím Azure functions bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Bez serveru zkracování adres URL](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
[Předchozí](orchestration-patterns.md)
[další](serverless-conclusion.md)