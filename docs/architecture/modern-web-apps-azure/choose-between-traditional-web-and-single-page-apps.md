---
title: Volba mezi tradičními webovými aplikacemi a jednostránkovými aplikacemi
description: Naučte se při sestavování webových aplikací zvolit mezi tradičními webovými aplikacemi a jednostránkové (Single Page Applications).
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9ede64249705aba3f22a9663b8a258e41f030aca
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739452"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Volba mezi tradičními Web Apps a jednostránkové aplikacemi

> "Zákonem o atwoodemi: Jakákoliv aplikace, kterou lze zapsat do JavaScriptu, bude nakonec napsána v JavaScriptu."  
> _\- Jan Atwoodem_

Existují dva obecné přístupy k sestavování webových aplikací Dnes: tradiční webové aplikace, které provádějí většinu aplikační logiky na serveru a jednostránkové aplikace (jednostránkové), které provádějí většinu logiky uživatelského rozhraní ve webovém prohlížeči. komunikace s webovým serverem primárně využívá webová rozhraní API. K dispozici je také hybridní přístup, nejjednodušší je hostovat jeden nebo více propracovaných podaplikací, které jsou v rámci větší tradiční webové aplikace.

Tradiční webové aplikace byste měli používat v těchto případech:

- Požadavky vaší aplikace na straně klienta jsou jednoduché nebo dokonce jen pro čtení.

- Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu.

- Váš tým není obeznámen s techniky vývoje JavaScriptu nebo TypeScript.

SPA byste měli používat v těchto případech:

- Vaše aplikace musí vystavovat bohatší uživatelské rozhraní s mnoha funkcemi.

- Váš tým je obeznámen s vývojem JavaScript a/nebo TypeScript.

- Vaše aplikace musí již vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.

Kromě toho architektura SPA vyžaduje větší architekturu a odbornosti zabezpečení. Dochází k většímu množství změn v důsledku častých aktualizací a nových architektur než tradičních webových aplikací. Konfigurace automatizovaných procesů sestavování a nasazování a využití možností nasazení, jako jsou kontejnery, jsou obtížnější s aplikacemi SPA než s tradičními webovými aplikacemi.

Vylepšení uživatelského prostředí, které je možné použít modelem SPA, je třeba zvážit na základě těchto požadavků.

## <a name="blazor"></a>Blazor

