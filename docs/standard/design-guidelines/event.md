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
ms.openlocfilehash: 852c99b1a41691911f7ae82d3b8104526811757d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289821"
---
# <a name="event-design"></a>Návrh události
Události jsou nejčastěji používané formy zpětných volání (konstrukce, které umožňují rozhraní volat do uživatelského kódu). Mezi další mechanismy zpětného volání patří členové, kteří přijímají delegáty, virtuální členy a moduly plug-in založené na rozhraní. data z studií použitelnosti označují, že většina vývojářů je pohodlnější díky událostem, než používá jiné mechanismy zpětného volání. Události jsou v ucelené integraci se sadou Visual Studio a mnoha jazyky.

 Je důležité si uvědomit, že existují dvě skupiny událostí: události vyvolané před stavem změny systému, nazývané před událostmi a události vyvolané po změně stavu, označované po událostech. Příkladem předběžné události by byla `Form.Closing` vyvolána před zavřením formuláře. Příkladem následné události `Form.Closed` , která je vyvolána po zavření formuláře.

 ✔️ použít termín "vyvolat" pro události, nikoli "oheň" nebo "Trigger".

 ✔️ použít <xref:System.EventHandler%601?displayProperty=nameWithType> místo ručního vytváření nových delegátů pro použití jako obslužných rutin událostí.

 ✔️ Zvažte použití podtřídy <xref:System.EventArgs> jako argumentu události, pokud nejste naprosto jistotu, že událost nebude nikdy potřebovat převést žádná data do metody zpracování událostí, v takovém případě lze `EventArgs` typ použít přímo.

 Pokud rozhraní API dodáváte přímo pomocí nástroje, nebudete `EventArgs` nikdy moci přidat žádná data, která by se měla přenést s událostí bez narušení kompatibility. Použijete-li podtřídu i v případě, že je zpočátku zcela prázdná, budete moci v případě potřeby přidat vlastnosti do podtřídy.

 k vyvolání každé události ✔️ použít chráněnou virtuální metodu. To platí pouze pro nestatické události pro nezapečetěné třídy, nikoli pro struktury, zapečetěné třídy nebo statické události.

 Účelem metody je poskytnout pro odvozenou třídu způsob, jakým má být událost zpracována pomocí přepsání. Přepisování je flexibilnější, rychlejší a přirozený způsob zpracování událostí základní třídy v odvozených třídách. Podle konvence má název metody začínat na "on" a musí následovat za názvem události.

 Odvozená třída může zvolit, že se má volat základní implementace metody v jejím přepsání. Připravte se na to bez jakéhokoli zpracování v metodě, která je nutná pro správné fungování základní třídy.

 ✔️ přijímá jeden parametr pro chráněnou metodu, která vyvolá událost.

 Parametr by měl mít název `e` a měl by být zadán jako třída argumentu události.

 ❌Při vyvolávání nestatické události nepředávejte jako odesilatele hodnotu null.

 Při vyvolání statické události ✔️ předat jako odesilateli hodnotu null.

 ❌Při vyvolání události nepředávejte jako datový parametr události hodnotu null.

 Měli byste předat, `EventArgs.Empty` Pokud nechcete předat žádná data metodě zpracování událostí. Vývojáři očekávají, že tento parametr nemá hodnotu null.

 ✔️ Zvažte vyvolání událostí, které může koncový uživatel zrušit. To platí jenom pro předběžné události.

 Použijte <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako argument události, aby mohl koncový uživatel události zrušit.

### <a name="custom-event-handler-design"></a>Vlastní návrh obslužné rutiny událostí
 Existují případy `EventHandler<T>` , kdy nelze použít, například když rozhraní potřebuje pracovat s dřívějšími verzemi modulu CLR, které nepodporovaly obecné typy. V takových případech může být nutné navrhnout a vyvinout delegáta vlastní obslužné rutiny události.

 ✔️ použít návratový typ void pro obslužné rutiny událostí.

 Obslužná rutina události může vyvolat více metod zpracování událostí, případně u více objektů. Pokud metody zpracování událostí povolily vrácení hodnoty, bude pro každé vyvolání události k dispozici více vrácených hodnot.

 ✔️ použít `object` jako typ prvního parametru obslužné rutiny události a zavolat ho `sender` .

 ✔️ použijte <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídu jako typ druhého parametru obslužné rutiny události a zavolejte ji `e` .

 ❌Nemusíte mít více než dva parametry pro obslužné rutiny událostí.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh členů](member.md)
- [Pokyny k návrhu architektury](index.md)
