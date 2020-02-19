---
title: Volba mezi tradičními webovými aplikacemi a jednostránkovými aplikacemi
description: Naučte se při sestavování webových aplikací zvolit mezi tradičními webovými aplikacemi a jednostránkové (Single Page Applications).
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450105"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Volba mezi tradičními Web Apps a jednostránkové aplikacemi

> "Zákonem o atwoodemi: Jakákoliv aplikace, kterou lze zapsat do JavaScriptu, bude nakonec napsána v JavaScriptu."  
> _\- Jan Atwoodem_

Existují dva obecné přístupy k sestavování webových aplikací Dnes: tradiční webové aplikace, které provádějí většinu aplikační logiky na serveru a jednostránkové aplikace (jednostránkové), které provádějí většinu logiky uživatelského rozhraní ve webovém prohlížeči. komunikace s webovým serverem primárně využívá webová rozhraní API. K dispozici je také hybridní přístup, nejjednodušší je hostovat jednu nebo více propracovaných podprocesů, které se budou líbit, jako v rámci větší tradiční webové aplikace.

Tradiční webové aplikace používejte v těchto případech:

- Požadavky vaší aplikace na straně klienta jsou jednoduché nebo dokonce jen pro čtení.

- Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu.

- Váš tým není obeznámen s techniky vývoje JavaScriptu nebo TypeScript.

Zabezpečené ověřování pomocí hesla použijte v těchto případech:

- Vaše aplikace musí vystavovat bohatší uživatelské rozhraní s mnoha funkcemi.

- Váš tým je obeznámen s vývojem JavaScript a/nebo TypeScript.

- Vaše aplikace musí již vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.

Kromě toho architektura SPA vyžaduje větší architekturu a odbornosti zabezpečení. Dochází k většímu množství změn v důsledku častých aktualizací a nových architektur než tradičních webových aplikací. Konfigurace automatizovaných procesů sestavování a nasazování a využití možností nasazení, jako jsou kontejnery, můžou být obtížnější s aplikacemi SPA než s tradičními webovými aplikacemi.

Vylepšení uživatelského prostředí, které může přístup k zabezpečenému přístupu přes SPA udělat, je třeba zvážit na základě těchto doporučení.

## <a name="blazor"></a>Blazor

