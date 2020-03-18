---
title: Ukázka obchodních scénářů a případů použití aplikací bez serveru
description: Naučte se bez serveru s praktickým přístupem k ukázkám, které sahají od zpracování obrazu až po mobilní back-endy a kanály ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787884"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Obchodní scénáře aplikací bez serveru a případy použití

Existuje mnoho případů použití a scénáře pro aplikace bez serveru. Tato kapitola obsahuje ukázky, které ilustrují různé scénáře. Scénáře zahrnují odkazy na související dokumentaci a úložiště veřejného zdrojového kódu. Ukázky v této kapitole vám umožní začít pracovat s vlastní sestavením a implementovat řešení bez serveru.

## <a name="analyze-and-archive-images"></a>Analýza a archivace obrázků

Tato ukázka ukazuje události bez serveru (Event Grid), pracovní postupy (aplikace logiky) a kód (Funkce Azure). Také ukazuje, jak integrovat s jiným prostředkem, v tomto případě Cognitive Services pro analýzu obrázků.

Konzolová aplikace umožňuje předat odkaz na adresu URL na webu. Aplikace publikuje adresu URL jako zprávu mřížky událostí. Souběžně aplikace funkce bez serveru a aplikace logiky přihlásit ke zprávě. Aplikace funkce bez serveru serializuje bitovou kopii do úložiště objektů blob. Ukládá také informace ve službě Azure Table Storage. Metadata uloží původní adresu URL obrázku a název bitové kopie objektu blob. Aplikace logiky spolupracuje s rozhraním API pro vlastní vizi, aby analyzovala bitovou kopii a vytvořila popisek generovaný počítačem. Titulek je uložen v tabulce metadat.

![Analýza a archivace architektury obrázků](./media/image-processing-example.png)

Samostatná jednostránková aplikace (SPA) volá funkci bez serveru, aby získala seznam obrázků a metadat. Pro každý obrázek volá jinou funkci, která doručuje obrazová data z archivu. Konečným výsledkem je galerie s automatickými titulky.

![Automatická galerie obrázků](./media/automated-image-gallery.png)

