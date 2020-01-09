---
title: Pokyny pro kolekce
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 231d8b04c11f19c4440e184533e1eeaded72b70b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709319"
---
# <a name="guidelines-for-collections"></a>Pokyny pro kolekce
Jakýkoli typ navržený specificky pro manipulaci se skupinou objektů s některými běžnými charakteristikami lze považovat za kolekci. Je téměř vždy vhodný pro tyto typy implementovat <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>, takže v této části doporučujeme pouze typy implementující jedno nebo obě tato rozhraní do kolekcí.  
  
 **X DO NOT** slabě typovaná kolekce použít veřejné rozhraní API.  
  
 Typ všech vrácených hodnot a parametrů představujících položky kolekce by měl být přesný typ položky, nikoli žádný z jeho základních typů (platí pouze pro veřejné členy kolekce).  
  
 **X DO NOT** použít <xref:System.Collections.ArrayList> nebo <xref:System.Collections.Generic.List%601> veřejné rozhraní API.  
  
 Tyto typy jsou datové struktury navržené pro použití v interní implementaci, nikoli ve veřejných rozhraních API. `List<T>` je optimalizováno pro výkon a výkon v ceně výkonu rozhraní API a flexibility. Pokud například vrátíte `List<T>`, nebudete někdy moci dostávat oznámení, když kód klienta upraví kolekci. `List<T>` také zveřejňuje mnoho členů, jako je například <xref:System.Collections.Generic.List%601.BinarySearch%2A>, které nejsou užitečné nebo použitelné v mnoha scénářích. Následující dvě části popisují typy (abstrakce) navržené speciálně pro použití ve veřejných rozhraních API.  
  
 **X DO NOT** použít `Hashtable` nebo `Dictionary<TKey,TValue>` veřejné rozhraní API.  
  
 Tyto typy jsou datové struktury navržené pro použití při interní implementaci. Veřejná rozhraní API by měla používat <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`nebo vlastní typ implementující jedno nebo obě rozhraní.  
  
 **X DO NOT** použít <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, nebo jakýkoli jiný typ, který implementuje kterékoli z těchto rozhraní, s výjimkou jako návratový typ `GetEnumerator` metoda.  
  
 Typy, které vracejí enumerátory z jiných metod než `GetEnumerator`, nelze použít spolu s příkazem `foreach`.  
  
 **X DO NOT** implementovat obě `IEnumerator<T>` a `IEnumerable<T>` na stejného typu. Totéž platí pro neobecná rozhraní `IEnumerator` a `IEnumerable`.  
  
## <a name="collection-parameters"></a>Parametry kolekce  
 **✓ DO** typ specializuje nejmenší možné použít jako typ parametru. Většina členů, kteří přibírají kolekce jako parametry, používá rozhraní `IEnumerable<T>`.  
  
 **X AVOID** pomocí <xref:System.Collections.Generic.ICollection%601> nebo <xref:System.Collections.ICollection> jako parametr pouze pro přístup `Count` vlastnost.  
  
 Místo toho zvažte použití `IEnumerable<T>` nebo `IEnumerable` a dynamicky kontroluje, zda objekt implementuje `ICollection<T>` nebo `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Vlastnosti kolekce a návratové hodnoty  
 **X DO NOT** zadejte vlastnosti nastavit kolekce.  
  
 Uživatelé mohou obsah kolekce nahradit tak, že nejprve vymaže kolekci a následně přidají nový obsah. Pokud je nahrazení celé kolekce běžným scénářem, zvažte poskytnutí `AddRange` metody v kolekci.  
  
 **✓ DO** použít `Collection<T>` nebo podtřídou třídy `Collection<T>` pro vlastnosti nebo return hodnoty představující kolekce pro čtení a zápis.  
  
 Pokud `Collection<T>` nesplňuje určitý požadavek (například kolekce nesmí implementovat <xref:System.Collections.IList>), použijte vlastní kolekci implementací `IEnumerable<T>`, `ICollection<T>`nebo <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** použít <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podtřídou třídy `ReadOnlyCollection<T>`, nebo ve výjimečných případech `IEnumerable<T>` pro vlastnosti nebo return hodnoty představující kolekce jen pro čtení.  
  
 Obecně je vhodnější `ReadOnlyCollection<T>`. Pokud nesplňuje určitý požadavek (například shromažďování nesmí implementovat `IList`), použijte vlastní kolekci implementací `IEnumerable<T>`, `ICollection<T>`nebo `IList<T>`. Pokud implementujete vlastní kolekci jen pro čtení, implementujte `ICollection<T>.IsReadOnly` pro návrat `true`.  
  
 V případech, kdy jste si jisti, že jediný scénář, který budete chtít někdy podporovat, je iterace jenom pro přeposílání, můžete jednoduše použít `IEnumerable<T>`.  
  
 **✓ CONSIDER** pomocí podtřídy obecné základní kolekce místo použití kolekce přímo.  
  
 To umožňuje lepší název a přidání pomocných členů, kteří nejsou přítomni v základních typech kolekce. To se hodí hlavně pro rozhraní API vysoké úrovně.  
  
 **✓ CONSIDER** vrácení podtřídou třídy `Collection<T>` nebo `ReadOnlyCollection<T>` velmi běžně používaných metod a vlastností.  
  
 To umožní přidat pomocné metody nebo změnit implementaci kolekce v budoucnu.  
  
 **✓ CONSIDER** pomocí kolekci s klíčem, je-li mít jedinečné klíče položky uložené v kolekci (názvy, ID, atd.). Kolekce s klíčem jsou kolekce, které mohou být indexovány pomocí celého čísla i klíče a jsou obvykle implementovány děděním z `KeyedCollection<TKey,TItem>`.  
  
 Kolekce s klíčem mají obvykle větší nároky na paměť a neměly by se používat v případě, že režie paměti převyšuje výhody použití klíčů.  
  
 **X DO NOT** vrátit hodnotu null. hodnoty z vlastnosti kolekce nebo z metody, které vrací kolekce. Místo toho se vrátí prázdná kolekce nebo prázdné pole.  
  
 Obecným pravidlem je, že kolekce a pole s hodnotou null a prázdné (0 položka) by měly být ošetřeny stejným způsobem.  
  
