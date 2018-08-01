---
title: Pokyny pro kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d73ff726e9ddfe1ec1d16dd020f53445f984fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578856"
---
# <a name="guidelines-for-collections"></a>Pokyny pro kolekce
Jakýkoli typ navrženo konkrétně k manipulaci s pro skupinu objektů, že některé běžné vlastnosti lze považovat za kolekce. Je téměř vždy vhodné pro tyto typy pro implementaci <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>, takže v této části jsme pouze na nabídnuté typy implementace jednoho nebo obou těchto rozhraní jako kolekce.  
  
 **X DO NOT** slabě typovaná kolekce použít veřejné rozhraní API.  
  
 Typ všechny návratové hodnoty a parametry položky kolekce představující musí být typ položky přesně, nikoli jakákoliv z jeho základních typů (to se týká pouze veřejné členy kolekce).  
  
 **X DO NOT** použít <xref:System.Collections.ArrayList> nebo <xref:System.Collections.Generic.List%601> veřejné rozhraní API.  
  
 Tyto typy jsou datové struktury, které jsou určeny k použití v interní implementaci není v veřejná rozhraní API. `List<T>` je optimalizován pro výkon a výkon za cenu čistotu rozhraní API a flexibility. Například, pokud vrátíte `List<T>`, někdy nebudete moci přijímat upozornění, když kód klienta upraví kolekce. Navíc `List<T>` zpřístupní mnoho členů, jako například <xref:System.Collections.Generic.List%601.BinarySearch%2A>, které nejsou užitečné nebo v mnoha scénářích není platná. Následující dvě části popisují typy (abstrakce) určený speciálně pro použití v veřejná rozhraní API.  
  
 **X DO NOT** použít `Hashtable` nebo `Dictionary<TKey,TValue>` veřejné rozhraní API.  
  
 Tyto typy jsou určeny k použití v interní implementaci datové struktury. Veřejná rozhraní API by měl používat <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, nebo vlastní typ implementace jedno nebo obě rozhraní.  
  
 **X DO NOT** použít <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, nebo jakýkoli jiný typ, který implementuje kterékoli z těchto rozhraní, s výjimkou jako návratový typ `GetEnumerator` metoda.  
  
 Typy vrácení výčty z metody jiné než `GetEnumerator` nelze použít s `foreach` příkaz.  
  
 **X DO NOT** implementovat obě `IEnumerator<T>` a `IEnumerable<T>` na stejného typu. Totéž platí i pro rozhraní neobecné `IEnumerator` a `IEnumerable`.  
  
