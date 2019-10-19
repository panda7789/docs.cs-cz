---
title: Využití bezserverových funkcí
description: Využití bez serveru a Azure Functions v cloudových nativních aplikacích
ms.date: 06/30/2019
ms.openlocfilehash: c79f611b83f63079634fb2bac037c99f851f18ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578924"
---
# <a name="leveraging-serverless-functions"></a>Využití bezserverových funkcí

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V rámci správy úplných počítačů a operačních systémů pro využívání cloudových možností, bez serveru na extrémním konci, kde jediná věc, za kterou zodpovídáte, je váš kód a platíte jenom při spuštění kódu. Azure Functions poskytuje způsob, jak v aplikacích vytvářet možnosti bez serveru. 

## <a name="what-is-serverless"></a>Co je bez serveru?

Computing bez serveru neznamená, že není k dispozici žádný server, na kterém je spuštěná aplikace – kód pořád běží na serveru někam. Rozdíl je v tom, že vývojový tým aplikace již nemusí mít obavy při správě serverové infrastruktury. Computingová řešení bez serveru, jako je Azure Functions týmu, zvyšují produktivitu a umožňují organizacím optimalizovat jejich prostředky a soustředit se na poskytování řešení.

Výpočetní prostředí bez serveru používá pro hostování aplikace nebo součásti vaší aplikace nestavové kontejnery s aktivační událostí. Platformy bez serveru se můžou škálovat a v závislosti na požadavcích podle potřeby. Platformy, jako je Azure Functions, mají snadný přímý přístup k jiným službám Azure, jako jsou fronty, události a úložiště.

## <a name="what-challenges-are-solved-by-serverless"></a>Jaké problémy řeší bez serveru?

Bez serveru je maximální abstrakcí z provozu vlastního hardwaru. Vývojáři se můžou zaměřit výhradně na psaní kódu pro řešení obchodních problémů, aniž by se museli starat o některé z následujících úloh, které by mohly být nutné při hostování vlastních serverů:

- Nákup počítačů a licencí softwaru
- Ubytování, zabezpečení, konfigurace a údržba počítačů a jejich požadavků na síť, výkon a/C
- Opravy a upgrade operačních systémů a softwaru
- Konfigurace webových serverů nebo služeb počítače pro hostování aplikačního softwaru
- Konfigurace aplikačního softwaru v rámci své platformy

Mnohé společnosti využívají spoustu pedagogů a přiřazují velké rozpočty na podporu těchto potíží s hardwarovou infrastrukturou. Pouhým přechodem na Cloud eliminují některé z těchto otázek; posunutí aplikací po celém serveru tak, aby se neodstranila zbývající aplikace.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Jaké scénáře jsou vhodné pro bez serveru?

Bez serveru se používají jednotlivé krátkodobé běžící funkce, které jsou volány v reakci na určitou aktivační událost. Díky tomu jsou ideální pro zpracování úloh na pozadí.

Aplikace může například potřebovat poslat e-mail jako součást zpracování žádosti. Místo odeslání e-mailu v rámci zpracování webové žádosti by se podrobnosti o e-mailu daly umístit do fronty a tato zpráva se dá použít k výběru zprávy a odeslání e-mailu. Celá řada různých částí aplikace nebo dokonce mnoho aplikací může využít stejnou funkci Azure, která poskytuje lepší výkon a škálovatelnost pro aplikace a používá [Vyrovnávání zatížení založené na frontě](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) , aby nedocházelo k kritickým bodům souvisejícím s posílání e-mailů.

I když je [vzor vydavatele/předplatitele](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) mezi aplikacemi a Azure Functions nejběžnějším vzorem, je možné použít i jiné vzory. Azure Functions můžou aktivovat jiné události, jako jsou třeba změny v Azure Blob Storage. Aplikace, která podporuje nahrávání imagí, by mohla mít zodpovědnost za vytváření miniatur nebo změnu velikosti nahraných obrázků na konzistentní rozměry nebo pro optimalizaci velikosti obrázků. Všechny tyto funkce mohou být aktivovány přímo vložením do Azure Blob Storage, zachovává složitost a zatížení samotné aplikace.

Mnoho aplikací má v rámci svých pracovních postupů dlouhotrvající procesy. Tyto úlohy jsou často prováděny v rámci interakce uživatele s aplikací a nutí uživatele počkat a negativně ovlivnit jejich prostředí. Computing bez serveru poskytuje skvělý způsob, jak provádět pomalejší úkoly mimo smyčku interakce uživatele. tyto úlohy se můžou snadno škálovat na vyžádání, aniž by bylo potřeba škálovat celou aplikaci.

## <a name="when-should-you-avoid-serverless"></a>Kdy byste se měli vyhnout bez serveru?

Pro úlohy, které neblokují uživatelské rozhraní, se používá výpočetní výkon bez serveru. To znamená, že nejsou ideální pro hostování webových aplikací nebo webových rozhraní API přímo. Hlavním důvodem je to, že řešení bez serveru se zřídí a na vyžádání se škáluje. Pokud je potřeba nová instance funkce, na kterou se říká *studený start*, trvá zřízení čas. Tato doba obvykle trvá několik sekund, ale může to trvat i v závislosti na různých faktorech. Jedna instance může být často udržována po neomezenou dobu (například tím, že je pravidelně vydává požadavek), ale pokud počet instancí někdy potřebuje horizontální navýšení kapacity, zůstane problém s jeho zahájením.

![Cold vs. začátek ](./media/cold-start-warm-start.png)
**obrázek 3-10**. Studené zahájení vs. začátek

Pokud potřebujete zabránit úplnému startu na začátku, můžete zvolit možnost přepnout z [plánu spotřeby na vyhrazený plán](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Můžete také [nakonfigurovat jednu nebo více předem](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) zavedených instancí s plánem Premium, takže pokud potřebujete přidat jinou instanci, je již a připravená k použití. Tyto možnosti mohou zmírnit jeden z klíčových otázek spojených s výpočetním prostředím bez serveru.

Měli byste se také obvykle vyhnout serveru bez serveru pro dlouhotrvající úlohy. Jsou nejvhodnější pro malé části práce, které je možné rychle dokončit. Většina platforem bez serveru vyžaduje, aby se jednotlivé funkce dokončily během několika minut. Azure Functions se výchozí hodnota intervalu 5 minut (může být nakonfigurovaná na 10 minut). Plán Azure Functions Premium může zmírnit i tento problém, což je výchozí časový limit na 30 minut a umožňuje nakonfigurovat neomezeně vyšší limit.

A konečně využití bez serveru pro určité úkoly v rámci aplikace přináší složitost. Je často vhodné architektovat aplikaci v modulárním, volně připojeném způsobem, a pak zjistit, jestli jsou výhody serveru nevýhodné, aby se zajistila další složitost. Mnohé menší aplikace budou v jednom monolitické nasazení dokonale fungovat, aniž by to vyžadovalo architekturu distribuované aplikace bez serveru.

## <a name="references"></a>Odkazy

- [Principy studeného startu bez serveru](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Předem zahřívání Azure Functions instance](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Vytvoření funkce na platformě Linux pomocí vlastní image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[Předchozí](leverage-containers-orchestrators.md)
>[Další](combine-containers-serverless-approaches.md)
