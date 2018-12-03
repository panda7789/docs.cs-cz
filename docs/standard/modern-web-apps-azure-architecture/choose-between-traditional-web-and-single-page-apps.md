---
title: Volba mezi tradičními webovými aplikacemi a jednostránkové aplikace
description: Zjistěte, jak si vybrat mezi tradičními webovými aplikacemi a jednostránkové aplikace (SPA) při vytváření webových aplikací.
author: ardalis
ms.author: wiwagn
ms.date: 6/28/2018
ms.openlocfilehash: abeee719c15263fea04a3bcf80a6e41c43b640d2
ms.sourcegitcommit: 82a3f7882bc03ed733af91fc2a0b113195bf5dc7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2018
ms.locfileid: "52745300"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Volba mezi tradičními webovými aplikacemi a jednostránkové aplikace (SPA)

> "Zákony vaší Atwoodem: všechny aplikace, které je možné psát v jazyce JavaScript, nakonec se zapíše v jazyce JavaScript."  
> _\- Jeffem Atwoodem_

Existují dva hlavní přístupy k vytváření webových aplikací ještě dnes: tradiční webových aplikací, které provádějí většinu aplikací logiky na serveru a jednostránkové aplikace (SPA), které provádějí většinu logiku uživatelského rozhraní ve webovém prohlížeči komunikuje s webovým serverem, primárně prostřednictvím webového rozhraní API. S hybridním přístupem je také možné, je nejjednodušší hostovat jeden nebo více bohaté SPA jako dílčí aplikace v rámci větší tradiční webové aplikace.

Byste měli použít tradiční webové aplikace při:

- Podle požadavků vaší aplikace na straně klienta jsou jednoduché nebo i jen pro čtení.

- Vaše aplikace potřebuje pro funkce v prohlížečích bez podpory jazyka JavaScript.

- Váš tým není obeznámen s JavaScript nebo TypeScript vývojářských technik.

Měli byste použít SPA při:

- Aplikace musí zveřejnit bohatší uživatelské rozhraní s mnoha funkcemi.

- Váš tým je zkušenosti s vývojem v jazyce JavaScript nebo TypeScript.

- Aplikace už musí vystavit rozhraní API pro ostatní klienty (interní nebo veřejný).

Navíc vyžadují větší architektury jednostránková aplikace architektury a bezpečnostních expertů. Dojde větší změny z důvodu časté aktualizace a nové rozhraní než tradiční webových aplikací. Konfigurace automatizované procesy sestavení a nasazení a při využívání možností nasazení, jako jsou kontejnery jsou s aplikacemi SPA obtížnější než tradičními webovými aplikacemi.

Vylepšení činnost koncového uživatele umožněno SPA modelu musí porovnat tyto aspekty.

## <a name="when-to-choose-traditional-web-apps"></a>Kdy zvolit tradičními webovými aplikacemi

Tady je podrobnější vysvětlení důvodů dříve uvedeno pro výběr tradiční webových aplikací.

**Vaše aplikace má požadavky na jednoduché, může být jen pro čtení a na straně klienta**

Mnoho webových aplikací se primárně spotřebuje způsobem jen pro čtení v převážné většině uživatelů. Aplikace jen pro čtení (nebo pro čtení – většinou) jsou obvykle mnohem jednodušší než ty, které udržují a manipulaci s spoustu stavu. Vyhledávací web může například sestávat z jeden vstupní bod se textové pole a druhá stránka pro zobrazení výsledků hledání. Anonymní uživatelé snadno provádět požadavky, a není nutné logiku na straně klienta. Podobně, blogu nebo obsah správy systému veřejně přístupných aplikace obvykle se skládá převážně obsah s malou chování na straně klienta. Tyto aplikace se snadno vytvářejí jako tradiční serverových webových aplikací, které provádět logiku na webovém serveru a generují kód jazyka HTML, který se má zobrazit v prohlížeči. Skutečnost, že každá jedinečná stránku webu má svou vlastní adresu URL, která může být záložek a indexovaný vyhledávači (ve výchozím nastavení, aniž by bylo nutné přidat jako samostatný prvek aplikace) je také vymazat výhoda v takových scénářích.

**Vaše aplikace potřebuje pro funkce v prohlížečích bez podpory jazyka JavaScript**

