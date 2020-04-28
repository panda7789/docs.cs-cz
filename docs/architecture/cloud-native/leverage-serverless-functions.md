---
title: Využití bezserverových funkcí
description: Využití bez serveru a Azure Functions v cloudových nativních aplikacích
ms.date: 04/13/2020
ms.openlocfilehash: 176499e3cd0349cd689b9d13d1c237a6343d13f3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199739"
---
# <a name="leveraging-serverless-functions"></a>Využití bezserverových funkcí

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V rámci spektra od správy fyzických počítačů po využití cloudových možností bez serveru na extrémním konci. Vaše jediná odpovědnost je váš kód a platíte jenom při spuštění kódu. Azure Functions poskytuje způsob, jak sestavovat možnosti bez serveru do nativních aplikací pro Cloud.

## <a name="what-is-serverless"></a>Co je bez serveru?

Bez serveru je poměrně novým modelem služby cloud computingu. Neznamená to, že jsou servery volitelné – váš kód pořád běží na serveru někam. Rozdíl je v tom, že se tým aplikace již netýká správy serverové infrastruktury. Místo toho dodavatel cloudu tuto zodpovědnost vlastní. Vývojový tým zvyšuje svou produktivitu díky doručování podnikových řešení zákazníkům, ne při přípravě na domovníing.

Výpočetní prostředí bez serveru používá pro hostování služeb nestavové kontejnery s událostmi. Můžou škálovat a v závislosti na potřebě požadavků. Platformy bez serveru, jako je Azure Functions, mají úzkou integraci s dalšími službami Azure, jako jsou fronty, události a úložiště.

## <a name="what-challenges-are-solved-by-serverless"></a>Jaké problémy řeší bez serveru?

Platformy bez serveru řeší mnoho časově náročných a nákladných otázek:

- Nákup počítačů a licencí softwaru
- Ubytování, zabezpečení, konfigurace a údržba počítačů a jejich požadavků na síť, výkon a/C
- Opravy a upgrade operačních systémů a softwaru
- Konfigurace webových serverů nebo služeb počítače pro hostování aplikačního softwaru
- Konfigurace aplikačního softwaru v rámci své platformy

Mnoho společností přiděluje velké rozpočty na podporu týkající se hardwarové infrastruktury. Přechod do cloudu může snížit náklady. posunutí aplikací na bez serveru může přispět k jejich odstranění.

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>Jaký je rozdíl mezi mikroslužbou a funkcí bez serveru?

Mikroslužba obvykle zapouzdřuje obchodní schopnost, jako je například nákupní košík pro online web elektronického obchodování. Zpřístupňuje více operací, které umožní uživateli spravovat své možnosti nákupu. Funkce je však malý, odlehčený blok kódu, který spouští operace s jedním účelem v reakci na událost.
Mikroslužby jsou obvykle vytvořené tak, aby reagovaly na žádosti, často z rozhraní. Požadavky mohou být založené na protokolu HTTP REST nebo gRPC. Služby bez serveru reagují na události. Jeho architektura řízená událostmi je ideální pro zpracování krátkodobě spuštěných úloh na pozadí.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Jaké scénáře jsou vhodné pro bez serveru?

Bez serveru zveřejňuje jednotlivé krátkodobé běžící funkce, které jsou vyvolány v reakci na Trigger. Díky tomu jsou ideální pro zpracování úloh na pozadí.

Aplikace může potřebovat poslat e-mail jako krok v pracovním postupu. Místo odeslání oznámení v rámci žádosti mikroslužeb umístěte podrobnosti zprávy do fronty. Funkce Azure může vyřadit zprávu do fronty a asynchronně odeslat e-mail. To by mohlo zlepšit výkon a škálovatelnost mikroslužby. [Vyrovnávání zátěže založené na frontách](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) se dá implementovat, aby nedocházelo k problémům při posílání e-mailů. Tato samostatná služba se navíc dá znovu použít jako nástroj pro celou řadu různých aplikací.

