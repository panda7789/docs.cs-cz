---
title: Pokyny pro kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571ebb2fdd2bcdfd8be1f0087d096e01f18790a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272942"
---
# <a name="guidelines-for-collections"></a>Pokyny pro kolekce
Jakýkoli typ určený konkrétně pro manipulaci s skupinu objektů, které mají některé běžné charakteristiky lze považovat za kolekce. Je téměř vždy vhodné pro tyto typy implementace <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>, takže se v této části považujeme pouze typy implementace jeden nebo oba z těchto rozhraní být kolekce.  
  
 **X DO NOT** slabě typovaná kolekce použít veřejné rozhraní API.  
  
 Typ položky přesně, nikoli jakákoliv z jeho základních typů (platí jenom pro veřejné členy kolekce) by měl být typu všechny návratové hodnoty a parametry představující kolekci položek.  
  
 **X DO NOT** použít <xref:System.Collections.ArrayList> nebo <xref:System.Collections.Generic.List%601> veřejné rozhraní API.  
  
 Tyto typy jsou datové struktury, která se používá v interní implementace, nejsou ve veřejných rozhraní API. `List<T>` je optimalizované pro výkon a výkon za cenu čistotu rozhraní API a flexibilitu. Například, pokud vrátíte `List<T>`, nikdy nebudete moct dostávat oznámení, když kód klienta upraví kolekci. Navíc `List<T>` poskytuje mnoho členů, jako například <xref:System.Collections.Generic.List%601.BinarySearch%2A>, které nejsou užitečné nebo použít v mnoha scénářích. Následující dvě části popisují typy (abstrakce) určený speciálně pro použití ve veřejných rozhraní API.  
  
 **X DO NOT** použít `Hashtable` nebo `Dictionary<TKey,TValue>` veřejné rozhraní API.  
  
 Tyto typy jsou datové struktury, která se používá v interní implementaci. Veřejné rozhraní API používejte <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, nebo vlastní typ implementující jedno nebo obě rozhraní.  
  
 **X DO NOT** použít <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, nebo jakýkoli jiný typ, který implementuje kterékoli z těchto rozhraní, s výjimkou jako návratový typ `GetEnumerator` metoda.  
  
 Typy jiné než vrácení enumerátory z metody `GetEnumerator` nelze použít s `foreach` příkazu.  
  
 **X DO NOT** implementovat obě `IEnumerator<T>` a `IEnumerable<T>` na stejného typu. Totéž platí i pro neobecné rozhraní `IEnumerator` a `IEnumerable`.  
  
