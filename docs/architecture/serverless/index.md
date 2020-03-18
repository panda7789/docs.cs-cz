---
title: 'Aplikace bez serveru: architektura, vzory a implementace v Azure'
description: Průvodce architekturou bez serveru. Zjistěte, kdy, proč a jak implementovat architekturu bez serveru (na rozdíl od infrastruktury jako služby [IaaS] nebo platformy jako služby [PaaS]) pro vaše podnikové aplikace.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 9dea7dbccb5c9e125f792e6a7287a7dd2fad26f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73093538"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>Aplikace bez serveru: architektura, vzory a implementace v Azure

![Snímek obrazovky, který zobrazuje obal e-knihy Aplikace bez serveru.](./media/index/serverless-apps-cover.jpg)

> KE STAŽENÍ K DISPOZICI NA ADRESE:<https://aka.ms/serverless-ebook>

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2018 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné <https://www.microsoft.com> známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autor:

> **[Jeremy Likness](https://twitter.com/jeremylikness)**, senior cloud advokát, Microsoft Corp.

Přispěvatelů:

> **[Cecil Phillip](https://twitter.com/cecilphillip)**, senior cloud advokát, Microsoft Corp.

Editory:

> **[Bill Wagner](https://twitter.com/billwagner)**, hlavní vývojář obsahu, Microsoft Corp.

> **[Maira Wenzel](https://twitter.com/mairacw)**, hlavní vývojář obsahu, Microsoft Corp.

Účastníci a recenzenti:

> **[Steve Smith](https://twitter.com/ardalis)**, majitel, Ardalis Services.

## <a name="introduction"></a>Úvod

[Bez serveru](https://azure.microsoft.com/solutions/serverless/) je vývoj cloudových platforem ve směru čistého cloudového nativního kódu. Bez serveru přibližuje vývojáře obchodní logice a zároveň je izoluje před problémy s infrastrukturou. Je to vzor, který neznamená "žádný server", ale spíše "méně server." Kód bez serveru je řízen událostmi. Kód může být spuštěn čímkoli od tradičního webového požadavku HTTP až po časovač nebo výsledek nahrání souboru. Infrastruktura bez serveru umožňuje okamžité škálování pro splnění elastických požadavků a nabízí mikrofakturaci, která skutečně "zaplatí za to, co používáte". Bez serveru vyžaduje nový způsob myšlení a přístup k vytváření aplikací a není to pravé řešení pro každý problém. Jako vývojář se musíte rozhodnout:

- Jaké jsou výhody a nevýhody bez serveru?
- Proč byste měli zvážit serverless pro své vlastní aplikace?
- Jak můžete vytvářet, testovat, nasazovat a udržovat kód bez serveru?
- Kde má smysl migrovat kód do bezserveru v existujících aplikacích a jaký je nejlepší způsob, jak tuto transformaci provést?

## <a name="about-this-guide"></a>O této příručce

Tato příručka se zaměřuje na cloud nativní vývoj aplikací, které používají bez serveru. Kniha upozorňuje na výhody a odhaluje potenciální nevýhody vývoje aplikací bez serveru a poskytuje přehled architektur bez serveru. Mnoho příkladů, jak lze použít bez serveru, jsou ilustrovány spolu s různými vzory návrhu bez serveru.

Tato příručka vysvětluje součásti platformy Azure bez serveru a zaměřuje se konkrétně na implementaci bezserveru pomocí [Funkce Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview). Dozvíte se o aktivačních událostech a vazbách a také o tom, jak implementovat aplikace bez serveru, které spoléhají na stav pomocí trvalých funkcí. Nakonec obchodní příklady a případové studie vám pomohou poskytnout kontext a referenční rámec k určení, zda je bezserveru správný přístup pro vaše projekty.

## <a name="evolution-of-cloud-platforms"></a>Vývoj cloudových platforem

Bez serveru je vyvrcholením několika iterací cloudových platforem. Vývoj začal fyzickým kovem v datovém centru a postupoval prostřednictvím infrastruktury jako služby (IaaS) a platformy jako služby (PaaS).

![Vývoj z místního prostředí na bezserveru](./media/serverless-evolution-iaas-paas.png)

Před cloud, rozeznatelné hranice existovala mezi vývojem a operacemi. Nasazení aplikace znamenalo odpovědi na nesčetné množství otázek, jako jsou:

- Jaký hardware by měl být nainstalován?
- Jak je fyzický přístup k počítači zabezpečen?
- Vyžaduje datové centrum nepřerušitelný zdroj napájení (UPS)?
- Kde jsou odesílány zálohy úložiště?
- Měla by existovat nadbytečná energie?

Seznam pokračuje a režie byla obrovská. V mnoha situacích byla IT oddělení nucena vypořádat se s neuvěřitelným odpadem. Odpad byl způsoben nadměrnou alokací serverů jako záložních strojů pro zotavení po havárii a pohotovostních serverů, které umožňují horizontální navýšení kapacity. Zavedení virtualizační technologie (například [Hyper-V)](/virtualization/hyper-v-on-windows/about/)s virtuálními počítači (VM) naštěstí vedlo k vytvoření infrastruktury jako služby (IaaS). Virtualizovaná infrastruktura umožnila operacím nastavit standardní sadu serverů jako páteřní, což vedlo k flexibilnímu prostředí schopnému zřizování jedinečných serverů "na vyžádání". Důležitější je, že virtualizace připravila půdu pro použití cloudu k poskytování virtuálních počítačů "jako služby". Společnosti by se mohly snadno dostat z podnikání starostí s nadbytečnou mocí nebo fyzickými stroji. Místo toho se zaměřili na virtuální prostředí.

IaaS stále vyžaduje vysoké režie, protože operace je stále zodpovědný za různé úkoly. Mezi tyto úkoly patří:

- Oprava a zálohování serverů.
- Instalace balíčků.
- Udržování aktuálního operačního systému.
- Sledování aplikace.

Další vývoj snížil režii tím, že platformu jako službu (PaaS). S PaaS, poskytovatel cloudu zpracovává operační systémy, bezpečnostní záplaty a dokonce i požadované balíčky pro podporu konkrétní platformy. Namísto vytváření virtuálního virtuálního zařízení a následné konfigurace rozhraní .NET Framework a vysazení serverů Internetové informační služby (IIS) vývojáři jednoduše zvolí "cíl platformy", například "webovou aplikaci" nebo koncový bod rozhraní API, a nasadí kód přímo. Otázky týkající se infrastruktury jsou omezeny na:

- Jakou velikost služeb jsou potřeba?
- Jak se škálují služby (přidávají další servery nebo uzly)?
- Jak služby vertikálně navýšit (zvýšit kapacitu hostingových serverů nebo uzlů)?

Serverless dále abstrahuje servery se zaměřením na kód řízený událostmi. Namísto platformy se vývojáři můžou soustředit na mikroslužbu, která dělá jednu věc. Dvě klíčové otázky pro vytváření kódu bez serveru jsou:

- Co spustí kód?
- Co kód dělá?

Bez serveru je infrastruktura abstrahována. V některých případech se vývojář již vůbec nestará o hostitele. Bez ohledu na to, zda je spuštěna instance služby IIS, Kestrel, Apache nebo jiného webového serveru pro správu webových požadavků, vývojář se zaměřuje na aktivační událost PROTOKOLU HTTP. Aktivační událost poskytuje standardní datové části pro různé platformy pro požadavek. Datová část nejen zjednodušuje proces vývoje, ale usnadňuje testování a v některých případech umožňuje snadno přenosný kód napříč platformami.

Další funkcí bez serveru je mikrofakturace. Je běžné, že webové aplikace hostují koncové body webového rozhraní API. V tradičních holé metal, IaaS a dokonce i PaaS implementace, prostředky pro hostování rozhraní API jsou hrazeny nepřetržitě. To znamená, že platíte za hostování koncových bodů, i když k nim nemáte přístup. Často zjistíte, že jedno rozhraní API se nazývá více než ostatní, takže celý systém je škálován na základě podpory oblíbených koncových bodů. Bez serveru umožňuje škálovat každý koncový bod nezávisle a platit za využití, takže žádné náklady vznikají, když nejsou volána api. Migrace může v mnoha případech výrazně snížit průběžné náklady na podporu koncových bodů.

## <a name="what-this-guide-doesnt-cover"></a>Co tato příručka nepokrývá

Tato příručka konkrétně zdůrazňuje přístupy architektury a návrhové vzory a není podrobný mat do podrobností implementace Azure Functions, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)nebo jiných platforem bez serveru. Tato příručka se nevztahuje například na pokročilé pracovní postupy s logic apps nebo funkce azure funkce, jako je konfigurace sdílení prostředků mezi zdroji (CORS), použití vlastnídomény nebo nahrávání certifikátů SSL. Tyto podrobnosti jsou k dispozici prostřednictvím [online dokumentace azure funkce](https://docs.microsoft.com/azure/azure-functions/functions-reference).

### <a name="additional-resources"></a>Další zdroje

- [Centrum architektury Azure](https://docs.microsoft.com/azure/architecture/)
- [Osvědčené postupy pro cloudové aplikace](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>Kdo by měl používat průvodce

Tato příručka byla napsána pro vývojáře a architekty řešení, kteří chtějí vytvářet podnikové aplikace s rozhraním .NET, které mohou používat komponenty bez serveru buď místně, nebo v cloudu. Je to užitečné pro vývojáře, architekty a technické osoby s rozhodovací pravomocí, kteří se zajímají o:

- Pochopení klady a zápory bezserveru vývoje
- Naučit se přistupovat k architektuře bez serveru
- Příklad implementace aplikací bez serveru

## <a name="how-to-use-the-guide"></a>Jak používat průvodce

První část této příručky zkoumá, proč bez serveru je životaschopná možnost porovnáním několika různých přístupů architektury. Zkoumá jak životní cyklus technologie, tak životní cyklus vývoje, protože všechny aspekty vývoje softwaru jsou ovlivněny rozhodnutími o architektuře. Průvodce pak zkoumá případy použití a návrhové vzory a zahrnuje referenční implementace pomocí funkce Azure. Každá část obsahuje další zdroje informací o určité oblasti. Průvodce uzavírá s prostředky pro návody a praktické zkoumání implementace bez serveru.

## <a name="send-your-feedback"></a>Pošlete svůj názor

Průvodce a související vzorky se neustále vyvíjejí, takže vaše zpětná vazba je vítána! Pokud máte komentáře o tom, jak lze tuto příručku zlepšit, použijte sekci zpětné vazby v dolní části libovolné stránky postavené na [problémech githubu](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Další](architecture-approaches.md)
