---
title: Návrh vlastnosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 8b6570b1b7c292729b78f2fe52f24f73319efe6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743667"
---
# <a name="property-design"></a>Návrh vlastnosti
I když jsou vlastnosti technicky velmi podobné metodám, jsou v souladu s jejich scénáři použití poměrně odlišné. Měly by se zobrazit jako inteligentní pole. Mají volání syntaxe polí a flexibilitu metod.

 ✔️ vytvořit vlastnosti jen pro získání, pokud volající by neměl být schopný změnit hodnotu vlastnosti.

 Pamatujte, že pokud je typ vlastnosti proměnlivý typ odkazu, hodnota vlastnosti může být změněna i v případě, že je vlastnost určena pouze pro čtení.

 ❌ neposkytují vlastnosti nebo vlastnosti jen pro nastavení s vlastností setter širší přístupnost než getter.

 Nepoužívejte například vlastnosti s veřejnou setter a Protected getter.

 Pokud vlastnost getter nelze poskytnout, implementujte funkci namísto metody. Zvažte možnost spustit název metody s `Set` a sledujte, co byste měli pojmenovat vlastnost. Například <xref:System.AppDomain> má metodu nazvanou `SetCachePath` místo toho, aby byla vlastnost pouze set s názvem `CachePath`.

 ✔️ poskytují výchozí hodnoty rozumné pro všechny vlastnosti, což zajistí, že výchozí hodnoty nebudou mít za následek bezpečnostní riziko ani vážně selhalo neefektivní kód.

 ✔️ Povolit nastavení vlastností v libovolném pořadí, i když dojde k dočasnému neplatnému stavu objektu.

 Je běžné, že dvě nebo více vlastností bude možné vzájemně souviset s bodem, kde některé hodnoty jedné vlastnosti mohou být neplatné vzhledem k hodnotám jiných vlastností stejného objektu. V takových případech by měly být výjimky, které jsou výsledkem neplatného stavu, odloženy, dokud se tyto vlastnosti nepoužívají společně s objektem.

 ✔️ zachovat předchozí hodnotu, pokud vlastnost setter vyvolá výjimku.

 ❌ Vyhněte se vyvolávání výjimek z mechanismů getter vlastnosti.

 Metody getter vlastnosti by měly být jednoduché operace a neměly by obsahovat žádné předběžné podmínky. Pokud getter může vyvolat výjimku, měla by být pravděpodobně přepracována jako metoda. Všimněte si, že toto pravidlo se nevztahuje na indexery, kde očekáváme výjimky v důsledku ověřování argumentů.

### <a name="indexed-property-design"></a>Návrh indexovaných vlastností
 Indexovaná vlastnost je speciální vlastnost, která může mít parametry a může být volána se speciální syntaxí podobnou indexování pole.

 Indexované vlastnosti se běžně označují jako indexery. Indexery by měly být používány pouze v rozhraních API, která poskytují přístup k položkám v logické kolekci. Například řetězec je kolekce znaků a indexer na <xref:System.String?displayProperty=nameWithType> byl přidán pro přístup ke svým znakům.

 ✔️ Zvažte použití indexerů k poskytnutí přístupu k datům uloženým v interním poli.

 ✔️ Zvažte poskytování indexerů na typech představujících kolekce položek.

 ❌ se vyhnout použití indexovaných vlastností s více než jedním parametrem.

 Pokud návrh vyžaduje více parametrů, převezměte v úvahu, zda vlastnost ve skutečnosti představuje přistupující objekt k logické kolekci. Pokud ne, použijte místo toho metody. Zvažte možnost spustit název metody pomocí `Get` nebo `Set`.

 ❌ zabránit indexerům s jinými typy parametrů než <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>nebo Enum.

 Pokud návrh vyžaduje jiné typy parametrů, silně znovu Vyhodnoťte, jestli rozhraní API skutečně představuje přistupující objekt k logické kolekci. Pokud tomu tak není, použijte metodu. Zvažte možnost spustit název metody pomocí `Get` nebo `Set`.

 ✔️ použít název `Item` u indexovaných vlastností, pokud neexistuje zjevně lepší název (například, viz vlastnost <xref:System.String.Chars%2A> na `System.String`).

 V C#nástroji jsou indexery ve výchozím nastavení pojmenované položky. K přizpůsobení tohoto názvu lze použít <xref:System.Runtime.CompilerServices.IndexerNameAttribute>.

 ❌ neposkytují indexer a metody, které jsou sémanticky ekvivalentní.

 ❌ neposkytují více než jednu skupinu přetížených indexerů v jednom typu.

 Toto je vynutil C# kompilátorem.

 ❌ nepoužívat výchozí indexované vlastnosti.

 Toto je vynutil C# kompilátorem.

### <a name="property-change-notification-events"></a>Události upozornění na změnu vlastnosti
 Někdy je užitečné poskytnout událost upozorňující uživatele na změny v hodnotě vlastnosti. Například `System.Windows.Forms.Control` vyvolává událost `TextChanged` po změně hodnoty vlastnosti `Text`.

 ✔️ Zvažte vyvolání události oznámení o změně při změně hodnot vlastností v rozhraních API na vysoké úrovni (obvykle komponent návrháře).

 Pokud je dobrým scénářem, že uživatel ví, kdy se změní vlastnost objektu, měl by objekt vyvolat událost upozornění na změnu pro vlastnost.

 Nepředpokládá se však, že bude nutné zvýšit nároky na vyvolání takových událostí pro rozhraní API nižší úrovně, jako jsou základní typy nebo kolekce. <xref:System.Collections.Generic.List%601> například nevyvolává takové události, když se do seznamu přidá nová položka a změní se vlastnost `Count`.

 ✔️ Zvažte vyvolání události oznámení o změně při změně hodnoty vlastnosti prostřednictvím externích sil.

 Pokud se hodnota vlastnosti mění přes některé externí síly (způsobem, který je jiný než voláním metod objektu), vyvolávají události upozorňující na vývojáře, že se hodnota mění a změnila. Dobrým příkladem je vlastnost `Text` ovládacího prvku textového pole. Když uživatel zadá text do `TextBox`, hodnota vlastnosti se automaticky změní.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
