---
title: 'Aplikace bez serveru: architektury, vzory a implementace Azure'
description: Průvodce architekturou bez serveru. Když, zjistěte, proč a jak implementovat architektury bez serveru (na rozdíl od infrastruktury jako služby [IaaS] nebo platforma jako služba [PaaS]) pro podnikové aplikace.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 6/26/2018
ms.openlocfilehash: 89e5f387e218703a2f6311ef848b3d613a9279f7
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404898"
---
![](./media/Cover.jpg)

# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Aplikace bez serveru: architektury, vzory a implementace Azure

> Ke stažení je k dispozici na: <https://aka.ms/serverless-ebook>

PUBLIKOVAL(A)

Microsoft Developer Division, .NET a Visual Studio produktových týmů

Divize Microsoft Corporation.

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.

Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory. Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené. Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.

Microsoft a ochranné známky uvedený na <https://www.microsoft.com> na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autor:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, vyšší Cloud Developer Advocate, VRCHOLU, Microsoft Corp.

Přispěvatel:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, Cloud Developer Advocate II, VRCHOLU, Microsoft Corp.

Editory:

> **[Bill Wagnera](https://twitter.com/billwagner)**, Senior obsahu pro vývojáře, VRCHOLU, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, Senior obsahu pro vývojáře, VRCHOLU, Microsoft Corp.

Účastníci a recenzenti:

> **[Steve Smith](https://twitter.com/ardalis)**, vlastník, Ardalis služby.

## <a name="introduction"></a>Úvod

Bez serveru je vývoj cloudových platformách ve směru cloud čistě nativní kód. Bez serveru přináší vývojáři blíže na obchodní logiku při izolační starostí o infrastrukturu. Je vzor, který není neznamená "žádný server" ale spíše "méně server". Kód bez serveru je řízená událostmi. Kód může být aktivované vše od tradiční webový požadavek HTTP na časovač, nebo výsledek po nahrání souboru. Umožňuje rychlé škálování s cílem splnit požadavky elastických infrastrukturu za bez serveru a nabízí fakturaci micro skutečně "za to, co používáte." Bez serveru vyžaduje nový způsob myšlení a přístup k vytváření aplikací a má to pravé řešení pro každý problém není. Jako vývojář musíte se rozhodnout:

* Jaké jsou výhody a nevýhody bez serveru?
* Proč bych můžete uvažovat o bez serveru pro vaše vlastní aplikace?
* Jak lze sestavení, testování, nasazení a udržování kódu bez serveru?
* Kde ho smysl migrace kódu do stávající aplikace bez serveru, a co je nejlepší způsob, jak provést tuto transformaci?

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka se zaměřuje na nativní vývoj cloudových aplikací, které používají bez serveru. Knihy zdůrazňuje výhody a zpřístupňuje potenciální nedostatky vývoj aplikací bez serveru a obsahuje průzkum architektur bez serveru. Mnoho příkladů jak prostředí bez serveru je možné jsou znázorněny spolu s různými způsoby návrhu bez serveru.

Tato příručka vysvětluje součásti platformy Azure bez serveru a se zaměřuje konkrétně na provádění bez serveru pomocí [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). Dozvíte se o triggerů a vazeb a jak implementovat aplikace bez serveru, které závisí na stavu pomocí odolná služba functions. A konečně, obchodní příklady a případové studie pomůže poskytnout kontext a referenční rámec k určení, zda bez serveru je ten správný přístup pro vaše projekty.

## <a name="evolution-of-cloud-platforms"></a>Vývoj cloudové platformy

Bez serveru vyvrcholí několika iterací cloudovými platformami. Vývoj začalo se fyzických počítačů v datovém centru a provedení určité prostřednictvím infrastruktury jako služby (IaaS) a platforma jako služba (PaaS).

![Vývoj v místním k bez serveru](./media/serverless-evolution-iaas-paas.png)

Před cloudu existuje a jasně hranice mezi vývojem a provozem. Nasazení aplikace určená, odpovídání na řadu dotazy jako:

* Jaký hardware by měly být nainstalovány?
* Jak je fyzický přístup k počítači zabezpečené?
* Vyžaduje datové centrum nepřerušitelný zdroj napájení (UPS)?
* Odešle se úložiště záloh
* Mělo by být redundantní napájení?

V seznamu přejde a obrovská režijní náklady. V mnoha situacích byly oddělení IT vynutit řešit neuvěřitelné plýtvání. Plýtvání kvůli byla z důvodu nadměrného přidělení serverů jako zálohování počítačů pro obnovení a úsporný režim servery po havárii umožňuje horizontální navýšení kapacity. Zavedením naštěstí, technologie virtualizace (třeba [Hyper-V](/virtualization/hyper-v-on-windows/about/)) se virtuální počítače (VM) vyvolalo infrastruktury jako služby (IaaS). Virtualizované infrastruktuře povolené operace nastavení standardní sadu serverů jako páteřní síť, což vede k flexibilním prostředí umožňující zřizování jedinečných serverů "na vyžádání." Důležitější, virtualizace připravit použití cloudu k poskytnutí virtuálních počítačů "jako služba." Společnosti by mohl snadno získat nevyvíjí obchodní činnost nástroje byste se museli starat o redundantní napájení nebo fyzické počítače. Místo toho, zaměřuje na virtuální prostředí.

IaaS stále vyžaduje náročné režijní náklady, protože operace je provádět různé úlohy. Mezi tyto úlohy patří:

* Opravy a zálohování serverů.
* Instalace balíčků.
* Průběžná operačního systému.
* Monitorování aplikace.

Představuje novou generaci snížit režijní náklady tím, že poskytuje platformu jako službu (PaaS). Poskytovatel cloudu modelu paas, zpracovává operační systémy, oprav zabezpečení a dokonce i požadované balíčky pro podporu konkrétní platformy. Místo vytváření virtuálního počítače a konfigurace rozhraní .NET Framework a sestavení Internetové informační služby (IIS) serverů, vývojářům jednoduše zvolte "cílová platforma" jako je například "Webová aplikace" nebo "Koncový bod rozhraní API" a nasazení kódu přímo. Dotazy infrastruktury jsou zmenšeny na:

* Jaké velikosti služby jsou potřeba?
* Jak služby horizontální navýšení kapacity (přidat další servery nebo uzly)?
* Jak služby vertikálně navýšit kapacitu (zvýšení kapacity pro hostitelské servery nebo uzly)?

Bez serveru další abstrahuje servery se zaměříte na kód založený na událostech. Místo platformu vývojáři můžou soustředit na mikroslužby, která provádí jednu věc. Dvě základní otázky pro vytváření kódu bez serveru jsou:

* Co spustí kód?
* K čemu kód slouží?

Pomocí prostředí bez serveru infrastruktury je abstrahovaný. V některých případech může vývojář už worries o hostiteli vůbec. Zda je spuštěna instance IIS, Kestrel, Apache nebo jiný webový server ke správě webových požadavků, vývojář se zaměřuje na aktivační událost HTTP. Aktivační událost poskytuje standardní, napříč platformami datová část požadavku. Datová část nejen usnadňuje proces vývoje, ale usnadňuje testování a v některých případech umožňuje kód snadno přenosné napříč platformami.

Další funkcí prostředí bez serveru je micro fakturace. Je běžné pro webové aplikace do koncových bodů hostitele webového rozhraní API. V tradiční holé počítače IaaS a dokonce i implementace PaaS, prostředky pro hostování rozhraní API se průběžně placené pro. To znamená, že platíte k hostování koncových bodů i v případě, že se nepoužívají. Často zjistíte ten, který volá rozhraní API více, než ostatní, takže celého systému se škálovat podle podpora oblíbených koncových bodů. Bez serveru umožňuje nezávislé škálování každého koncového bodu a platby za využití, tak žádné náklady se účtují, když nejsou volána rozhraní API. Migrace může v mnoha případech výrazně snížit náklady na průběžnou pro podporu koncových bodů.

## <a name="what-this-guide-doesnt-cover"></a>Co tato příručka nepopisuje

Tato příručka konkrétně zvýrazní přístupy k architektuře a vzory návrhu a není podrobné informace o Azure Functions, podrobnosti implementace [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps), nebo jiné platformy bez serveru. Tato příručka nepopisuje, například pokročilých pracovních postupů s Logic Apps nebo funkce Azure Functions, jako je konfigurace sdílení prostředků mezi zdroji (CORS), použití vlastních domén nebo nahrávání certifikátů SSL. Tyto podrobnosti jsou dostupné prostřednictvím online [dokumentaci ke službě Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Další zdroje

* [Azure Architecture center](https://docs.microsoft.com/azure/architecture/)
* [Osvědčené postupy pro cloudové aplikace](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kdo by měl používat v Průvodci

Tento průvodce je určen pro vývojáře a architekty řešení, kteří chtějí vytvářet podnikové aplikace pomocí .NET, který může použít komponenty bez serveru v místním prostředí nebo v cloudu. Je užitečné pro vývojáře, architekty a technický pracovník s rozhodovací pravomocí zájem o informace:

* Principy výhody a nevýhody vývoj bez serveru
* Tom, jak přistupovat ke architektury bez serveru
* Ukázky implementace aplikace bez serveru

## <a name="how-to-use-the-guide"></a>Jak používat Průvodce

První část tohoto průvodce zkontroluje důvod, proč bez serveru je vhodným řešením porovnáním několik přístupů jinou architekturu. Zkontroluje technologie a vývoj životní cyklus, protože všechny aspekty vývoje softwaru jsou ovlivněny rozhodnutí o architektuře. Průvodce zkontroluje případy použití a vzory návrhu a zahrnuje referenční implementace pomocí služby Azure Functions. Každý oddíl obsahuje další prostředky pro další informace o konkrétní oblasti. V Průvodci končí prostředky pro návody a praktické prozkoumávání provádění bez serveru.

## <a name="send-your-feedback"></a>Pošlete svůj názor

Příručka a ukázky související se neustále vyvíjí, takže uvítali váš názor! Pokud máte připomínky jak se tento průvodce může zlepšit, použijte část zpětná vazba v dolní části libovolné stránky založená na [problémy Githubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
[Next](architecture-approaches.md)