### <a name="snapshots-versus-live-collections"></a>Snímky versus živé kolekce  
 Kolekce představující stav v určitém okamžiku se nazývají kolekce snímků. Například kolekce obsahující řádky vrácené z databázového dotazu by byla snímkem. Kolekce, které vždy představují aktuální stav, se nazývají živé kolekce. Například kolekce `ComboBox`ch položek je živá kolekce.  
  
 **X DO NOT** vracejí snímek kolekce z vlastností. Vlastnosti by měly vracet živé kolekce.  
  
 Metody getter vlastnosti by měly být velmi prosté operace. Vrácení snímku vyžaduje vytvoření kopie interní kolekce v operaci O (n).  
  
 **✓ DO** použít kolekci snímku nebo živé `IEnumerable<T>` (nebo jeho dílčí) představují kolekce, které jsou volatile (tj, který můžete změnit bez explicitně úpravy kolekce).  
  
 Obecně platí, že všechny kolekce, které představují sdílený prostředek (například soubory v adresáři), jsou nestálé. Tyto kolekce jsou velmi obtížné nebo nemožné implementovat jako živé kolekce, pokud implementace nestačí jenom pro dopředné enumerátory.  
  
## <a name="choosing-between-arrays-and-collections"></a>Výběr mezi poli a kolekcemi  
 **✓ DO** upřednostnit kolekce přes pole.  
  
 Kolekce poskytují větší kontrolu nad obsahem, můžou se v průběhu času vyvíjet a jsou užitečnější. Kromě toho se nedoporučuje používat pole pro scénáře jen pro čtení, protože náklady na klonování pole jsou zakazují. Studie použitelnosti ukázaly, že někteří vývojáři se lépe cítí pomocí rozhraní API založených na kolekcích.  
  
 Pokud ale vyvíjíte rozhraní API nízké úrovně, může být lepší použít pole pro scénáře pro čtení i zápis. Pole mají menší nároky na paměť, což pomáhá snižovat pracovní sadu a přístup k prvkům v poli je rychlejší, protože je optimalizován modulem runtime.  
  
 **✓ CONSIDER** použití polí v nižší úrovně rozhraní API minimalizovat využití paměti a maximalizovat výkon.  
  
 **✓ DO** pomocí bajtových polí místo kolekcí bajtů.  
  
 **X DO NOT** použít pole pro vlastnosti, pokud by pak bylo vlastnost vrací nové pole (například kopii interní pole) pokaždé, když je volána metoda getter vlastnosti.  
  