ASP.NET Core 3,0 zavádí nový model pro vytváření bohatých, interaktivních a sestavitelního uživatelského rozhraní s názvem Blazor. Blazor na straně serveru umožňuje vývojářům vytvořit uživatelské rozhraní se syntaxí Razor na serveru a pro tento kód pro doručení do prohlížeče a spuštění na straně klienta pomocí webového [sestavení](https://webassembly.org/). ASP.NET Core 3,0 je stále ve vývoji, ale měli byste očekávat, že v aktualizaci 3,0 pro tuto elektronickou knihu získáte další informace o této technologii. Další informace o Blazor najdete v tématu Začínáme [s Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Kdy zvolit tradiční webové aplikace

Následuje podrobnější vysvětlení výše uvedených důvodů pro vybírání tradičních webových aplikací.

**Vaše aplikace má jednoduché, možná jen pro čtení, požadavky na na straně klienta.**

Mnohé webové aplikace jsou primárně využívány způsobem, který je určen jen pro čtení, prostřednictvím obrovské většiny jejich uživatelů. Aplikace jen pro čtení (nebo jen pro čtení) jsou obvykle mnohem jednodušší než ty, které udržují a manipulují s velkým stavem. Například vyhledávací stroj může sestávat z jediného vstupního bodu s textovým polem a druhou stránkou pro zobrazení výsledků hledání. Anonymní uživatelé můžou snadno vytvářet požadavky a pro logiku na straně klienta je málo nutná. Podobně se jako veřejná aplikace pro blog nebo systém správy obsahu obvykle skládá hlavně z hlediska obsahu s malým chováním na straně klienta. Tyto aplikace jsou snadno sestavené jako tradiční webové aplikace založené na serveru, které na webovém serveru provádějí logiku a vykreslují HTML pro zobrazení v prohlížeči. Skutečnost, že každá jedinečná stránka webu má svou vlastní adresu URL, kterou je možné zadělit a indexovat vyhledávacími moduly (ve výchozím nastavení je to bez nutnosti přidat tuto možnost jako samostatnou funkci aplikace) je také v takových scénářích jasné zvýhodnění.

**Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu.**

Webové aplikace, které potřebují fungovat v prohlížečích s omezením nebo bez podpory JavaScriptu, by měly být zapsány pomocí tradičních pracovních postupů webové aplikace (nebo je musí být možné vrátit k takovému chování). Jednostránkové vyžaduje JavaScript na straně klienta, aby fungoval. Pokud není k dispozici, není jednostránkové vhodným řešením.

**Váš tým není obeznámen s techniky vývoje JavaScriptu nebo TypeScript.**

Pokud váš tým není obeznámen s jazykem JavaScript nebo TypeScript, ale je obeznámen s vývojem webových aplikací na straně serveru, bude pravděpodobně moci doručovat tradiční webovou aplikaci rychleji než SPA. Pokud se jednostránkové, že se naučíte programovat program, nebo se vyžaduje uživatelské prostředí, které zabezpečené SPA vyžaduje, jsou tradiční webové aplikace efektivnější volbou pro týmy, které už jsou obeznámené sestavou.

## <a name="when-to-choose-spas"></a>Kdy zvolit jednostránkové

Následuje podrobnější vysvětlení, kdy zvolit pro vaši webovou aplikaci styl jedné stránky pro vývoj aplikací.

**Vaše aplikace musí vystavovat bohatší uživatelské rozhraní s mnoha funkcemi.**

Jednostránkové může podporovat bohatou funkcionalitu na straně klienta, která nevyžaduje opětovné načtení stránky, protože uživatelé probírají akce nebo přecházejí mezi oblastmi aplikace. Jednostránkové se může načíst rychleji, načítat data na pozadí a jednotlivé akce uživatelů jsou větší reakce, protože celá data na stránce jsou zřídka. Jednostránkové může podporovat přírůstkové aktualizace, ukládat částečně dokončené formuláře nebo dokumenty, aniž by uživatel musel kliknout na tlačítko pro odeslání formuláře. Jednostránkové může podporovat rozsáhlá chování na straně klienta, jako je například přetahování, mnohem jednodušší než tradiční aplikace. Jednostránkové může být navržená tak, aby běžela v odpojeném režimu a prováděla aktualizace modelu na straně klienta, které se nakonec po opětovném navázání připojení zpátky na server. Pokud požadavky vaší aplikace zahrnují bohatou funkčnost, která překračuje možnosti, které se zobrazí v typických formulářích HTML, měli byste zvolit aplikaci stylu SPA.

Všimněte si, že často jednostránkové potřebovat implementovat funkce, které jsou integrované do tradičních webových aplikací, jako je například zobrazení smysluplné adresy URL na adresním řádku odrážet aktuální operaci (a povolením, aby se uživatelé mohli k této adrese URL vrátit pomocí záložky nebo přímý odkaz). Jednostránkové by měl také uživatelům dovolit, aby používali tlačítka pro zpět a přeposílání v prohlížeči s výsledky, které se na ně neočekávaně.

**Váš tým je obeznámen s vývojem JavaScript a/nebo TypeScript.**

Psaní jednostránkové vyžaduje znalost pomocí JavaScriptu a/nebo TypeScript a postupů programování a knihoven na straně klienta. Váš tým by měl být příslušný pro psaní moderního JavaScriptu pomocí architektury SPA, jako je například úhlová.

> ### <a name="references--spa-frameworks"></a>Odkazy – rozhraní SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Porovnání platforem JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Vaše aplikace už musí vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.**

Pokud už podporujete webové rozhraní API pro použití jinými klienty, může to vyžadovat menší úsilí k vytvoření implementace SPA, která tato rozhraní API využívá místo reprodukce logiky ve formuláři na straně serveru. Jednostránkové rozsáhlých použití webových rozhraní API k dotazování a aktualizaci dat, když uživatelé pracují s aplikací.

## <a name="decision-table--traditional-web-or-spa"></a>Tabulka rozhodnutí – tradiční web nebo SPA

Následující rozhodovací tabulka shrnuje některé základní faktory, které je potřeba vzít v úvahu při volbě mezi tradiční webovou aplikací a SPA.

| **Jednotek**                                           | **Tradiční webová aplikace** | **Jednostránková aplikace** |
| ---------------------------------------------------- | ----------------------- | --------------------------- |
| Požadovaný tým se znalostí jazyka JavaScript a TypeScript | **Poskytuje**             | **Požadovanou**                |
| Podpora prohlížečů bez skriptování                   | **Doložen**           | **Nepodporováno**           |
| Minimální chování aplikace na straně klienta             | **Dobře hodící se**         | **Přehnaně důkladné**                |
| Bohatě komplexní požadavky na uživatelské rozhraní            | **Limitovan**             | **Dobře hodící se**             |

>[!div class="step-by-step"]
>[Předchozí](modern-web-applications-characteristics.md)
>[Další](architectural-principles.md)
