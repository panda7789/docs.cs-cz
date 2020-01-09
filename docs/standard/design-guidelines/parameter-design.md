---
title: Návrh parametru
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: e3725cd11e170c64b6cbf7d77a7a6526603dfd95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709111"
---
# <a name="parameter-design"></a>Návrh parametru

Tato část obsahuje obecné pokyny pro návrh parametrů, včetně oddílů s pokyny pro kontrolu argumentů. Kromě toho byste měli postupovat podle pokynů popsaných v tématu [parametry pojmenování](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** používat alespoň odvozený typ parametru, který poskytuje funkci vyžadovanou člena.  
  
 Předpokládejme například, že chcete navrhnout metodu, která vytvoří výčet kolekce a vytiskne každou položku do konzoly. Taková metoda by měla přijmout <xref:System.Collections.IEnumerable> jako parametr, ne <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList>, například.  
  
 **X DO NOT** používat vyhrazené parametry.  
  
 Pokud je v některé budoucí verzi potřeba více vstupů ke členu, může být přidáno nové přetížení.  
  
 **X DO NOT** mít veřejně vystaven metod, které berou ukazatele, pole ukazatele nebo vícerozměrná pole jako parametry.  
  
 Ukazatele a multidimenzionální pole jsou poměrně obtížné použít. Ve většině případů je možné rozhraní API přenavrhovat, aby se předešlo přebírání těchto typů jako parametrů.  
  
 **✓ DO** umístit všechny `out` všechny hodnoty ve-následující parametry a `ref` parametry (s výjimkou pole parametrů), i když je výsledkem nekonzistence v parametru řazení mezi přetížení (najdete v části [člena Přetížení](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 Parametry `out` lze zobrazit jako nadbytečné návratové hodnoty a jejich seskupení usnadňuje pochopení signatury metody.  
  
 **✓ DO** být konzistentní názvy parametrů při přepisování členy nebo implementace členů rozhraní.  
  
 Tím se lépe komunikuje vztah mezi metodami.  
  
### <a name="choose-between-enum-and-boolean-parameters"></a>Zvolit mezi výčtovým a logickým parametrem  
 **✓ DO** použijte výčty, pokud člen byste jinak museli dvě nebo více parametrů logická hodnota.  
  
 **X DO NOT** používat logické hodnoty, pokud jste si naprosto jisti, nikdy bude potřeba více než dvě hodnoty.  
  
 Výčty umožňují určit místo pro budoucí sčítání hodnot, ale měli byste si uvědomit o všech důsledcích přidávání hodnot do výčtů, které jsou popsány v [návrhu výčtu](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** pomocí logických výrazů pro konstruktor parametry, které jsou hodnoty skutečně dvou stavů a jednoduše slouží k inicializaci logická hodnota vlastnosti.  
  
### <a name="validate-arguments"></a>Ověřit argumenty  
 **✓ DO** ověřte argumenty předaný veřejný, chráněný nebo – explicitně implementovaná členy. Pokud se ověření nepovede, vyvolejte <xref:System.ArgumentException?displayProperty=nameWithType>nebo jednu z jejích podtříd.  
  
 Všimněte si, že skutečné ověření nemusí nutně probíhat ve veřejném nebo chráněném členu. Může dojít na nižší úrovni v některé soukromé nebo interní rutině. Hlavním bodem je, že celá oblast Surface, která je vystavena koncovým uživatelům, kontroluje argumenty.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> Pokud je předán prázdný argument a člen nepodporuje argumenty null.  
  
 **✓ DO** ověření výčtu parametry.  
  
 Nepředpokládat argumenty výčtu budou v rozsahu definovaném výčtem. Modul CLR umožňuje přetypování libovolné celočíselné hodnoty do hodnoty Enum i v případě, že ve výčtu není definována hodnota.  
  
 **X DO NOT** použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> rozsahu výčtu kontrol.  
  
 **✓ DO** mějte na paměti, že měnitelný argumenty byl změněn. po jejich byly ověřeny.  
  
 Pokud je člen citlivý na zabezpečení, doporučujeme vytvořit kopii a pak ověřit a zpracovat argument.  
  
### <a name="pass-parameters"></a>Parametry předání  
 Z perspektivy návrháře architektury existují tři hlavní skupiny parametrů: parametry podle hodnoty, parametry `ref` a parametry `out`.  
  
 Pokud je předán argument pomocí parametru podle hodnoty, člen obdrží kopii skutečného předaného argumentu. Pokud je argumentem hodnotový typ, je kopie argumentu vložena do zásobníku. Pokud je argumentem odkazový typ, kopie odkazu je vložena do zásobníku. Nejoblíbenější jazyky CLR, jako například C#, Visual Basic a C++, jsou ve výchozím nastavení k předávání parametrů podle hodnoty.  
  
 Pokud je předán argument pomocí parametru `ref`, člen obdrží odkaz na vlastní předaný argument. Pokud je argumentem hodnotový typ, odkaz na argument je vložen do zásobníku. Pokud je argumentem odkazový typ, odkaz na odkaz je vložen do zásobníku. parametry `Ref` lze použít k umožnění člena upravovat argumenty předané volajícím.  
  
 parametry `Out` se podobají parametrům `ref` s malým rozdílem. Parametr je zpočátku považován za nepřiřazený a nemůže být načten v těle členu před tím, než se mu přiřadí nějaká hodnota. Parametr musí být také přiřazen určitou hodnotu před tím, než se člen vrátí.  
  
 **X AVOID** pomocí `out` nebo `ref` parametry.  
  
 Použití parametrů `out` nebo `ref` vyžaduje zkušenosti s ukazateli, porozumění způsobu, jakým se liší typy hodnot a referenční typy, a metody zpracování s více návratových hodnot. Rozdíl mezi parametry `out` a `ref` navíc není široce srozumitelný. Architektura architekt návrhu pro obecnou cílovou skupinu by neměla očekávat, že uživatelé budou hlavní pracovat s parametry `out` nebo `ref`.  
  
 **X DO NOT** předat odkazové typy odkazem.  
  
 Na pravidlo existují omezené výjimky, jako je například metoda, kterou lze použít k prohození odkazů.  
  
### <a name="members-with-variable-number-of-parameters"></a>Členové s proměnným počtem parametrů  
 Členy, kteří mohou převzít proměnný počet argumentů, jsou vyjádřeny zadáním parametru Array. Například <xref:System.String> poskytuje následující metodu:  
  
```csharp  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Uživatel pak může zavolat metodu <xref:System.String.Format%2A?displayProperty=nameWithType>, a to následujícím způsobem:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Přidáním klíčového slova C# params do parametru pole se změní parametr na parametr pole param, který se nazývá, a poskytuje zástupce pro vytvoření dočasného pole.  
  
```csharp  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Díky tomu může uživatel volat metodu předáním prvků pole přímo v seznamu argumentů.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Všimněte si, že klíčové slovo params lze přidat pouze k poslednímu parametru v seznamu parametrů.  
  
 **✓ CONSIDER** přidávání params – klíčové slovo do pole parametry, pokud očekáváte, koncovým uživatelům předat pole s malý počet elementů. Pokud se očekává, že se v běžných scénářích budou předávat i celá řada prvků, uživatelé pravděpodobně nebudou tyto prvky vložit do seznamu, takže klíčové slovo params není nutné.  
  
 **X AVOID** pomocí parametry pole, pokud má volající by téměř vždy již vstupu v matici.  
  
 Například členy s parametry bajtového pole by se téměř nikdy nevolaly předáním jednotlivých bajtů. Z tohoto důvodu parametry bajtového pole v .NET Framework nepoužívají klíčové slovo params.  
  
 **X DO NOT** použijte parametry pole, pokud je pole upraveném člen trvá parametr pole parametry.  
  
 Vzhledem k tomu, že mnoho kompilátorů přepíná argumenty člena do dočasného pole na webu volání, pole může být dočasným objektem, a proto dojde ke ztrátě všech změn v poli.  
  
 **✓ CONSIDER** pomocí klíčového slova parametry v jednoduchých přetížení, i když ho nelze použít na složitější přetížení.  
  
 Zeptejte se sami, pokud by uživatelé měli hodnotu pole params v jednom přetížení, i když to nebylo ve všech přetíženích.  
  
 **✓ DO** zkuste pořadí parametrů, aby bylo možné použít params – klíčové slovo.  
  
 **✓ CONSIDER** poskytnutí speciální přetížení a cesty kódu pro volání s malým počtem argumentů rozhraní API velmi náročné na výkon.  
  
 Díky tomu je možné vyhnout se vytváření objektů pole při volání rozhraní API s malým počtem argumentů. Vytvořte názvy parametrů tak, že převezmete jednotný tvar parametru Array a přidáte číselnou příponu.  
  
 Tuto věc byste měli provést pouze v případě, že se chystáte o zvláštní cestu k celému kódu, ne pouze vytvořit pole a volat obecnější metodu.  
  
 **✓ DO** Uvědomte si, že null by prošel jako argument parametry pole.  
  
 Před zpracováním byste měli ověřit, že pole není null.  
  
 **X DO NOT** použít `varargs` metody, které jsou známé jako se třemi tečkami.  
  
 Některé jazyky CLR, například C++, podporují alternativní konvenci pro předávání seznamů parametrů proměnných s názvem `varargs` metody. Konvence by se neměla používat v rozhraních, protože není kompatibilní se specifikací CLS.  
  
### <a name="pointer-parameters"></a>Parametry ukazatele  
 Obecně platí, že by ukazatelé neměl být uveden v oblasti veřejného povrchu dobře navržené architektury spravovaného kódu. Ve většině případů by měly být ukazatele zapouzdřeny. V některých případech se ale vyžaduje, aby se v případě interoperability a používání ukazatelů v takových případech používaly příslušné ukazatele.  
  
 **✓ DO** alternativu přinášejí kteréhokoli člena, který se použije argument ukazatele, protože ukazatele nejsou kompatibilní se specifikací CLS.  
  
 **X AVOID** provádění nákladné argument kontrola ukazatel argumentů.  
  
 **✓ DO** použijte běžné konvence související ukazatele při návrhu členy s ukazatele.  
  
 Například není nutné předávat počáteční index, protože k dosažení stejného výsledku lze použít jednoduchou aritmetickou akci s ukazatelem.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
