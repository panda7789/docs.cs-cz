---
title: 'Bezserverové aplikace: Architektura, vzory a implementace v Azure'
description: Průvodce architekturou bez serveru. Zjistěte, kdy, proč a jak implementovat architekturu bez serveru (na rozdíl od infrastruktury jako služby [IaaS] nebo platformy jako služby [PaaS]) pro podnikové aplikace.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 148a79e39c047897719e4f97efd84676b1b92636
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "68676754"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Bezserverové aplikace: Architektura, vzory a implementace v Azure

![Snímek obrazovky zobrazující titulní knihu aplikací bez serveru](./media/index/serverless-apps-cover.jpg)

> STAŽENÍ k dispozici v:<https://aka.ms/serverless-ebook>

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2018 by Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autorizova

> **[Jeremy Likness](https://twitter.com/jeremylikness)** , Poradce pro cloudový vývoj, Poradce pro cloudový vývoj, Apex, Microsoft Corp.

Skupinou

> **[Cecil Phillip](https://twitter.com/cecilphillip)** , Poradce pro cloudový vývoj II, Apex, Microsoft Corp.

Editory

> **[Bill Wagner](https://twitter.com/billwagner)** , náměstek – vývojář obsahu, Apex, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)** , vrchní vývojář obsahu, Apex, Microsoft Corp.

Účastníci a kontroloři:

> **[Steve Smith](https://twitter.com/ardalis)** , Owner, Ardalis Services.

## <a name="introduction"></a>Úvod

Bez [serveru](https://azure.microsoft.com/solutions/serverless/) je vývoj cloudových platforem ve směru čistého nativního cloudového kódu. Bez serveru přináší vývojářům lepší obchodní logiku a zároveň je zajímají z problematiky infrastruktury. Je to vzor, který neznamená "žádný server", ale spíše "méně serveru". Kód bez serveru je řízený událostmi. Kód může být aktivován cokoliv z tradičního webového požadavku HTTP do časovače nebo z důvodu odeslání souboru. Infrastruktura založená na bez serveru umožňuje okamžité škálování, aby splňovalo elastické požadavky, a nabízí mikrofakturaci skutečně "platíte za to, co využijete". Bez serveru se vyžaduje nový způsob, jak si vytvářet aplikace a nejedná se o správné řešení pro všechny problémy. Jako vývojář se musíte rozhodnout:

* Jaké jsou odborníci a nevýhody bez serveru?
* Proč byste měli zvážit bez serveru pro vlastní aplikace?
* Jak můžete sestavovat, testovat, nasazovat a udržovat kód bez serveru?
* Tam, kde má smysl migrovat kód na bez serveru v existujících aplikacích a jaký je nejlepší způsob, jak tuto transformaci provést?

## <a name="about-this-guide"></a>O této příručce

Tato příručka se zaměřuje na nativní vývoj aplikací v cloudu, které používají bez serveru. Kniha zvýrazní výhody a zpřístupňuje potenciální nevýhody vývoje aplikací bez serveru a poskytuje průzkum architektur bez serveru. Mnoho příkladů použití bez serveru je znázorněno spolu s různými vzory návrhu bez serveru.

Tato příručka vysvětluje komponenty platformy bez serveru Azure a zaměřuje se konkrétně na implementaci bez serveru s využitím [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). Dozvíte se o triggerech a vazbách a o tom, jak implementovat aplikace bez serveru, které spoléhají na stav pomocí trvalých funkcí. A konečně, obchodní příklady a případové studie pomůžou poskytnout kontext a rámec odkazů, abyste zjistili, jestli je bez serveru správným přístupem k vašim projektům.

## <a name="evolution-of-cloud-platforms"></a>Vývoj cloudových platforem

Bez serveru je ukončeno několik iterací cloudových platforem. Vývoj začala s fyzickým kovm v datovém centru a procházel prostřednictvím infrastruktury jako služby (IaaS) a platformy jako služby (PaaS).

![Vývoj z místního prostředí do bez serveru](./media/serverless-evolution-iaas-paas.png)

Před cloudem existovala hranice discernible mezi vývojem a operacemi. Nasazení aplikace znamenalo zodpovězení nesčetných otázek, jako je:

* Jaký hardware se má nainstalovat?
* Jak je fyzický přístup k počítači zabezpečený?
* Vyžaduje datové centrum nepřerušitelný zdroj napájení (UPS)?
* Kam se odesílají zálohy úložiště?
* Měli byste mít redundantní napájení?

V seznamu se dopadne a režie byla nemimořádná. V mnoha situacích byly IT oddělení nuceně zabývat se nevelkým odpadem. Odpad z důvodu zajištění horizontálního navýšení kapacity serverů jako záložních počítačů pro zotavení po havárii a pro pohotovostní servery. Naštěstí zavedení virtualizační technologie (například [technologie Hyper-V](/virtualization/hyper-v-on-windows/about/)) s Virtual Machines (virtuální počítače) vedlo k infrastruktuře jako služby (IaaS). Virtualizované infrastruktura má povolené operace pro nastavení standardní sady serverů jako páteřní sítě, což vede k flexibilnímu prostředí, které umožňuje zřídit na vyžádání jedinečné servery. Důležitější – virtualizace nastavila fázi pro použití cloudu k poskytování virtuálních počítačů jako služby. Společnosti se můžou snadno dostat do činnosti, která se obává redundantního napájení nebo fyzických počítačů. Místo toho se zaměřují na virtuální prostředí.

IaaS stále vyžaduje velkou režii, protože operace stále zodpovídají za různé úkoly. Mezi tyto úlohy patří:

* Probíhá oprava a zálohování serverů.
* Instalují se balíčky.
* Udržování operačního systému v aktuálním stavu.
* Monitorování aplikace

Další vývoj snížil režii poskytováním platforem jako služby (PaaS). V PaaS poskytovatel cloudu zpracovává operační systémy, opravy zabezpečení a dokonce i požadované balíčky pro podporu konkrétní platformy. Namísto sestavování virtuálního počítače a následnou konfigurací .NET Framework a nasazení serverů Internetová informační služba (IIS) můžou vývojáři jednoduše zvolit "cíl platformy", jako je například webová aplikace nebo koncový bod rozhraní API, a přímo nasadit kód. Otázky infrastruktury se snižují na:

* Jaké služby velikosti jsou potřeba?
* Jak se služby škálují (přidat další servery nebo uzly)?
* Jak se služby škálují (zvyšují kapacitu hostitelských serverů nebo uzlů)?

Servery s dalšími abstrakcemi bez serveru se zaměřením na kód řízený událostmi. Místo platformy se můžou vývojáři soustředit na mikroslužbu, která dělá jednu věc. Mezi dvě klíčové otázky pro sestavování kódu bez serveru patří:

* Co kód aktivuje?
* Co kód dělá?

Infrastruktura je bez serveru abstraktní. V některých případech už vývojář nebere na starosti žádné informace o hostiteli. Bez ohledu na to, jestli je pro správu webových požadavků spuštěná instance IIS, Kestrel, Apache nebo nějaký jiný webový server, se vývojář zaměřuje na Trigger HTTP. Aktivační událost poskytuje pro požadavek standardní datovou část pro různé platformy. Datová část nejen zjednodušuje proces vývoje, ale usnadňuje testování a v některých případech usnadňuje přenos kódu napříč platformami.

Další funkcí bez serveru je mikro fakturace. Pro webové aplikace je běžné hostování koncových bodů webového rozhraní API. V tradičních IaaS a dokonce PaaSch implementacích jsou prostředky pro hostování rozhraní API průběžně placené. To znamená, že platíte za hostování koncových bodů i v případě, že nejsou k dispozici. Často uvidíte, že jedno rozhraní API se nazývá více než jiné, takže celý systém se škáluje na základě podpory oblíbených koncových bodů. Bez serveru můžete každý koncový bod škálovat nezávisle a platíte za využití, takže se neúčtují žádné náklady, pokud se rozhraní API nevolají. Migrace může v mnoha případech významně snížit průběžné náklady na podporu koncových bodů.

## <a name="what-this-guide-doesnt-cover"></a>Co tato příručka nepopisuje

Tato příručka konkrétně zvýrazňuje přístupy k architektuře a vzory návrhu a není hlubokým podrobněem v podrobnostech implementace Azure Functions, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)nebo jiných platforem bez serveru. Tato příručka se zabývá například pokročilými pracovními postupy pomocí Logic Apps nebo funkcí Azure Functions, jako je například konfigurace sdílení prostředků mezi zdroji (CORS), použití vlastních domén nebo nahrávání certifikátů SSL. Tyto podrobnosti jsou k dispozici v online [Azure Functions dokumentaci](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Další zdroje

* [Centrum architektury Azure](https://docs.microsoft.com/azure/architecture/)
* [Osvědčené postupy pro cloudové aplikace](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kdo má používat Průvodce

Tato příručka je určená pro vývojáře a architekty řešení, kteří chtějí sestavovat podnikové aplikace s .NET, které můžou používat komponenty bez serveru místně i v cloudu. Je užitečné pro vývojáře, architekty a pracovníky technického rozhodování, které zajímá:

* Porozumění profesionálům a nevýhody vývoje bez serveru
* Seznámení s postupy při přístupu k architektuře bez serveru
* Příklady implementací aplikací bez serveru

## <a name="how-to-use-the-guide"></a>Jak používat Průvodce

První část této příručky se zabývá tím, proč je bez serveru možnost životaschopná, a to porovnáním několika různých přístupů k architektuře. Prověřuje jak životní cyklus vývoje a vývoje, protože všechny aspekty vývoje softwaru mají vliv na rozhodování o architektuře. Průvodce pak prověřuje případy použití a vzory návrhu a obsahuje referenční implementace pomocí Azure Functions. Každá část obsahuje další zdroje informací o konkrétní oblasti. Tato příručka se dokončí s prostředky pro návody a praktický průzkum implementace bez serveru.

## <a name="send-your-feedback"></a>Poslat svůj názor

Průvodce a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá! Pokud máte komentáře týkající se vylepšení této příručky, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Next](architecture-approaches.md)