## <a name="implementing-custom-collections"></a>Implementace vlastních kolekcí  
 **✓ CONSIDER** dědění z `Collection<T>`, `ReadOnlyCollection<T>`, nebo `KeyedCollection<TKey,TItem>` při návrhu nové kolekce.  
  
 **✓ DO** implementovat `IEnumerable<T>` při návrhu nové kolekce. Zvažte implementaci `ICollection<T>` nebo dokonce `IList<T>`, kde to dává smysl.  
  
 Při implementaci takové vlastní kolekce se řiďte vzorem rozhraní API vytvořeným `Collection<T>` a `ReadOnlyCollection<T>` co nejpřesněji. To znamená, že je třeba implementovat stejné členy explicitně, pojmenovat parametry jako tyto dvě kolekce a tak dále.  
  
 **✓ CONSIDER** implementace rozhraní neobecné kolekce (`IList` a `ICollection`) Pokud kolekce se často předá rozhraní API trvá tato rozhraní jako vstup.  
  
 **X AVOID** implementace rozhraní pro kolekce na typy s komplexní rozhraní API koncept kolekce, které nejsou.  
  
 **X DO NOT** dědit z neobecného základní kolekcí, jako `CollectionBase`. Místo toho použijte `Collection<T>`, `ReadOnlyCollection<T>`a `KeyedCollection<TKey,TItem>`.  
  
### <a name="naming-custom-collections"></a>Pojmenovávání vlastních kolekcí  
 Kolekce (typy, které implementují `IEnumerable`) se vytvářejí hlavně ze dvou důvodů: (1) pro vytvoření nové struktury dat s operacemi specifickými pro strukturu a často různé charakteristiky výkonu než stávající datové struktury (např. <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) a (2) pro vytvoření specializované kolekce pro uchovávání konkrétní sady položek (například <xref:System.Collections.Specialized.StringCollection>). V interní implementaci aplikací a knihoven se často používají datové struktury. Specializované kolekce jsou převážně vystaveny v rozhraních API (jako typy vlastností a parametrů).  
  
 **✓ DO** používat příponu "Slovník" v názvech abstrakce implementace `IDictionary` nebo `IDictionary<TKey,TValue>`.  
  
 **✓ DO** používat příponu "Kolekce" v názvech typů implementace `IEnumerable` (nebo některého z jejich potomků) a představuje seznam položek.  
  
 **✓ DO** použijte název struktura příslušná data pro vlastní datové struktury.  
  
 **X AVOID** pomocí libovolné přípony zdání konkrétní implementace, jako je například "LinkedList" nebo "Zatřiďovací tabulky," v názvech abstrakce kolekce.  
  
 **✓ CONSIDER** prefixu názvy kolekci s názvem typu položky. Například kolekce, která ukládá položky typu `Address` (implementace `IEnumerable<Address>`), by měla být pojmenována `AddressCollection`. Pokud je typ položky rozhraní, může být předpona "I" typu položky vynechána. Proto může být kolekce <xref:System.IDisposable>ch položek volána `DisposableCollection`.  
  
 **✓ CONSIDER** pomocí předpony "Jen pro čtení" v názvech kolekcí jen pro čtení, pokud odpovídající kolekci lze zapisovat, mohou být přidány nebo již existuje v rámci.  
  
 Například kolekce řetězců jen pro čtení by měla být volána `ReadOnlyStringCollection`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
