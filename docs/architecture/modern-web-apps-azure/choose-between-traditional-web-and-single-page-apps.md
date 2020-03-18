---
title: Volba mezi tradičními webovými aplikacemi a jednostránkovými aplikacemi
description: Přečtěte si, jak si vybrat mezi tradičními webovými aplikacemi a jednostránkovými aplikacemi (SPA) při vytváření webových aplikací.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450105"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Vyberte si mezi tradičními webovými aplikacemi a jednostránkovými aplikacemi (SPA)

> "Atwood zákon: Každá aplikace, která může být napsána v JavaScriptu, bude nakonec napsán v JavaScriptu."  
> _\-Jeff Atwood_

Existují dva obecné přístupy k vytváření webových aplikací dnes: tradiční webové aplikace, které provádějí většinu aplikační logiky na serveru, a jednostránkové aplikace (SP), které provádějí většinu logiky uživatelského rozhraní ve webovém prohlížeči, komunikace s webovým serverem především pomocí webových API. Hybridní přístup je také možné, nejjednodušší je hostit jeden nebo více bohatých SPA-jako podaplikace v rámci větší tradiční webové aplikace.

Tradiční webové aplikace používejte v::

- Požadavky na straně klienta vaší aplikace jsou jednoduché nebo dokonce jen pro čtení.

- Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu.

- Váš tým není obeznámen s vývojovými technikami JavaScriptu nebo TypeScriptu.

Spa použijte, když:

- Aplikace musí vystavit bohaté uživatelské rozhraní s mnoha funkcemi.

- Váš tým je obeznámen s vývojem JavaScriptu a/nebo TypeScriptu.

- Aplikace již musí vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.

Kromě toho spa architektury vyžadují větší architektonické a bezpečnostní znalosti. Zažívají větší konve kvůli častým aktualizacím a novým architekturám než tradiční webové aplikace. Konfigurace automatizovaných procesů sestavení a nasazení a využití možností nasazení, jako jsou kontejnery, může být obtížnější s aplikacemi SPA než u tradičních webových aplikací.

Zlepšení uživatelské zkušenosti umožněné přístupem SPA musí být porovnáno s těmito úvahami.

## <a name="blazor"></a>Blazor

