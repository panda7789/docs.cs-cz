---
title: Pokyny pro kolekce
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 50497de6569b448ab036af8a1fbf76a47565e2bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741861"
---
# <a name="guidelines-for-collections"></a>Pokyny pro kolekce
Jakýkoli typ navržený specificky pro manipulaci se skupinou objektů s některými běžnými charakteristikami lze považovat za kolekci. Je téměř vždy vhodný pro tyto typy implementovat <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>, takže v této části doporučujeme pouze typy implementující jedno nebo obě tato rozhraní do kolekcí.

 ❌ nepoužívejte ve veřejných rozhraních API slabě typované kolekce.

 Typ všech vrácených hodnot a parametrů představujících položky kolekce by měl být přesný typ položky, nikoli žádný z jeho základních typů (platí pouze pro veřejné členy kolekce).

 ve veřejných rozhraních API ❌ nepoužívat <xref:System.Collections.ArrayList> ani <xref:System.Collections.Generic.List%601>.

 Tyto typy jsou datové struktury navržené pro použití v interní implementaci, nikoli ve veřejných rozhraních API. `List<T>` je optimalizováno pro výkon a výkon v ceně výkonu rozhraní API a flexibility. Pokud například vrátíte `List<T>`, nebudete někdy moci dostávat oznámení, když kód klienta upraví kolekci. `List<T>` také zveřejňuje mnoho členů, jako je například <xref:System.Collections.Generic.List%601.BinarySearch%2A>, které nejsou užitečné nebo použitelné v mnoha scénářích. Následující dvě části popisují typy (abstrakce) navržené speciálně pro použití ve veřejných rozhraních API.

 ve veřejných rozhraních API ❌ nepoužívat `Hashtable` ani `Dictionary<TKey,TValue>`.

 Tyto typy jsou datové struktury navržené pro použití při interní implementaci. Veřejná rozhraní API by měla používat <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`nebo vlastní typ implementující jedno nebo obě rozhraní.

 ❌ nepoužívejte <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>ani jiný typ, který implementuje některá z těchto rozhraní, s výjimkou návratového typu metody `GetEnumerator`.

 Typy, které vracejí enumerátory z jiných metod než `GetEnumerator`, nelze použít spolu s příkazem `foreach`.

 ❌ neimplementuje současně `IEnumerator<T>` a `IEnumerable<T>` stejného typu. Totéž platí pro neobecná rozhraní `IEnumerator` a `IEnumerable`.

## <a name="collection-parameters"></a>Parametry kolekce
 ✔️ použít jako typ parametru možnost minimálního specializovaného typu. Většina členů, kteří přibírají kolekce jako parametry, používá rozhraní `IEnumerable<T>`.

 ❌ nepoužívejte <xref:System.Collections.Generic.ICollection%601> nebo <xref:System.Collections.ICollection> jako parametr pouze pro přístup k vlastnosti `Count`.

 Místo toho zvažte použití `IEnumerable<T>` nebo `IEnumerable` a dynamicky kontroluje, zda objekt implementuje `ICollection<T>` nebo `ICollection`.

## <a name="collection-properties-and-return-values"></a>Vlastnosti kolekce a návratové hodnoty
 ❌ neposkytují nastavitelné vlastnosti kolekce.

 Uživatelé mohou obsah kolekce nahradit tak, že nejprve vymaže kolekci a následně přidají nový obsah. Pokud je nahrazení celé kolekce běžným scénářem, zvažte poskytnutí `AddRange` metody v kolekci.

 ✔️ použít `Collection<T>` nebo podtřídu `Collection<T>` pro vlastnosti nebo návratové hodnoty reprezentující kolekce pro čtení i zápis.

 Pokud `Collection<T>` nesplňuje určitý požadavek (například kolekce nesmí implementovat <xref:System.Collections.IList>), použijte vlastní kolekci implementací `IEnumerable<T>`, `ICollection<T>`nebo <xref:System.Collections.Generic.IList%601>.

 ✔️ použít <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podtřídu `ReadOnlyCollection<T>`nebo ve výjimečných případech `IEnumerable<T>` pro vlastnosti nebo návratové hodnoty reprezentující kolekce jen pro čtení.

 Obecně je vhodnější `ReadOnlyCollection<T>`. Pokud nesplňuje určitý požadavek (například shromažďování nesmí implementovat `IList`), použijte vlastní kolekci implementací `IEnumerable<T>`, `ICollection<T>`nebo `IList<T>`. Pokud implementujete vlastní kolekci jen pro čtení, implementujte `ICollection<T>.IsReadOnly` pro návrat `true`.

 V případech, kdy jste si jisti, že jediný scénář, který budete chtít někdy podporovat, je iterace jenom pro přeposílání, můžete jednoduše použít `IEnumerable<T>`.

 ✔️ Zvažte použití podtříd obecných základních kolekcí namísto přímého použití kolekcí.

 To umožňuje lepší název a přidání pomocných členů, kteří nejsou přítomni v základních typech kolekce. To se hodí hlavně pro rozhraní API vysoké úrovně.

 ✔️ Zvažte vrácení podtřídy `Collection<T>` nebo `ReadOnlyCollection<T>` z velmi běžně používaných metod a vlastností.

 To umožní přidat pomocné metody nebo změnit implementaci kolekce v budoucnu.

 ✔️ Zvažte použití kolekce s klíčem, pokud položky uložené v kolekci mají jedinečné klíče (jména, ID atd.). Kolekce s klíčem jsou kolekce, které mohou být indexovány pomocí celého čísla i klíče a jsou obvykle implementovány děděním z `KeyedCollection<TKey,TItem>`.

 Kolekce s klíčem mají obvykle větší nároky na paměť a neměly by se používat v případě, že režie paměti převyšuje výhody použití klíčů.

 ❌ nevrací hodnoty null z vlastností kolekce nebo z metod vracejících kolekce. Místo toho se vrátí prázdná kolekce nebo prázdné pole.

 Obecným pravidlem je, že kolekce a pole s hodnotou null a prázdné (0 položka) by měly být ošetřeny stejným způsobem.

### <a name="snapshots-versus-live-collections"></a>Snímky versus živé kolekce
 Kolekce představující stav v určitém okamžiku se nazývají kolekce snímků. Například kolekce obsahující řádky vrácené z databázového dotazu by byla snímkem. Kolekce, které vždy představují aktuální stav, se nazývají živé kolekce. Například kolekce `ComboBox`ch položek je živá kolekce.

 ❌ nevracet kolekce snímků z vlastností. Vlastnosti by měly vracet živé kolekce.

 Metody getter vlastnosti by měly být velmi prosté operace. Vrácení snímku vyžaduje vytvoření kopie interní kolekce v operaci O (n).

 ✔️ použít buď kolekci snímků, nebo živý `IEnumerable<T>` (nebo její podtyp) k vyjádření kolekcí, které jsou nestálé (to znamená, že se může změnit bez explicitní úpravy kolekce).

 Obecně platí, že všechny kolekce, které představují sdílený prostředek (například soubory v adresáři), jsou nestálé. Tyto kolekce jsou velmi obtížné nebo nemožné implementovat jako živé kolekce, pokud implementace nestačí jenom pro dopředné enumerátory.

## <a name="choosing-between-arrays-and-collections"></a>Výběr mezi poli a kolekcemi
 ✔️ preferovat kolekce před poli.

 Kolekce poskytují větší kontrolu nad obsahem, můžou se v průběhu času vyvíjet a jsou užitečnější. Kromě toho se nedoporučuje používat pole pro scénáře jen pro čtení, protože náklady na klonování pole jsou zakazují. Studie použitelnosti ukázaly, že někteří vývojáři se lépe cítí pomocí rozhraní API založených na kolekcích.

 Pokud ale vyvíjíte rozhraní API nízké úrovně, může být lepší použít pole pro scénáře pro čtení i zápis. Pole mají menší nároky na paměť, což pomáhá snižovat pracovní sadu a přístup k prvkům v poli je rychlejší, protože je optimalizován modulem runtime.

 ✔️ Zvažte použití polí v rozhraních API nízké úrovně k minimalizaci spotřeby paměti a maximalizaci výkonu.

 ✔️ místo kolekcí bajtů použít pole bajtů.

 ❌ nepoužívejte pole pro vlastnosti, pokud by vlastnost musela vracet nové pole (například kopie interního pole) pokaždé, když je volána vlastnost getter.

## <a name="implementing-custom-collections"></a>Implementace vlastních kolekcí
 ✔️ Při navrhování nových kolekcí zvažte dědění z `Collection<T>`, `ReadOnlyCollection<T>`nebo `KeyedCollection<TKey,TItem>`.

 ✔️ implementovat `IEnumerable<T>` při navrhování nových kolekcí. Zvažte implementaci `ICollection<T>` nebo dokonce `IList<T>`, kde to dává smysl.

 Při implementaci takové vlastní kolekce se řiďte vzorem rozhraní API vytvořeným `Collection<T>` a `ReadOnlyCollection<T>` co nejpřesněji. To znamená, že je třeba implementovat stejné členy explicitně, pojmenovat parametry jako tyto dvě kolekce a tak dále.

 ✔️ Zvažte implementaci neobecného rozhraní kolekce (`IList` a `ICollection`), pokud kolekce bude často předána rozhraním API, která přebírají tato rozhraní jako vstup.

 ❌ se vyhnout implementaci rozhraní kolekcí u typů se složitými rozhraními API, která nesouvisí s konceptem kolekce.

 ❌ nedědí z neobecných základních kolekcí, jako je například `CollectionBase`. Místo toho použijte `Collection<T>`, `ReadOnlyCollection<T>`a `KeyedCollection<TKey,TItem>`.

### <a name="naming-custom-collections"></a>Pojmenovávání vlastních kolekcí
 Kolekce (typy, které implementují `IEnumerable`) se vytvářejí hlavně ze dvou důvodů: (1) pro vytvoření nové struktury dat s operacemi specifickými pro strukturu a často různé charakteristiky výkonu než stávající datové struktury (např. <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) a (2) pro vytvoření specializované kolekce pro uchovávání konkrétní sady položek (například <xref:System.Collections.Specialized.StringCollection>). V interní implementaci aplikací a knihoven se často používají datové struktury. Specializované kolekce jsou převážně vystaveny v rozhraních API (jako typy vlastností a parametrů).

 ✔️ použijte příponu "Dictionary" v názvu abstrakce implementující `IDictionary` nebo `IDictionary<TKey,TValue>`.

 ✔️ použít příponu "Collection" v názvech typů, které implementují `IEnumerable` (nebo některé z jeho potomků) a představují seznam položek.

 ✔️ použijte název příslušné struktury dat pro vlastní datové struktury.

 ❌ nepoužívejte žádné přípony, což by znamenalo konkrétní implementaci, jako je "LinkedList" nebo "zatřiďovací tabulka", v názvech abstrakcí kolekce.

 ✔️ Zvažte názvy kolekcí s názvem typu položky. Například kolekce, která ukládá položky typu `Address` (implementace `IEnumerable<Address>`), by měla být pojmenována `AddressCollection`. Pokud je typ položky rozhraní, může být předpona "I" typu položky vynechána. Proto může být kolekce <xref:System.IDisposable>ch položek volána `DisposableCollection`.

 ✔️ Zvažte použití předpony "ReadOnly" v názvech kolekcí jen pro čtení, pokud může být do rozhraní přidána odpovídající zapisovatelná kolekce nebo již existuje.

 Například kolekce řetězců jen pro čtení by měla být volána `ReadOnlyStringCollection`.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
