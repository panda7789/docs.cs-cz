---
title: Volba mezi tradiční webové aplikace a jednostránkové aplikace
description: Architekti moderních webových aplikací pomocí ASP.NET Core a Microsoft Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: bbb217b2f11901658fa70a5e5cff6521d157952c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104763"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Volba mezi tradiční webové aplikace a jednostránkové aplikace (SPA)

> "Je Atwood zákonem: jakékoli aplikace, která může být napsán v jazyce JavaScript, zapíšou nakonec v jazyce JavaScript."  
> _\- Jeff Atwood_

## <a name="summary"></a>Souhrn

Existují dvě obecné metody vytvářet webové aplikace ještě dnes: tradiční webových aplikací, které provádějí většinu logiku aplikace na serveru a jednostránkové aplikace (SPA), které provádějí většinu logiku uživatelského rozhraní ve webovém prohlížeči, komunikuje s webovým serverem, především pomocí webového rozhraní API. Hybridní přístup je také možné, nejjednodušší se hostitele jednu nebo více bohaté SPA jako dílčí aplikací v rámci větší tradiční webové aplikace.

Měli byste použít tradiční webové aplikace při:

-   Požadavky na straně klienta aplikace jsou jednoduchý nebo i jen pro čtení.

-   Aplikace musí fungovat v prohlížečích bez podpory jazyka JavaScript.

-   Váš tým je obeznámeni s JavaScript nebo TypeScript technik vývoje.

Měli byste použít SPA při:

-   Aplikace musí vystavit bohaté uživatelské rozhraní s mnoha funkcemi.

-   Váš tým je obeznámeni s vývojem pro JavaScript a TypeScript.

-   Aplikace musí již zveřejňují rozhraní API pro ostatní klienty (interní nebo veřejná).

Navíc vyžadují větší SPA architektury architektury a odborných znalosti zabezpečení. Dojde k větší změn z důvodu časté aktualizace a nové rozhraní než tradiční webových aplikací. Konfigurace automatizované procesy sestavení a nasazení a použití možnosti nasazení jako kontejnery jsou s aplikacemi SPA obtížnější než tradiční webové aplikace.

Vylepšení v možné díky modelu SPA činnost koncového uživatele je nutné porovnat těchto aspektů.

## <a name="when-to-choose-traditional-web-apps"></a>Kdy použít tradiční webové aplikace

Následuje podrobnější vysvětlení dříve uvádí důvody pro výběr tradiční webových aplikací.

**Aplikace má požadavky na jednoduchý, může být jen pro čtení, straně klienta**

Mnoho webových aplikací jsou primárně spotřebovávána způsobem jen pro čtení valná většina uživatelů. Jen pro čtení (nebo pro čtení – většinou) aplikace jsou obvykle mnohem jednodušší než ty, které udržují a manipulaci s značnou část stavu. Vyhledávací může například obsahovat jeden vstupní bod se textové pole a druhá stránka pro zobrazení výsledků vyhledávání. Anonymní uživatelé snadno provádět požadavky a je nutné pro logiku na straně klienta. Podobně blogu nebo obsah systém správy je veřejná aplikace obvykle obsahuje především obsah s malým množstvím chování klienta. Jsou takové aplikace snadno vytvořené jako tradiční na serveru webové aplikace, které provádět logiku na webovém serveru a vykreslení HTML, který se má zobrazit v prohlížeči. Vymazat výhodu v těchto scénářích má také skutečnost, že každý jedinečný stránce webu má svou vlastní adresu URL, která může být aktuálně přihlášeni a indexovaný vyhledávači (ve výchozím nastavení, aniž by bylo nutné přidat jako samostatný prvek aplikace).

**Aplikace musí fungovat v prohlížečích bez podpory jazyka JavaScript**

Webové aplikace, které je potřeba fungovat v prohlížečích s omezeným nebo bez podpory jazyka JavaScript by měly být zapsány pomocí pracovních postupů tradiční webové aplikace (nebo alespoň moct vrátit zpět k takové chování). SPA vyžadují JavaScript na straně klienta, chcete-li funkce; Pokud není k dispozici, nejsou SPA dobrou volbou.

**Je-li obeznámeni s JavaScript nebo TypeScript technik vývoje váš tým**