## <a name="collection-parameters"></a>Kolekce parametrů  
 **✓ DO** typ specializuje nejmenší možné použít jako typ parametru. Většina členy trvá kolekcí, jak používat parametry `IEnumerable<T>` rozhraní.  
  
 **X AVOID** pomocí <xref:System.Collections.Generic.ICollection%601> nebo <xref:System.Collections.ICollection> jako parametr pouze pro přístup `Count` vlastnost.  
  
 Místo toho zvažte použití `IEnumerable<T>` nebo `IEnumerable` a dynamicky kontroluje, zda daný objekt implementuje `ICollection<T>` nebo `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Kolekce vlastností a návratové hodnoty  
 **X DO NOT** zadejte vlastnosti nastavit kolekce.  
  
 Uživatelům můžete nahradit obsah kolekce nejprve vymazáním kolekce a následným přidáním nového obsahu. Pokud nahrazování celé kolekce je běžný scénář, zvažte poskytnutí `AddRange` metody v kolekci.  
  
 **✓ DO** použít `Collection<T>` nebo podtřídou třídy `Collection<T>` pro vlastnosti nebo return hodnoty představující kolekce pro čtení a zápis.  
  
 Pokud `Collection<T>` nesplňuje některé požadavky (například kolekce nesmí implementovat <xref:System.Collections.IList>), použijte vlastní kolekce implementací `IEnumerable<T>`, `ICollection<T>`, nebo <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** použít <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podtřídou třídy `ReadOnlyCollection<T>`, nebo ve výjimečných případech `IEnumerable<T>` pro vlastnosti nebo return hodnoty představující kolekce jen pro čtení.  
  
 Obecně platí, dáváte přednost `ReadOnlyCollection<T>`. Pokud nesplňuje některé požadavky (například kolekce nesmí implementovat `IList`), použijte vlastní kolekce implementací `IEnumerable<T>`, `ICollection<T>`, nebo `IList<T>`. Pokud se rozhodnete implementovat vlastní kolekce jen pro čtení, implementovat `ICollection<T>.IsReadOnly` vrátit `true`.  
  
 V případech, kdy jste si jisti, že je jediným případem se někdy budete chtít podporu dopředné iterace, můžete jednoduše použít `IEnumerable<T>`.  
  
 **✓ CONSIDER** pomocí podtřídy obecné základní kolekce místo použití kolekce přímo.  
  
 To umožňuje lepší názvu a pro přidávání členů pomocné rutiny, které nejsou k dispozici u typů kolekce základní. To platí zejména pro rozhraní API vysoké úrovně.  
  
 **✓ CONSIDER** vrácení podtřídou třídy `Collection<T>` nebo `ReadOnlyCollection<T>` velmi běžně používaných metod a vlastností.  
  
 To znamená, že umožní přidají metody helper nebo změňte implementaci kolekce v budoucnu.  
  
 **✓ CONSIDER** pomocí kolekci s klíčem, je-li mít jedinečné klíče položky uložené v kolekci (názvy, ID, atd.). Kolekce s klíči jsou kolekce, které můžete indexovat pomocí celé číslo a klíč a jsou obvykle implementovány pomocí dědění z `KeyedCollection<TKey,TItem>`.  
  
 Kolekce s klíči obvykle mají větší pracovníkům paměti by se neměl používat, pokud zatížení paměti převažuje získané výhody s klíči.  
  
 **X DO NOT** vrátit hodnotu null. hodnoty z vlastnosti kolekce nebo z metody, které vrací kolekce. Místo toho vrátí prázdnou kolekci nebo prázdné pole.  
  
 Obecně platí, že by měla být hodnota null a prázdné kolekce (0 položek) nebo pole chovají stejně.  
  
### <a name="snapshots-versus-live-collections"></a>Snímky a živé kolekce  
 Kolekce představující stavu v určitém okamžiku v čase se kterým se říká kolekce snímku. Kolekce obsahující řádků vrácená z dotazu databáze by například snímku. Kolekce, vždycky představujících aktuální stav, se nazývají živé kolekce. Například kolekce `ComboBox` položky je kolekce za provozu.  
  
 **X DO NOT** vracejí snímek kolekce z vlastností. Vlastnosti by měla vrátit živé kolekce.  
  
 Gettery vlastností by měl být velmi jednoduché operace. Vrácení snímku vyžaduje vytvoření kopie vnitřní kolekce v operaci O(n).  
  
 **✓ DO** použít kolekci snímku nebo živé `IEnumerable<T>` (nebo jeho dílčí) představují kolekce, které jsou volatile (tj, který můžete změnit bez explicitně úpravy kolekce).  
  
 Všechny kolekce představující sdíleného prostředku (např. soubory v adresáři) jsou obecně volatile. Tato kolekce jsou velmi obtížné či nemožné implementovat jako živé kolekcí, není-li implementace jednoduše dopředné enumerátor.  
  
## <a name="choosing-between-arrays-and-collections"></a>Volba mezi pole a kolekce  
 **✓ DO** upřednostnit kolekce přes pole.  
  
 Kolekce poskytují větší kontrolu nad obsah, můžete v průběhu času vyvíjejí a jsou lépe použitelná. Kromě toho pomocí pole pro scénáře, jen pro čtení se nedoporučují, protože je odrazovat vysokými náklady na klonování pole. Použitelnost studií vyplývá, že někteří vývojáři klidem více pomocí rozhraní API založená na kolekci.  
  
 Ale pokud vyvíjíte rozhraní API nízké úrovně, může být vhodnější použít pole pro čtení i zápis scénáře. Pole mají nižší paměťové nároky, což pomáhá snižovat pracovní sady, a přístup k prvkům v poli je rychlejší, protože je optimalizovaný modul runtime.  
  
 **✓ CONSIDER** použití polí v nižší úrovně rozhraní API minimalizovat využití paměti a maximalizovat výkon.  
  
 **✓ DO** pomocí bajtových polí místo kolekcí bajtů.  
  
 **X DO NOT** použít pole pro vlastnosti, pokud by pak bylo vlastnost vrací nové pole (například kopii interní pole) pokaždé, když je volána metoda getter vlastnosti.  
  
## <a name="implementing-custom-collections"></a>Implementace vlastních kolekcí  
 **✓ CONSIDER** dědění z `Collection<T>`, `ReadOnlyCollection<T>`, nebo `KeyedCollection<TKey,TItem>` při návrhu nové kolekce.  
  
 **✓ DO** implementovat `IEnumerable<T>` při návrhu nové kolekce. Zvažte implementaci `ICollection<T>` nebo dokonce `IList<T>` to bude dávat smysl.  
  
 Při implementaci těchto vlastní kolekce, mají tvar API stanovené `Collection<T>` a `ReadOnlyCollection<T>` co nejpřesněji. To znamená explicitně implementovat stejné členy, pojmenujte parametry, jako jsou tyto dvě kolekce název je a tak dále.  
  
 **✓ CONSIDER** implementace rozhraní neobecné kolekce (`IList` a `ICollection`) Pokud kolekce se často předá rozhraní API trvá tato rozhraní jako vstup.  
  
 **X AVOID** implementace rozhraní pro kolekce na typy s komplexní rozhraní API koncept kolekce, které nejsou.  
  
 **X DO NOT** dědit z neobecného základní kolekcí, jako `CollectionBase`. Použití `Collection<T>`, `ReadOnlyCollection<T>`, a `KeyedCollection<TKey,TItem>` místo.  
  
### <a name="naming-custom-collections"></a>Názvy vlastních kolekcí  
 Kolekce (typy, které implementují `IEnumerable`) jsou vytvořeny hlavně pro dva důvody: (1) Chcete-li vytvořit novou strukturu dat s operacemi specifický pro strukturu a často odlišných výkonových existujícím datovým strukturám charakteristik (například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) a (2) Chcete-li vytvořit kolekci specializované pro uchování konkrétní sady položek (například <xref:System.Collections.Specialized.StringCollection>). Datové struktury jsou nejčastěji používají v interní implementaci aplikací a knihoven. Specializované kolekce se hlavně zveřejněné v rozhraní API (jako typy vlastností a parametrů).  
  
 **✓ DO** používat příponu "Slovník" v názvech abstrakce implementace `IDictionary` nebo `IDictionary<TKey,TValue>`.  
  
 **✓ DO** používat příponu "Kolekce" v názvech typů implementace `IEnumerable` (nebo některého z jejich potomků) a představuje seznam položek.  
  
 **✓ DO** použijte název struktura příslušná data pro vlastní datové struktury.  
  
 **X AVOID** pomocí libovolné přípony zdání konkrétní implementace, jako je například "LinkedList" nebo "Zatřiďovací tabulky," v názvech abstrakce kolekce.  
  
 **✓ CONSIDER** prefixu názvy kolekci s názvem typu položky. Například kolekce ukládání položek typu `Address` (implementace `IEnumerable<Address>`) by měly být pojmenovány `AddressCollection`. Pokud typ položky je rozhraní, předponu "I" položky lze vynechat typu. Díky tomu se kolekce <xref:System.IDisposable> položky lze volat `DisposableCollection`.  
  
 **✓ CONSIDER** pomocí předpony "Jen pro čtení" v názvech kolekcí jen pro čtení, pokud odpovídající kolekci lze zapisovat, mohou být přidány nebo již existuje v rámci.  
  
 Například by měla být volána jen pro čtení kolekce řetězců `ReadOnlyStringCollection`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