## <a name="collection-parameters"></a>Kolekce parametrů  
 **✓ DO** typ specializuje nejmenší možné použít jako typ parametru. Většina členy trvá kolekce jako parametry použijte `IEnumerable<T>` rozhraní.  
  
 **X AVOID** pomocí <xref:System.Collections.Generic.ICollection%601> nebo <xref:System.Collections.ICollection> jako parametr pouze pro přístup `Count` vlastnost.  
  
 Místo toho zvažte použití `IEnumerable<T>` nebo `IEnumerable` a dynamicky kontrola, zda objekt implementuje `ICollection<T>` nebo `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Kolekce vlastností a návratové hodnoty  
 **X DO NOT** zadejte vlastnosti nastavit kolekce.  
  
 Uživatele můžete nahradit obsah kolekce nejprve vymazání kolekce a potom přidat nový obsah. Pokud nahrazení celé kolekce je běžný scénář, zvažte možnost poskytování `AddRange` metoda v kolekci.  
  
 **✓ DO** použít `Collection<T>` nebo podtřídou třídy `Collection<T>` pro vlastnosti nebo return hodnoty představující kolekce pro čtení a zápis.  
  
 Pokud `Collection<T>` nesplňuje některé požadavky (například nesmí kolekce implementovat <xref:System.Collections.IList>), používat vlastní kolekce implementací `IEnumerable<T>`, `ICollection<T>`, nebo <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** použít <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podtřídou třídy `ReadOnlyCollection<T>`, nebo ve výjimečných případech `IEnumerable<T>` pro vlastnosti nebo return hodnoty představující kolekce jen pro čtení.  
  
 Obecně platí, raději `ReadOnlyCollection<T>`. Pokud nesplňuje požadavek na některé (například nesmí kolekce implementovat `IList`), používat vlastní kolekce implementací `IEnumerable<T>`, `ICollection<T>`, nebo `IList<T>`. Pokud budete implementovat vlastní kolekce jen pro čtení, implementujte `ICollection<T>.IsReadOnly` vrátit `true`.  
  
 V případech, kdy jste si jisti, že jediný scénář, se někdy budete chtít podporu je dopředné iterace, můžete jednoduše použít `IEnumerable<T>`.  
  
 **✓ CONSIDER** pomocí podtřídy obecné základní kolekce místo použití kolekce přímo.  
  
 To umožňuje lepší názvu a pro přidávání členů pomocné rutiny, které se nenacházejí na typy základní kolekcí. Používá se především pro vysoké úrovně rozhraní API.  
  
 **✓ CONSIDER** vrácení podtřídou třídy `Collection<T>` nebo `ReadOnlyCollection<T>` velmi běžně používaných metod a vlastností.  
  
 To znamená, že vám umožní přidat pomocné metody nebo změňte implementaci kolekce v budoucnu.  
  
 **✓ CONSIDER** pomocí kolekci s klíčem, je-li mít jedinečné klíče položky uložené v kolekci (názvy, ID, atd.). Kolekce s klíči jsou kolekce, které může indexovat pomocí celé číslo a klíč a jsou obvykle implementované dědění z `KeyedCollection<TKey,TItem>`.  
  
 Kolekce s klíči obvykle mají větší paměti pracovníkům a by se neměla používat, pokud nároky na paměť převáží o výhodách klíče.  
  
 **X DO NOT** vrátit hodnotu null. hodnoty z vlastnosti kolekce nebo z metody, které vrací kolekce. Místo toho vrátí prázdnou kolekci nebo prázdné pole.  
  
 Obecně platí, že by měla být hodnota null a prázdný kolekcí (0 položek) nebo pole chovají stejně.  
  
### <a name="snapshots-versus-live-collections"></a>Snímky a za provozu kolekce  
 Kolekce představující stav v určitém okamžiku v čase se označují jako snímek kolekce. Kolekce obsahující řádků vrácená z dotazu databáze by být například snímek. Kolekce, které vždy představují aktuální stav, se nazývají za provozu kolekce. Například kolekce `ComboBox` položky je soubor za provozu.  
  
 **X DO NOT** vracejí snímek kolekce z vlastností. Vlastnosti by měl vrátit za provozu kolekce.  
  
 Mechanismy získání vlastnost by měla být velmi jednoduché operace. Vrácení snímek vyžaduje vytvoření kopie vnitřní kolekce v O(n) operace.  
  
 **✓ DO** použít kolekci snímku nebo živé `IEnumerable<T>` (nebo jeho dílčí) představují kolekce, které jsou volatile (tj, který můžete změnit bez explicitně úpravy kolekce).  
  
 Všechny kolekce představující sdíleného prostředku (například soubory v adresáři) jsou obecně volatile. Tyto kolekce jsou velmi obtížné nebo dokonce znemožňují implementovat jako kolekce za provozu, pokud jeho implementace je jednoduše dopředné enumerátor.  
  
## <a name="choosing-between-arrays-and-collections"></a>Volba mezi pole a kolekce  
 **✓ DO** upřednostnit kolekce přes pole.  
  
 Kolekce poskytuje větší kontrolu nad obsah, můžete v průběhu času vyvíjejí a jsou více použitelné. Kromě toho použití polí pro scénáře jen pro čtení se nedoporučuje. protože je cenově náklady klonování pole. Použitelnost studií vyplývá, že někteří vývojáři bez obav více pomocí rozhraní API založené na kolekcích.  
  
 Ale pokud vyvíjíte nízké úrovně rozhraní API, může být vhodnější použít pole pro scénáře pro čtení a zápis. Pole mít menší nároky paměti, která pomáhá snižovat pracovní sady, a přístup k prvků v poli je rychlejší, protože je optimalizována modulem runtime.  
  
 **✓ CONSIDER** použití polí v nižší úrovně rozhraní API minimalizovat využití paměti a maximalizovat výkon.  
  
 **✓ DO** pomocí bajtových polí místo kolekcí bajtů.  
  
 **X DO NOT** použít pole pro vlastnosti, pokud by pak bylo vlastnost vrací nové pole (například kopii interní pole) pokaždé, když je volána metoda getter vlastnosti.  
  
## <a name="implementing-custom-collections"></a>Implementace vlastních kolekcí  
 **✓ CONSIDER** dědění z `Collection<T>`, `ReadOnlyCollection<T>`, nebo `KeyedCollection<TKey,TItem>` při návrhu nové kolekce.  
  
 **✓ DO** implementovat `IEnumerable<T>` při návrhu nové kolekce. Zvažte implementaci `ICollection<T>` nebo i `IList<T>` kde má smysl.  
  
 Při implementaci těchto vlastní kolekce, postupujte podle vzoru rozhraní API vymezenému `Collection<T>` a `ReadOnlyCollection<T>` co nejblíže. To znamená implementovat stejné členy explicitně, název parametry, jako jsou tyto dvě kolekce název je a tak dále.  
  
 **✓ CONSIDER** implementace rozhraní neobecné kolekce (`IList` a `ICollection`) Pokud kolekce se často předá rozhraní API trvá tato rozhraní jako vstup.  
  
 **X AVOID** implementace rozhraní pro kolekce na typy s komplexní rozhraní API koncept kolekce, které nejsou.  
  
 **X DO NOT** dědit z neobecného základní kolekcí, jako `CollectionBase`. Použití `Collection<T>`, `ReadOnlyCollection<T>`, a `KeyedCollection<TKey,TItem>` místo.  
  
### <a name="naming-custom-collections"></a>Názvy vlastních kolekcí  
 Kolekce (typy, které implementují `IEnumerable`) jsou vytvořeny především dvou důvodů: (1) Chcete-li vytvořit novou strukturu dat s operacích specifických struktura a často různé výkonové charakteristiky než existující datové struktury (například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) a (2) Chcete-li vytvořit kolekci specializované pro uložení konkrétní sadu položek (například <xref:System.Collections.Specialized.StringCollection>). Datové struktury se nejčastěji používají k implementaci interní aplikace a knihovny. Specializované kolekce jsou především mají být exponovány v rozhraní API (jako vlastnost a parametr typy).  
  
 **✓ DO** používat příponu "Slovník" v názvech abstrakce implementace `IDictionary` nebo `IDictionary<TKey,TValue>`.  
  
 **✓ DO** používat příponu "Kolekce" v názvech typů implementace `IEnumerable` (nebo některého z jejich potomků) a představuje seznam položek.  
  
 **✓ DO** použijte název struktura příslušná data pro vlastní datové struktury.  
  
 **X AVOID** pomocí libovolné přípony zdání konkrétní implementace, jako je například "LinkedList" nebo "Zatřiďovací tabulky," v názvech abstrakce kolekce.  
  
 **✓ CONSIDER** prefixu názvy kolekci s názvem typu položky. Například kolekce ukládání položky typu `Address` (implementace `IEnumerable<Address>`) by měla mít název `AddressCollection`. Pokud typ položky je rozhraní, "I" předpony položky lze vynechat typu. Proto kolekci <xref:System.IDisposable> položky lze volat `DisposableCollection`.  
  
 **✓ CONSIDER** pomocí předpony "Jen pro čtení" v názvech kolekcí jen pro čtení, pokud odpovídající kolekci lze zapisovat, mohou být přidány nebo již existuje v rámci.  
  
 Například by měla být volána jen pro čtení kolekci řetězců `ReadOnlyStringCollection`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
