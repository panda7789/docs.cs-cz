---
title: Návrh události
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741684"
---
# <a name="event-design"></a>Návrh události
Události jsou nejčastěji používané formy zpětných volání (konstrukce, které umožňují rozhraní volat do uživatelského kódu). Mezi další mechanismy zpětného volání patří členové, kteří přijímají delegáty, virtuální členy a moduly plug-in založené na rozhraní. data z studií použitelnosti označují, že většina vývojářů je pohodlnější díky událostem, než používá jiné mechanismy zpětného volání. . Události jsou v ucelené integraci se sadou Visual Studio a mnoha jazyky.

 Je důležité si uvědomit, že existují dvě skupiny událostí: události vyvolané před stavem změny systému, nazývané před událostmi a události vyvolané po změně stavu, označované po událostech. Příkladem předběžné události by byla `Form.Closing`, která je aktivována před zavřením formuláře. Příkladem následné události by byl `Form.Closed`, který je vyvolán po zavření formuláře.

 ✔️ použít termín "vyvolat" pro události, nikoli "oheň" nebo "Trigger".

 ✔️ použít <xref:System.EventHandler%601?displayProperty=nameWithType> namísto ručního vytváření nových delegátů pro použití jako obslužných rutin událostí.

 ✔️ Zvažte použití podtřídy <xref:System.EventArgs> jako argumentu události, pokud nejste naprosto jistotu, že událost nebude nikdy potřebovat převést žádná data do metody zpracování událostí. v takovém případě lze typ `EventArgs` použít přímo.

 Pokud rozhraní API dodáváte přímo pomocí `EventArgs`, nebudete nikdy moci přidat žádná data, která by se měla přenést s událostí bez narušení kompatibility. Použijete-li podtřídu i v případě, že je zpočátku zcela prázdná, budete moci v případě potřeby přidat vlastnosti do podtřídy.

 k vyvolání každé události ✔️ použít chráněnou virtuální metodu. To platí pouze pro nestatické události pro nezapečetěné třídy, nikoli pro struktury, zapečetěné třídy nebo statické události.

 Účelem metody je poskytnout pro odvozenou třídu způsob, jakým má být událost zpracována pomocí přepsání. Přepisování je flexibilnější, rychlejší a přirozený způsob zpracování událostí základní třídy v odvozených třídách. Podle konvence má název metody začínat na "on" a musí následovat za názvem události.

 Odvozená třída může zvolit, že se má volat základní implementace metody v jejím přepsání. Připravte se na to bez jakéhokoli zpracování v metodě, která je nutná pro správné fungování základní třídy.

 ✔️ přijímá jeden parametr pro chráněnou metodu, která vyvolá událost.

 Parametr by měl mít název `e` a měl by být zadán jako třída argumentu události.

 Při vyvolání nestatické události ❌ Nepředávat jako odesilateli hodnotu null.

 Při vyvolání statické události ✔️ předat jako odesilateli hodnotu null.

 Při vyvolání události ❌ Nepředávat jako datový parametr události hodnotu null.

 Pokud nechcete předat žádná data do metody zpracování událostí, je vhodné předat `EventArgs.Empty`. Vývojáři očekávají, že tento parametr nemá hodnotu null.

 ✔️ Zvažte vyvolání událostí, které může koncový uživatel zrušit. To platí jenom pro předběžné události.

 Pokud chcete koncovému uživateli dovolit události zrušit, použijte <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako argument události.

### <a name="custom-event-handler-design"></a>Vlastní návrh obslužné rutiny událostí
 Existují případy, kdy `EventHandler<T>` nelze použít, například když rozhraní potřebuje pracovat se staršími verzemi modulu CLR, které nepodporovaly obecné typy. V takových případech může být nutné navrhnout a vyvinout delegáta vlastní obslužné rutiny události.

 ✔️ použít návratový typ void pro obslužné rutiny událostí.

 Obslužná rutina události může vyvolat více metod zpracování událostí, případně u více objektů. Pokud metody zpracování událostí povolily vrácení hodnoty, bude pro každé vyvolání události k dispozici více vrácených hodnot.

 ✔️ Použijte `object` jako typ prvního parametru obslužné rutiny události a zavolejte ho `sender`.

 ✔️ Použijte <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako typ druhého parametru obslužné rutiny události a zavolejte ji `e`.

 ❌ pro obslužné rutiny událostí neobsahují více než dva parametry.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