Asynchronní zasílání zpráv z front a témat je běžným vzorem pro aktivaci funkcí bez serveru. Azure Functions se ale můžou aktivovat jinými událostmi, jako jsou třeba změny v Azure Blob Storage. Služba, která podporuje nahrávání imagí, může mít za účelem optimalizace velikosti obrázku zodpovědnost funkce Azure. Funkci lze aktivovat přímo vložením do služby Azure Blob Storage, což zachovává složitost operací mikroslužeb.

Mnohé služby mají dlouhotrvající procesy v rámci svých pracovních postupů. Tyto úlohy jsou často prováděny v rámci interakce uživatele s aplikací. Tyto úlohy můžou vynutit, aby uživatel čekal a negativně ovlivnil své zkušenosti. Computing bez serveru poskytuje skvělý způsob, jak přesunout pomalejší úlohy mimo smyčku interakce uživatele. Tyto úlohy se můžou škálovat na vyžádání bez nutnosti škálovat celou aplikaci.

## <a name="when-should-you-avoid-serverless"></a>Kdy byste se měli vyhnout bez serveru?

Řešení bez serveru jsou zajišťována a škálovatelná na vyžádání. Při vyvolání nové instance se jedná o běžný problém Starter. Studené zahájení je doba potřebná k zajištění této instance. Obvykle může tato prodleva trvat několik sekund, ale může to trvat v závislosti na různých faktorech. Po zřízení se jedna instance udržuje jako aktivní, dokud obdrží pravidelné požadavky. Pokud je však služba volána méně často, může ji Azure odstranit z paměti a při vyvolání vyžadovat studenou spouštěcí službu. V případě, že se funkce škáluje na novou instanci, jsou také vyžadovány studené starty.

Obrázek 3-10 ukazuje vzorek pro studený start. Všimněte si dalších kroků, které jsou potřeba, když je aplikace studená.

![Studená vs.](./media/cold-start-warm-start.png)
počáteční**Obrázek 3-10**. Studené zahájení vs. začátek

Aby nedocházelo k úplnému startu, můžete přepnout z [plánu spotřeby na vyhrazený plán](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Můžete také nakonfigurovat jednu nebo více předem zavedených [instancí](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) s upgradem plánu Premium. V takových případech, pokud potřebujete přidat jinou instanci, je už na cestách a připraveno k použití. Tyto možnosti mohou přispět ke zmírnění potíží s studeným startem souvisejícím s výpočetním prostředím bez serveru.

Poskytovatelé cloudových služeb se účtují za servery bez serveru založeného na době provádění výpočetního prostředí a spotřebované paměti. Dlouho běžící operace nebo úlohy s vysokou spotřebou paměti nejsou vždy nejlepšími kandidáty pro bez serveru. Funkce bez serveru přidává malým blokům práce, které je možné rychle dokončit. Většina platforem bez serveru vyžaduje, aby se jednotlivé funkce dokončily během několika minut. Azure Functions výchozí doba trvání 5 minut, která se dá nakonfigurovat až na 10 minut. Plán Azure Functions Premium může zmírnit tento problém taky, což je výchozí časové limity na 30 minut s neomezeným vyšším limitem, který se dá nakonfigurovat. Výpočetní čas není kalendářní čas. Pokročilejší funkce využívající [Azure Durable Functions Framework](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) můžou pozastavit provádění v průběhu několika dnů. Fakturace vychází z skutečné doby spuštění – když se funkce probudí a pokračuje ve zpracování.

A konečně využití Azure Functions pro úlohy aplikace přináší složitost. Je vhodné nejdřív navrhnout svou aplikaci s modulárním, volně vázaným návrhem. Pak zjistíte, jestli neexistují výhody serveru, které budou mít větší složitost.

>[!div class="step-by-step"]
>[Předchozí](leverage-containers-orchestrators.md)
>[Další](combine-containers-serverless-approaches.md)