Úplné úložiště a pokyny k vytvoření aplikace logiky jsou k dispozici zde: [Připojení mřížky událostí](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Mobilní klient napříč platformami využívající Xamarin.Forms a funkce

Podívejte se, jak implementovat jednoduchou funkci Azure bez serveru na Webu Azure Portal nebo ve Visual Studiu. Vytvořte klienta s Xamarin.Forms, který běží na Android, iOS a Windows. Aplikace je pak rafinována tak, aby používala JavaScriptOvý zápis objektu (JSON) jako komunikační médium mezi serverem a mobilními klienty s back-endem bez serveru.

Další informace naleznete [v tématu Implementace jednoduché funkce Azure s klientem Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Generování fotomozaiky s rozpoznáváním obrazu bez serveru

Ukázka používá Azure Functions a Microsoft Cognitive Services Custom Vision Service ke generování foto mozaiky ze vstupní bitové kopie. Model je trénován k rozpoznání obrázků. Když je obrázek nahrán, rozpozná ho a vyhledá pomocí bingu. Původní obrázek se znovu složí pomocí výsledků hledání.

![Orlando oko fotografie a mozaika](./media/orlando-eye-both.png)

Můžete například trénovat model s památkami Orlando, jako je Orlando Eye. Vlastní vize rozpozná obraz Orlando Eye a funkce vytvoří fotomozaiku složenou z výsledků vyhledávání obrázků Bing pro "Orlando Eye".

Další informace naleznete v [tématu Azure Functions foto mozaika generátor](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrace existující aplikace do cloudu

Jak je popsáno v předchozích kapitolách, je běžné přijmout n-vrstvé architektury pro hostování vaší aplikace v místním prostředí. Přestože migrace prostředků "tak, jak jsou" pomocí virtuálních počítačů je nejméně riskantní cestu ke cloudu, mnoho společností se rozhodnou využít příležitosti k refaktorování jejich aplikací. Naštěstí refaktoring nemusí být "vše-nebo-nic" úsilí. Ve skutečnosti je možné migrovat aplikaci a pak postupně nahradit komponenty cloudovými nativními protějšky.

Aplikace používá funkci proxy serverů Funkce Azure k povolení refaktoringu koncového bodu z původního místního kódu do koncového bodu bez serveru.

![Architektura migrace](./media/migration-architecture.png)

Proxy server poskytuje jeden koncový bod rozhraní API, který je aktualizován tak, aby přesměroval jednotlivé požadavky při jejich přesunu do funkcí bez serveru.

Můžete zobrazit video, které vás provede celou migrací: [Zvedejte a posuňte se pomocí funkcí Azure bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102). Přístup k ukázkovému kódu: [Přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analýza souboru CSV a vložení do databáze

Extrakce, transformace a zatížení (ETL) je běžná obchodní funkce, která integruje různé systémy. Tradiční přístupy často zahrnují nastavení vyhrazených serverů FTP a nasazení naplánovaných úloh za účelem analýzy souborů a jejich překladu pro obchodní použití. Architektura bez serveru usnadňuje úlohu, protože aktivační událost může spustit při nahrání souboru. Azure Functions řeší úkoly, jako je ETL prostřednictvím jeho ideální složení malé kousky kódu, které se zaměřují na konkrétní problém.

![Snímek obrazovky, který zobrazuje proces analýzy csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Zdrojový kód a praktická laboratoř naleznete v tématu [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Zkrácení odkazů a sledování metrik

Nástroje pro zkrácení odkazů původně pomohly zakódovat adresy URL v krátkých příspěvcích na Twitteru, aby se přizpůsobily limitu 140 znaků. Rozrostly se tak, aby zahrnovaly několik použití, nejčastěji pro sledování prokliků pro analýzy. Scénář zkracovače odkazů je zcela bezserverová aplikace, která spravuje odkazy a sestavy metriky.

Funkce Azure se používá k poskytování jednostránkové aplikace (SPA), která umožňuje vložit dlouhou adresu URL a generovat krátké adresy URL. Adresy URL jsou označeny pro sledování věcí, jako jsou kampaně (témata) a média (například sociální sítě, na které jsou odkazy zveřejněny). Krátký kód se ukládá v Azure Table Storage jako klíč, s dlouhou adresu URL jako hodnotu. Když kliknete na krátký odkaz, jiná funkce vyhledá dlouhou adresu URL, odešle přesměrování a umístí informace o události do fronty. Jiná funkce Azure zpracuje frontu a umístí informace do Azure Cosmos DB.

![Architektura zkracovače odkazů](./media/link-shortener-architecture.png)

Pak můžete vytvořit řídicí panel Power BI, abyste získali přehledo shromážděných dat. Na back-end, Application Insights poskytuje důležité metriky. Telemetrie zahrnuje, jak dlouho trvá pro průměrného uživatele k přesměrování a jak dlouho trvá přístup k Azure Table Storage.

![Příklad Power BI](./media/power-bi-example.png)

Kompletní link shortener repozitář s pokyny je k dispozici zde: [Zkracovač BEZ serveru URL](https://github.com/jeremylikness/serverless-url-shortener). O zjednodušené verzi si můžete přečíst zde: [Azure Storage pro aplikace .NET bez serveru během několika minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Ověření připojení zařízení pomocí příkazu ping

Ukázka se skládá z azure iot hub a funkce Azure. Nová zpráva v centru IoT Hub aktivuje funkci Azure. Kód bez serveru odešle stejný obsah zprávy zpět do zařízení, které jej odeslané. Projekt má veškerý kód a konfiguraci nasazení potřebnou pro řešení.

Další informace najdete v [tématu Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Doporučené zdroje

- [Generátor fotomozaiky Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Ping služby Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Azure Storage pro aplikace .NET bez serveru během několika minut](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Přineste si vlastní aplikaci](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Testovací laboratoř importu CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Připevnění mřížky událostí](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implementace jednoduché funkce Azure s klientem Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Zvedat a posouvat pomocí funkcí Azure bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Zkracovač adres URL bez serveru](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Předchozí](orchestration-patterns.md)
>[další](serverless-conclusion.md)