Pokud váš tým obeznámeni s JavaScript nebo TypeScript, ale je obeznámeni s vývoj webové serverové aplikace, pravděpodobně budou moct rychleji než SPA poskytovat tradiční webové aplikace. Není-li learning k programu SPA cílem, nebo se vyžaduje uživatelské prostředí poskytované SPA, tradiční webové aplikace jsou vyšší produktivitu výběru týmům, kteří jsou již obeznámeni s jejich vytváření.

## <a name="when-to-choose-spas"></a>Když chcete-li zvolit SPA

Následuje podrobnější vysvětlení kdy zvolit styl jednostránkové aplikace vývoje pro vaši webovou aplikaci.

**Aplikace musí vystavit bohaté uživatelské rozhraní s mnoha funkcemi**

SPA může podporovat bohaté funkce klienta, které nevyžaduje opětovné načtení stránky, když uživatelé provést akce nebo přejděte mezi oblastmi aplikace. SPA můžete načítat rychleji, načítání dat na pozadí, a akce jednotlivých uživatelů jsou rychlejšího vzhledem k tomu, že vyskytují jen vzácně zavážky celou stránku. SPA může podporovat přírůstkové aktualizace, aniž by uživatel musel klikněte na tlačítko pro odeslání formuláře ukládání částečně vyplněné formuláře nebo dokumenty. Bohaté chování klienta, jako je například přetahování myší, může podporovat SPA mnohem snadněji než tradiční aplikace. SPA můžete určený ke spouštění v odpojeném režimu, provedení aktualizace na straně klienta model, který se nakonec synchronizují zpět na server, jakmile se znovu navázané připojení. Pokud vaše aplikace požadavky zahrnují bohaté funkce, která přesahuje co nabízí typické formuláře HTML, měli byste vybrat k SPA styl aplikaci.

Všimněte si, že často SPA nutné implementovat funkce, které jsou integrované v tradiční webové aplikace, například zobrazení smysluplný adresy URL na adresu panelu odrážející aktuální operace (a umožní uživatelům záložku nebo přímý odkaz na tuto adresu URL pro návrat do něj). SPA také měli povolit uživatelům používat tlačítka vpřed a zpět v prohlížeči s výsledky, které nebudou neohlášeného je.

**Je váš tým obeznámeni s vývojem pro JavaScript a TypeScript**

Zápis SPA vyžaduje znalost jazyka JavaScript a TypeScript a způsobů programování na straně klienta a knihovny. Váš tým musí být příslušný zápis moderní JavaScriptu pomocí rozhraní SPA jako úhlová.

> ### <a name="references--spa-frameworks"></a>Odkazy – SPA architektury
> - **Úhlová**  
> <https://angular.io>
> - **Porovnání rámci jazyka JavaScript**  
> <https://javascriptreport.com/the-ultimate-guide-to-javascript-frameworks/>

**Aplikace musí již zveřejňují rozhraní API pro ostatní klienty (interní nebo veřejná)**

Pokud jste již podporujete webové rozhraní API pro ostatní klienty, může vyžadovat méně úsilí pro vytvoření SPA implementace, která využívá tato rozhraní API místo reprodukci logiku ve formuláři na straně serveru. SPA zkontrolujte rozsáhlé používání webových rozhraní API pro dotazování a aktualizace dat, jak uživatelé pracují s aplikací.

## <a name="decision-table--traditional-web-or-spa"></a>Rozhodovací tabulky – tradiční Web nebo SPA

Následující rozhodnutí tabulka shrnuje některé základní faktorů, které je třeba zvážit při výběru mezi tradiční webové aplikace a SPA.

  | **Koeficient** | **Tradiční webové aplikace** | **Jednostránková aplikace** |
  |---|---|---|
  | Požadované Team znalost jazyka JavaScript nebo TypeScript | **Minimální** | **Požadované** |
  | Podpora prohlížeče bez skriptování | **Podporované** | **Nepodporuje se** |
  | Chování minimální aplikace na straně klienta | **Well-Suited** | **Přehnaně** |
  | Požadavky na bohatou a komplexní uživatelské rozhraní | **Omezené** | **Well-Suited** |

>[!div class="step-by-step"]
[Předchozí](modern-web-applications-characteristics.md)
[další](architectural-principles.md)