ASP.NET Core 3,0 zavádí nový model pro vytváření bohatých, interaktivních a sestavitelního uživatelského rozhraní s názvem Blazor. Blazor na straně serveru umožňuje vývojářům vytvořit uživatelské rozhraní se syntaxí Razor na serveru a pro tento kód pro doručení do prohlížeče a spuštění na straně klienta pomocí webového [sestavení](https://webassembly.org/). Blazor Server je teď k dispozici v ASP.NET Core 3,0 nebo novějším. Blazor na straně klienta by měla být k dispozici v 2020.

Blazor poskytuje novou, třetí možnost, kterou je třeba vzít v úvahu při vyhodnocování, jestli se má sestavit čistě webová aplikace vydaná serverem nebo SPA. Pomocí Blazor můžete sestavovat bohatě, SPA jako chování na straně klienta a nemusíte přitom významně vyvíjet JavaScript. Aplikace Blazor můžou volat rozhraní API pro vyžádání dat nebo provádění operací na straně serveru.

Zvažte vytvoření webové aplikace pomocí Blazor v těchto případech:

- Vaše aplikace musí vystavovat bohatší uživatelské rozhraní.

- Váš tým je pohodlnější při vývoji .NET, než JavaScript nebo vývoj TypeScript.

Další informace o Blazor najdete v tématu Začínáme [s Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Kdy zvolit tradiční webové aplikace

Následuje podrobnější vysvětlení výše uvedených důvodů pro vybírání tradičních webových aplikací.

**Vaše aplikace má jednoduché, možná jen pro čtení, požadavky na na straně klienta.**

Mnohé webové aplikace jsou primárně využívány způsobem, který je určen jen pro čtení, prostřednictvím obrovské většiny jejich uživatelů. Aplikace jen pro čtení (nebo jen pro čtení) jsou obvykle mnohem jednodušší než ty, které udržují a manipulují s velkým stavem. Například vyhledávací stroj může sestávat z jediného vstupního bodu s textovým polem a druhou stránkou pro zobrazení výsledků hledání. Anonymní uživatelé můžou snadno vytvářet požadavky a pro logiku na straně klienta je málo nutná. Podobně se jako veřejná aplikace pro blog nebo systém správy obsahu obvykle skládá hlavně z hlediska obsahu s malým chováním na straně klienta. Tyto aplikace jsou snadno sestavené jako tradiční webové aplikace založené na serveru, které provádějí logiku na webovém serveru a vykreslují HTML pro zobrazení v prohlížeči. Skutečnost, že každá jedinečná stránka webu má svou vlastní adresu URL, kterou je možné zadělit a indexovat vyhledávacími moduly (ve výchozím nastavení je to bez nutnosti přidat tuto možnost jako samostatnou funkci aplikace) je také v takových scénářích jasné zvýhodnění.

**Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu.**

Webové aplikace, které potřebují fungovat v prohlížečích s omezením nebo bez podpory JavaScriptu, by měly být zapsány pomocí tradičních pracovních postupů webové aplikace (nebo je musí být možné vrátit k takovému chování). Jednostránkové vyžaduje JavaScript na straně klienta, aby fungoval. Pokud není k dispozici, není jednostránkové vhodným řešením.

**Váš tým není obeznámen s techniky vývoje JavaScriptu nebo TypeScript.**

Pokud váš tým není obeznámen s jazykem JavaScript nebo TypeScript, ale je obeznámen s vývojem webových aplikací na straně serveru, bude pravděpodobně moci doručovat tradiční webovou aplikaci rychleji než SPA. Pokud se jednostránkové, že se naučíte programovat program, nebo se vyžaduje uživatelské prostředí, které zabezpečené SPA vyžaduje, jsou tradiční webové aplikace efektivnější volbou pro týmy, které už jsou obeznámené sestavou.

## <a name="when-to-choose-spas"></a>Kdy zvolit jednostránkové

Následuje podrobnější vysvětlení, kdy zvolit pro vaši webovou aplikaci styl jedné stránky pro vývoj aplikací.

**Vaše aplikace musí vystavovat bohatší uživatelské rozhraní s mnoha funkcemi.**

Jednostránkové může podporovat bohatou funkcionalitu na straně klienta, která nevyžaduje opětovné načtení stránky, protože uživatelé probírají akce nebo přecházejí mezi oblastmi aplikace. Jednostránkové se může načíst rychleji, načítat data na pozadí a jednotlivé akce uživatelů jsou větší reakce, protože celá data na stránce jsou zřídka. Jednostránkové může podporovat přírůstkové aktualizace, ukládat částečně dokončené formuláře nebo dokumenty, aniž by uživatel musel kliknout na tlačítko pro odeslání formuláře. Jednostránkové může podporovat rozsáhlá chování na straně klienta, jako je například přetahování, mnohem jednodušší než tradiční aplikace. Jednostránkové může být navržená tak, aby běžela v odpojeném režimu a prováděla aktualizace modelu na straně klienta, které se nakonec po opětovném navázání připojení zpátky na server. Pokud požadavky vaší aplikace obsahují bohatou funkci, která překračuje možnosti, které se zobrazí v typických formulářích HTML, vyberte aplikaci ve stylu SPA.

Jednostránkové je často potřeba implementovat funkce, které jsou integrované do tradičních webových aplikací, jako je například zobrazení smysluplné adresy URL na adresním řádku odrážet aktuální operaci (a povolením, aby uživatelé mohli k této adrese URL přejít nebo přímý odkaz). Jednostránkové by měl také uživatelům dovolit, aby používali tlačítka pro zpět a přeposílání v prohlížeči s výsledky, které se na ně neočekávaně.

**Váš tým je obeznámen s vývojem JavaScript a/nebo TypeScript.**

Psaní jednostránkové vyžaduje znalost pomocí JavaScriptu a/nebo TypeScript a postupů programování a knihoven na straně klienta. Váš tým by měl být příslušný pro psaní moderního JavaScriptu pomocí architektury SPA, jako je například úhlová.

> ### <a name="references--spa-frameworks"></a>Odkazy – rozhraní SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Reakce**
>   <https://reactjs.org/>
> - **Porovnání platforem JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Vaše aplikace už musí vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.**

Pokud už podporujete webové rozhraní API pro použití jinými klienty, může to vyžadovat menší úsilí k vytvoření implementace SPA, která tato rozhraní API využívá místo reprodukce logiky ve formuláři na straně serveru. Jednostránkové rozsáhlých použití webových rozhraní API k dotazování a aktualizaci dat, když uživatelé pracují s aplikací.

## <a name="when-to-choose-blazor"></a>Kdy zvolit Blazor

Následuje podrobnější vysvětlení, kdy zvolit Blazor pro vaši webovou aplikaci.

**Vaše aplikace musí vystavovat bohatší uživatelské rozhraní.**

Podobně jako jednostránkové založené na JavaScriptu můžou aplikace Blazor podporovat bohatá chování klienta bez nutnosti opětovného načtení stránky. Tyto aplikace jsou lépe reagují na uživatele a načítají se pouze data (nebo HTML), která jsou nutná k reakci na danou interakci uživatele. Správně navržené aplikace Blazor na straně serveru můžou být nakonfigurované tak, aby se spouštěly jako aplikace Blazor na straně klienta s minimálními změnami, jakmile je tato funkce podporovaná.

**Váš tým je pohodlnější při vývoji .NET, než JavaScript nebo vývoj TypeScript.**

Mnoho vývojářů nabízí vyšší produktivitu díky .NET a Razor než s jazyky na straně klienta, jako je JavaScript nebo TypeScript. Vzhledem k tomu, že serverová strana aplikace je již vyvíjena pomocí technologie .NET, aplikace Blazor zajistí, že každý vývojář rozhraní .NET v týmu může pochopit a potenciálně sestavit chování pro front-end aplikace.

## <a name="decision-table"></a>Tabulka rozhodnutí

Následující rozhodovací tabulka shrnuje některé základní faktory, které je potřeba vzít v úvahu při volbě mezi tradiční webovou aplikací, ZABEZPEČENou nebo Blazor aplikací.

| **Jednotek**                                           | **Tradiční webová aplikace** | **Jednostránková aplikace** | **Aplikace Blazor**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| Požadovaný tým se znalostí jazyka JavaScript a TypeScript | **Poskytuje**             | **Požadovanou**                | **Poskytuje**     |
| Podpora prohlížečů bez skriptování                   | **Podporuje se**           | **Nepodporuje se**           | **Podporuje se**   |
| Minimální chování aplikace na straně klienta             | **Dobře hodící se**         | **Přehnaně důkladné**                | **Realizovat**      |
| Bohatě komplexní požadavky na uživatelské rozhraní            | **Limitovan**             | **Dobře hodící se**             | **Dobře hodící se** |

>[!div class="step-by-step"]
>[Předchozí](modern-web-applications-characteristics.md)
>[Další](architectural-principles.md)
