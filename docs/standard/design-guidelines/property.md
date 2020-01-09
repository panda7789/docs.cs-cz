---
title: Návrh vlastnosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 5d5cdbfdb38c7aebaca6cbcdeb63959ac12884e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709124"
---
# <a name="property-design"></a>Návrh vlastnosti
I když jsou vlastnosti technicky velmi podobné metodám, jsou v souladu s jejich scénáři použití poměrně odlišné. Měly by se zobrazit jako inteligentní pole. Mají volání syntaxe polí a flexibilitu metod.  
  
 **✓ DO** vytvořit vlastnosti jen pro get, pokud má volající neměli mít možnost ke změně hodnoty vlastnosti.  
  
 Pamatujte, že pokud je typ vlastnosti proměnlivý typ odkazu, hodnota vlastnosti může být změněna i v případě, že je vlastnost určena pouze pro čtení.  
  
 **X DO NOT** poskytnout setter s širší usnadnění než metoda getter vlastnosti jen pro sadu nebo vlastnosti.  
  
 Nepoužívejte například vlastnosti s veřejnou setter a Protected getter.  
  
 Pokud vlastnost getter nelze poskytnout, implementujte funkci namísto metody. Zvažte možnost spustit název metody s `Set` a sledujte, co byste měli pojmenovat vlastnost. Například <xref:System.AppDomain> má metodu nazvanou `SetCachePath` místo toho, aby byla vlastnost pouze set s názvem `CachePath`.  
  
 **✓ DO** zadejte rozumný výchozí hodnoty pro všechny vlastnosti, zajistíte, že výchozí hodnoty nezpůsobovalo neustálé bezpečnostní riziko nebo terribly neefektivní kód.  
  
 **✓ DO** povolit vlastnosti nastavit v libovolném pořadí, i když to vede k dočasné neplatný stav objektu.  
  
 Je běžné, že dvě nebo více vlastností bude možné vzájemně souviset s bodem, kde některé hodnoty jedné vlastnosti mohou být neplatné vzhledem k hodnotám jiných vlastností stejného objektu. V takových případech by měly být výjimky, které jsou výsledkem neplatného stavu, odloženy, dokud se tyto vlastnosti nepoužívají společně s objektem.  
  
 **✓ DO** zachovat předchozí hodnotu, pokud metoda setter vlastnosti vyvolá výjimku.  
  
 **X AVOID** vyvolání výjimky z metody vlastnost getter.  
  
 Metody getter vlastnosti by měly být jednoduché operace a neměly by obsahovat žádné předběžné podmínky. Pokud getter může vyvolat výjimku, měla by být pravděpodobně přepracována jako metoda. Všimněte si, že toto pravidlo se nevztahuje na indexery, kde očekáváme výjimky v důsledku ověřování argumentů.  
  
### <a name="indexed-property-design"></a>Návrh indexovaných vlastností  
 Indexovaná vlastnost je speciální vlastnost, která může mít parametry a může být volána se speciální syntaxí podobnou indexování pole.  
  
 Indexované vlastnosti se běžně označují jako indexery. Indexery by měly být používány pouze v rozhraních API, která poskytují přístup k položkám v logické kolekci. Například řetězec je kolekce znaků a indexer na <xref:System.String?displayProperty=nameWithType> byl přidán pro přístup ke svým znakům.  
  
 **✓ CONSIDER** použití indexery pro poskytnutí přístupu k datům uloženým v interní pole.  
  
 **✓ CONSIDER** poskytuje indexery na typy reprezentující kolekce položek.  
  
 **X AVOID** použití indexovaných vlastností s více než jeden parametr.  
  
 Pokud návrh vyžaduje více parametrů, převezměte v úvahu, zda vlastnost ve skutečnosti představuje přistupující objekt k logické kolekci. Pokud ne, použijte místo toho metody. Zvažte možnost spustit název metody pomocí `Get` nebo `Set`.  
  
 **X AVOID** indexery s typy parametrů jinak než <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, nebo výčet.  
  
 Pokud návrh vyžaduje jiné typy parametrů, silně znovu Vyhodnoťte, jestli rozhraní API skutečně představuje přistupující objekt k logické kolekci. Pokud tomu tak není, použijte metodu. Zvažte možnost spustit název metody pomocí `Get` nebo `Set`.  
  
 **✓ DO** použijte název `Item` pro indexovaných vlastností, pokud je samozřejmě lepší název (například najdete v článku <xref:System.String.Chars%2A> vlastnost na `System.String`).  
  
 V C#nástroji jsou indexery ve výchozím nastavení pojmenované položky. K přizpůsobení tohoto názvu lze použít <xref:System.Runtime.CompilerServices.IndexerNameAttribute>.  
  
 **X DO NOT** zadejte indexer a metody, které jsou sémanticky ekvivalentní.  
  
 **X DO NOT** zadat více než jednu řadu přetížené indexery jednomu typu.  
  
 Toto je vynutil C# kompilátorem.  
  
 **X DO NOT** nevýchozí použití indexovaných vlastností.  
  
 Toto je vynutil C# kompilátorem.  
  
### <a name="property-change-notification-events"></a>Události upozornění na změnu vlastnosti  
 Někdy je užitečné poskytnout událost upozorňující uživatele na změny v hodnotě vlastnosti. Například `System.Windows.Forms.Control` vyvolává událost `TextChanged` po změně hodnoty vlastnosti `Text`.  
  
 **✓ CONSIDER** vyvolání změnit události oznámení při změně hodnoty vlastností v vysoké úrovně rozhraní API (obvykle návrháře komponenty).  
  
 Pokud je dobrým scénářem, že uživatel ví, kdy se změní vlastnost objektu, měl by objekt vyvolat událost upozornění na změnu pro vlastnost.  
  
 Nepředpokládá se však, že bude nutné zvýšit nároky na vyvolání takových událostí pro rozhraní API nižší úrovně, jako jsou základní typy nebo kolekce. <xref:System.Collections.Generic.List%601> například nevyvolává takové události, když se do seznamu přidá nová položka a změní se vlastnost `Count`.  
  
 **✓ CONSIDER** vyvolání události oznámení při změně hodnoty vlastnosti prostřednictvím externí vynutí změn.  
  
 Pokud se hodnota vlastnosti mění přes některé externí síly (způsobem, který je jiný než voláním metod objektu), vyvolávají události upozorňující na vývojáře, že se hodnota mění a změnila. Dobrým příkladem je vlastnost `Text` ovládacího prvku textového pole. Když uživatel zadá text do `TextBox`, hodnota vlastnosti se automaticky změní.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
