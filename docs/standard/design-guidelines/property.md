---
title: Návrh vlastnosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: e4ed4fd39a9ebd63b9d5dbff38dc15647d65934f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708984"
---
# <a name="property-design"></a>Návrh vlastnosti
Přestože jsou vlastnosti technicky velmi podobné metody, jsou značně odlišná z hlediska jejich scénáře použití. Měla by se zobrazit jako inteligentní pole. Mají volání syntaxe pole a flexibilitu metody.  
  
 **✓ DO** vytvořit vlastnosti jen pro get, pokud má volající neměli mít možnost ke změně hodnoty vlastnosti.  
  
 Mějte na paměti, že pokud typ vlastnosti je proměnlivý odkazový typ, hodnoty vlastnosti lze změnit i v případě, že vlastnost je určená jenom pro.  
  
 **X DO NOT** poskytnout setter s širší usnadnění než metoda getter vlastnosti jen pro sadu nebo vlastnosti.  
  
 Například nepoužívejte vlastnosti veřejné metody setter a getter chráněné.  
  
 Pokud metoda getter vlastnosti nejde zadat, implementujte funkci jako metodu. Vezměte v úvahu od názvu metody název `Set` a postupujte podle pokynů s co by mít pojmenujete vlastnost. Například <xref:System.AppDomain> obsahuje metodu nazvanou `SetCachePath` namísto toho, aby vlastnost jen pro sadu s názvem `CachePath`.  
  
 **✓ DO** zadejte rozumný výchozí hodnoty pro všechny vlastnosti, zajistíte, že výchozí hodnoty nezpůsobovalo neustálé bezpečnostní riziko nebo terribly neefektivní kód.  
  
 **✓ DO** povolit vlastnosti nastavit v libovolném pořadí, i když to vede k dočasné neplatný stav objektu.  
  
 Je běžné, že dva nebo více vlastností tak, aby vzájemně propojené do bodu, ve kterých některé hodnoty jednu vlastnost může být neplatný zadané hodnoty dalších vlastností na stejný objekt. V takovém případě by měly být výjimky vyplývající z neplatný stav odložit, dokud vzájemně propojené vlastnosti jsou skutečně používané tímto objektem společně.  
  
 **✓ DO** zachovat předchozí hodnotu, pokud metoda setter vlastnosti vyvolá výjimku.  
  
 **X AVOID** vyvolání výjimky z metody vlastnost getter.  
  
 Gettery vlastností by měl být jednoduché operace a nemají žádné předpoklady. Pokud getter může vyvolat výjimku, by pravděpodobně upravena jako metodu. Všimněte si, že toto pravidlo se nevztahuje na indexery, kde Očekáváme, že výjimky v důsledku ověřování argumentů.  
  
### <a name="indexed-property-design"></a>Indexovaná vlastnost návrhu  
 Indexovaná vlastnost je speciální vlastnost, která může mít parametry a mohou být volány pomocí speciální syntaxe podobná indexování pole.  
  
 Indexované vlastnosti se běžně označují jako indexery. Indexery by měla sloužit pouze v rozhraní API, která poskytuje přístup k položkám v logické kolekce. Například řetězec je kolekce znaků a indexer na <xref:System.String?displayProperty=nameWithType> byl přidán přístup k jeho znaků.  
  
 **✓ CONSIDER** použití indexery pro poskytnutí přístupu k datům uloženým v interní pole.  
  
 **✓ CONSIDER** poskytuje indexery na typy reprezentující kolekce položek.  
  
 **X AVOID** použití indexovaných vlastností s více než jeden parametr.  
  
 Pokud návrhu vyžaduje více parametrů, zvažte, jestli přistupující objekt vlastnosti ve skutečnosti představuje logické kolekce. Pokud tomu tak není, použijte metody. Vezměte v úvahu od názvu metody název `Get` nebo `Set`.  
  
 **X AVOID** indexery s typy parametrů jinak než <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, nebo výčet.  
  
 Pokud návrhu vyžaduje jiné typy parametrů, důrazně opětovné vyhodnocení, jestli přistupující objekt rozhraní API ve skutečnosti představuje logické kolekce. Pokud tomu tak není, použijte metodu. Vezměte v úvahu od názvu metody název `Get` nebo `Set`.  
  
 **✓ DO** použijte název `Item` pro indexovaných vlastností, pokud je samozřejmě lepší název (například najdete v článku <xref:System.String.Chars%2A> vlastnost na `System.String`).  
  
 V jazyce C# indexery jsou ve výchozím nastavení s názvem položky. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Lze upravit tento název.  
  
 **X DO NOT** zadejte indexer a metody, které jsou sémanticky ekvivalentní.  
  
 **X DO NOT** zadat více než jednu řadu přetížené indexery jednomu typu.  
  
 To je vynucena kompilátorem jazyka C#.  
  
 **X DO NOT** nevýchozí použití indexovaných vlastností.  
  
 To je vynucena kompilátorem jazyka C#.  
  
### <a name="property-change-notification-events"></a>Oznámení události změny vlastnosti  
 Někdy je užitečné poskytnout událost upozornění uživatele změny hodnoty vlastnosti. Například `System.Windows.Forms.Control` vyvolá `TextChanged` událostí po hodnota jeho `Text` je změněna vlastnost.  
  
 **✓ CONSIDER** vyvolání změnit události oznámení při změně hodnoty vlastností v vysoké úrovně rozhraní API (obvykle návrháře komponenty).  
  
 Pokud je dobré scénář pro uživatele potřebujete vědět, kdy je změna vlastnosti objektu, by měla vyvolat objekt událost oznámení o změně pro vlastnost.  
  
 Je ale pravděpodobné, aby za režie potřebná k vyvolání těchto událostí pro rozhraní API nízké úrovně, jako je například základní typy nebo kolekce. Například <xref:System.Collections.Generic.List%601> by vyvolat tyto události při přidání nové položky do seznamu a `Count` změny vlastností.  
  
 **✓ CONSIDER** vyvolání události oznámení při změně hodnoty vlastnosti prostřednictvím externí vynutí změn.  
  
 Pokud se změní hodnota vlastnosti prostřednictvím některé externí platnost (způsobem jinak než pomocí volání metody na objektu), vyvolat události znamenat pro vývojáře, že hodnota se mění a došlo ke změně. Dobrým příkladem je `Text` vlastnost ovládacího prvku textového pole. Když uživatel zadá text `TextBox`, automaticky změní hodnotu vlastnosti.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