ASP.NET Core 3.0 představuje nový model pro vytváření bohatého, interaktivního a kompozičného ui s názvem Blazor. Blazor server-side umožňuje vývojářům vytvářet uživatelské rozhraní s břitvou na serveru a pro tento kód, které mají být dodány do prohlížeče a provedeny client-side pomocí [WebAssembly](https://webassembly.org/). Blazor server-side je nyní k dispozici s ASP.NET Core 3.0 nebo novější. Blazor klientská strana by měla být k dispozici v roce 2020.

Blazor poskytuje novou, třetí možnost, aby zvážila při hodnocení, zda vytvořit čistě server-poskytnuté webové aplikace nebo SPA. Můžete vytvářet bohaté, SPA-jako klient-side chování pomocí Blazor, bez nutnosti významného vývoje JavaScriptu. Aplikace Blazor mohou volat api pro vyžádání dat nebo provádění operací na straně serveru.

Zvažte vytvoření webové aplikace s Blazor, když:

- Aplikace musí vystavit bohaté uživatelské rozhraní

- Váš tým je s vývojem .NET pohodlnější než vývoj JavaScriptu nebo TypeScriptu

Další informace o Blazoru najdete [v tématu Začínáme s Blazorem](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Kdy si vybrat tradiční webové aplikace

Následuje podrobnější vysvětlení dříve uvedených důvodů pro výběr tradičních webových aplikací.

**Aplikace má jednoduché, případně jen pro čtení, požadavky na straně klienta**

Mnoho webových aplikací jsou primárně konzumovány v jen pro čtení způsobem drtivá většina jejich uživatelů. Aplikace jen pro čtení (nebo většinou pro čtení) mají tendenci být mnohem jednodušší než ty, které udržují a manipulují s velkým státem. Vyhledávač se může například skládat z jednoho vstupního bodu s textovým polem a druhé stránky pro zobrazení výsledků hledání. Anonymní uživatelé mohou snadno provádět požadavky a je málo potřeba logiky na straně klienta. Podobně, blog nebo systém pro správu obsahu veřejné aplikace obvykle se skládá hlavně z obsahu s malým chováním na straně klienta. Tyto aplikace jsou snadno postaveny jako tradiční webové aplikace založené na serveru, které provádějí logiku na webovém serveru a vykreslují HTML, které mají být zobrazeny v prohlížeči. Skutečnost, že každá jedinečná stránka webu má svou vlastní adresu URL, která může být záložkou a indexována vyhledávači (ve výchozím nastavení, aniž by bylo třeba ji přidávat jako samostatnou vlastnost aplikace), je také jasným přínosem v takových scénářích.

**Vaše aplikace musí fungovat v prohlížečích bez podpory JavaScriptu**

Webové aplikace, které potřebují fungovat v prohlížečích s omezenou nebo žádnou podporou JavaScriptu, by měly být napsány pomocí tradičních pracovních postupů webové aplikace (nebo alespoň být schopen se k takovému chování vrátit). Technologie BEZ OV Vyžadují javascript na straně klienta, aby fungoval; Pokud není k dispozici, nejsou spa dobrou volbou.

**Váš tým není obeznámen s technologiemi vývoje JavaScriptu nebo TypeScriptu**

Pokud váš tým není obeznámen s JavaScriptem nebo TypeScriptem, ale je obeznámen s vývojem webových aplikací na straně serveru, pak bude pravděpodobně schopen dodat tradiční webovou aplikaci rychleji než SPA. Pokud není požadováno naučit se programovat plány SPNebo nebo pokud není vyžadováno uživatelské prostředí poskytované spa, jsou tradiční webové aplikace produktivnější volbou pro týmy, které jsou již obeznámeny s jejich vytvářením.

## <a name="when-to-choose-spas"></a>Kdy si vybrat sraby

Následuje podrobnější vysvětlení, kdy zvolit styl vývoje aplikací s jednou stránkou pro webovou aplikaci.

**Aplikace musí vystavit bohaté uživatelské rozhraní s mnoha funkcemi**

Místní certifikační konzole mohou podporovat bohaté funkce na straně klienta, které nevyžadují opětovné načtení stránky, protože uživatelé provází akce nebo procházet mezi oblastmi aplikace. Technologie ZABEZPEČENÍ se mohou načítat rychleji, načítat data na pozadí a akce jednotlivých uživatelů jsou citlivější, protože opětovné načtení celé stránky je vzácné. Technologie SRAB mohou podporovat přírůstkové aktualizace a ukládat částečně vyplněné formuláře nebo dokumenty, aniž by uživatel musel kliknout na tlačítko pro odeslání formuláře. SpA může podporovat bohaté chování na straně klienta, jako je například přetažení, mnohem snadněji než tradiční aplikace. Certifikáty zabezpečení mohou být navrženy tak, aby běžely v odpojeném režimu a aby byly aktualizovány modely na straně klienta, které jsou nakonec synchronizovány zpět na server po obnovení připojení. Pokud požadavky aplikace zahrnují bohaté funkce, které přesahují rámec toho, co nabízejí typické formuláře HTML, zvolte aplikaci ve stylu SPA.

Často je třeba implementovat funkce, které jsou integrovány do tradičních webových aplikací, jako je například zobrazení smysluplné adresy URL v adresním řádku odrážející aktuální operaci (a umožňuje uživatelům záložku nebo přímý odkaz na tuto adresu URL pro návrat k ní). Místní ochrana osobních and sifanů by také měla uživatelům umožnit používat tlačítka prohlížeče pro záda a vpřed s výsledky, které je nepřekvapí.

**Váš tým je obeznámen s vývojem JavaScriptu a/nebo TypeScriptu**

Psaní postupů pro řešení v řepa vyžaduje znalost JavaScriptu a/nebo TypeScriptu a programovacích technik a knihoven na straně klienta. Váš tým by měl být kompetentní v psaní moderní JavaScript pomocí SPA framework jako Angular.

> ### <a name="references--spa-frameworks"></a>Reference – SPA Frameworks
>
> - **Angular**  
>   <https://angular.io>
> - **Reagovat**
>   <https://reactjs.org/>
> - **Porovnání javascriptových rámců**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Aplikace již musí vystavit rozhraní API pro jiné (interní nebo veřejné) klienty.**

Pokud již podporujete webové rozhraní API pro použití jinými klienty, může vyžadovat méně úsilí k vytvoření implementace SPA, která využívá tato rozhraní API, spíše než reprodukovat logiku ve formě na straně serveru. Sraby rozsáhle využívají webová řešení API k dotazování a aktualizaci dat při interakci uživatelů s aplikací.

## <a name="when-to-choose-blazor"></a>Kdy si vybrat Blazor

Následuje podrobnější vysvětlení, kdy si vybrat Blazor pro vaši webovou aplikaci.

**Aplikace musí vystavit bohaté uživatelské rozhraní**

Stejně jako JavaScript-založené SPA, Blazor aplikace mohou podporovat bohaté chování klienta bez opětovného načtení stránky. Tyto aplikace lépe reagují na uživatele a načítají pouze data (nebo HTML) potřebná k reakci na danou interakci s uživatelem. Správně navrženy aplikace Blazor na straně serveru lze nakonfigurovat tak, aby běžely jako aplikace Blazor na straně klienta s minimálními změnami, jakmile je tato funkce podporována.

**Váš tým je s vývojem .NET pohodlnější než vývoj JavaScriptu nebo TypeScriptu**

Mnoho vývojářů je produktivnějších s rozhraními .NET a Razor než s jazyky na straně klienta, jako je JavaScript nebo TypeScript. Vzhledem k tomu, že serverová strana aplikace je již vyvíjena s rozhraním .NET, pomocí Blazor zajišťuje, že každý vývojář rozhraní .NET v týmu může pochopit a potenciálně vytvořit chování front-endu aplikace.

## <a name="decision-table"></a>Tabulka rozhodnutí

Následující tabulka rozhodnutí shrnuje některé základní faktory, které je třeba vzít v úvahu při výběru mezi tradiční webovou aplikací, spa nebo aplikací Blazor.

| **Faktor**                                           | **Tradiční webová aplikace** | **Jednostránková aplikace** | **Aplikace Blazor**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| Požadovaná znalost týmu s JavaScriptem/TypeScriptem | **Minimální**             | **Požadováno**                | **Minimální**     |
| Podpora prohlížečů bez skriptování                   | **Podporovány**           | **Nepodporuje se**           | **Podporovány**   |
| Minimální chování aplikace na straně klienta             | **Dobře se hodí**         | **Zbytečná**                | **Životaschopné**      |
| Bohaté a komplexní požadavky na uživatelské rozhraní            | **Omezeně**             | **Dobře se hodí**             | **Dobře se hodí** |

>[!div class="step-by-step"]
>[Předchozí](modern-web-applications-characteristics.md)
>[další](architectural-principles.md)