Webové aplikace, které je potřeba pracovat v prohlížečích s omezená nebo žádná podpora jazyka JavaScript by měly být zapsány pomocí pracovních postupů tradiční webové aplikace (nebo aspoň moci vrátit k takové chování). SPA vyžadovat, aby se funkce; JavaScript na straně klienta Pokud není k dispozici, nejsou SPA dobrou volbou.

**Váš tým není obeznámen s postupy vývoje jazyka JavaScript nebo TypeScript**

Pokud váš tým není obeznámen s JavaScript nebo TypeScript, ale zná vývoj na straně serveru webové aplikace, pravděpodobně budou moct doručovat rychleji než SPA tradiční webové aplikace. Není-li se program SPA cíl nebo poskytované SPA uživatelské prostředí je povinný, jsou tradičními webovými aplikacemi produktivnější volbu pro týmy, které jsou již znáte sestaveny.

## <a name="when-to-choose-spas"></a>Kdy zvolit SPA

Tady je podrobnější vysvětlení kdy zvolit jednostránkové aplikace stylu vývoje pro vaši webovou aplikaci.

**Aplikace musí zveřejnit bohatší uživatelské rozhraní s mnoha funkcemi**

SPA může podporovat bohaté funkce na straně klienta, který nevyžaduje, aby znovu načíst tuto stránku jako uživatelům provádět akce nebo přecházet mezi oblastmi této aplikace. SPA může načíst rychleji, načítají se data na pozadí, a akce jednotlivých uživatelů jsou rychlejší reakce, protože se vyskytují jen vzácně zpracovávané celou stránku. SPA podporuje přírůstkové aktualizace, aniž by uživatel musel klikněte na tlačítko pro odeslání formuláře ukládá částečně dokončené formuláře nebo dokumenty. Bohaté chování na straně klienta, jako je například přetažení myší, může podporovat SPA mnohem snadněji než tradiční aplikace. SPA můžete určený ke spouštění v odpojeném režimu, provádění aktualizací na straně klienta modelu, který se nakonec synchronizují zpět na server, jakmile se připojení znovu navázáno. Pokud vaše aplikace požadavky zahrnují bohatým funkcím sady, který jde nad rámec co nabízí typické formuláře HTML, měli byste zvolit aplikace SPA style.

Všimněte si, že často SPA nutné k implementaci funkcí, které jsou integrované do tradičními webovými aplikacemi, jako je například zobrazení smysluplnou adresu URL na adresu panelu odráží aktuální operaci (a umožní uživatelům záložku nebo přímý odkaz na tuto adresu URL pro návrat k jeho). SPA také měli uživatelům povolit používání tlačítka vpřed a zpět v prohlížeči s výsledky, které jim nebude překvapí.

**Váš tým je zkušenosti s vývojem v jazyce JavaScript nebo TypeScript**

Zápis SPA vyžaduje znalost jazyka JavaScript nebo TypeScript a techniky programování na straně klienta a knihovny. Váš tým by měl být příslušné při psaní moderní JavaScript s využitím SPA architekturu jako třeba Angular.

> ### <a name="references--spa-frameworks"></a>Odkazy – rozhraní SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Porovnání architektury JavaScriptu**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Aplikace musí již vystavit rozhraní API pro ostatní klienty (interní nebo veřejný)**

Pokud jste již podpory webového rozhraní API pro ostatní klienty, může vyžadovat menším úsilím pro vytvoření implementace jednostránková aplikace, které využívají tato rozhraní API spíše než reprodukce logiky ve formuláři na straně serveru. SPA využívat rozsáhlé webové rozhraní API k dotazování a aktualizace dat jak uživatelé pracují s aplikací.

## <a name="decision-table--traditional-web-or-spa"></a>Tabulka rozhodnutí – tradiční webu nebo aplikace SPA

Následující rozhodnutí tabulka shrnuje některé základní faktory ke zvážení při výběru mezi tradičními webovými aplikací a SPA.

| **faktor**                                           | **Tradiční webové aplikace** | **Jednostránková aplikace** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| Požadované týmu znalost jazyka JavaScript/TypeScript | **Minimální**             | **Vyžaduje**                |
| Podpora prohlížeče bez skriptování                   | **Podporované**           | **Nepodporuje se**           |
| Chování minimální aplikace na straně klienta             | **Well-Suited**         | **Přehnaně**                |
| Požadavky na bohatě vybaveným a komplexní uživatelské rozhraní            | **Limited**             | **Well-Suited**             |

>[!div class="step-by-step"]
>[Předchozí](modern-web-applications-characteristics.md)
>[další](architectural-principles.md)