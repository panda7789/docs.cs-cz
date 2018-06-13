---
title: Parametr návrhu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e39b38fd72f9f3b9ce76aa6f7e96e44841daabb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578271"
---
# <a name="parameter-design"></a>Parametr návrhu
Tato část obsahuje obecné Rady ohledně návrhu parametr, včetně oddíly s pokyny pro kontrolu argumenty. Kromě toho se seznamte s podle pokynů popsaných v [pojmenování parametry](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **PROVEĎTE ✓** používat alespoň odvozený typ parametru, který poskytuje funkci vyžadovanou člena.  
  
 Předpokládejme například, že můžete navrhnout metodu, která vytvoří výčet kolekce a vytiskne každou položku do konzoly. Tato metoda by měla trvat <xref:System.Collections.IEnumerable> jako parametr, není <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList>, např.  
  
 **X nesmí** používat vyhrazené parametry.  
  
 Další vstup na člena, je potřeba v některých budoucí verze, mohou být přidány nové přetížení.  
  
 **X nesmí** mít veřejně vystaven metod, které berou ukazatele, pole ukazatele nebo vícerozměrná pole jako parametry.  
  
 Multidimenzionální pole a ukazatelé jsou relativně obtížně použitelný správně. Ve většině případů může být rozhraní API upravený tak, aby Neberte tyto typy jako parametry.  
  
 **PROVEĎTE ✓** umístit všechny `out` všechny hodnoty ve-následující parametry a `ref` parametry (s výjimkou pole parametrů), i když je výsledkem nekonzistence v parametru řazení mezi přetížení (najdete v části [člena Přetížení](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametry se dají považovat za velmi návratové hodnoty, a jejich seskupování usnadňuje podpis metody pochopit.  
  
 **PROVEĎTE ✓** být konzistentní názvy parametrů při přepisování členy nebo implementace členů rozhraní.  
  
 To lépe komunikuje vztah mezi metody.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Volba mezi logickou parametry a výčtu  
 **PROVEĎTE ✓** použijte výčty, pokud člen byste jinak museli dvě nebo více parametrů logická hodnota.  
  
 **X nesmí** používat logické hodnoty, pokud jste si naprosto jisti, nikdy bude potřeba více než dvě hodnoty.  
  
 Výčty získáte určitý prostor pro budoucí přidání hodnot, ale byste měli vědět všechny dopadů přidání hodnot do výčty, které jsou popsané v [návrhu výčtu](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ ZVAŽTE** pomocí logických výrazů pro konstruktor parametry, které jsou hodnoty skutečně dvou stavů a jednoduše slouží k inicializaci logická hodnota vlastnosti.  
  
### <a name="validating-arguments"></a>Ověřování argumenty  
 **PROVEĎTE ✓** ověřte argumenty předaný veřejný, chráněný nebo – explicitně implementovaná členy. Throw <xref:System.ArgumentException?displayProperty=nameWithType>, nebo jeden z jejích podtříd, pokud se ověření nezdaří.  
  
 Všimněte si, že samotné ověření nemusí nutně dojít ve veřejných nebo chráněného člena samotného. K tomu mohlo dojít na nižší úrovni v některé rutiny soukromý nebo interní. Hlavní bod je, že celém povrchu, který je zveřejněný koncovým uživatelům kontroluje argumenty.  
  
 **PROVEĎTE ✓** throw <xref:System.ArgumentNullException> Pokud je předán prázdný argument a člen nepodporuje argumenty null.  
  
 **PROVEĎTE ✓** ověření výčtu parametry.  
  
 Nepředpokládejte výčtu argumenty bude v rozsah definovaný hodnotami výčtu. Modul CLR umožňuje přetypování žádné celočíselnou hodnotu na hodnotu výčtu, i v případě, že hodnota není definována ve výčtu.  
  
 **X nesmí** použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> rozsahu výčtu kontrol.  
  
 **PROVEĎTE ✓** mějte na paměti, že měnitelný argumenty byl změněn. po jejich byly ověřeny.  
  
 Pokud je člen citlivé na zabezpečení, můžete se doporučuje vytvoření kopie a poté ověření a zpracování argument.  
  
### <a name="parameter-passing"></a>Předávání parametrů  
 Z pohledu návrháře framework, jsou tři hlavní skupiny parametrů: parametry, pomocí hodnoty `ref` parametrů, a `out` parametry.  
  
 Když argument je předána prostřednictvím parametru-hodnota, člen obdrží kopii skutečného argument předaný v. Pokud má argument hodnotu typu hodnoty, je kopie argumentu uložena v zásobníku. Pokud je argument typu odkazu, kopie odkaz na zprovozněn v zásobníku. Nejoblíbenější jazyky CLR, jako je C#, VB.NET a C++, výchozí nastavení předávání parametrů hodnotou.  
  
 Když je argument předaný prostřednictvím `ref` parametr člen obdrží odkaz na skutečné argument předaný v. Pokud má argument hodnotu typu hodnoty, je v zásobníku uvést odkaz na argument. Pokud je argument typu odkazu, odkaz na odkaz na zprovozněn v zásobníku. `Ref` Parametry lze povolit člena pro úpravu argumenty předaná volající funkcí.  
  
 `Out` parametry jsou podobné `ref` parametry se některé malé rozdíly. Parametr je zpočátku považovat za nepřiřazené a nelze ho přečíst v těle člen před přiřazením některá z hodnot. Parametr navíc má být přiděleny určitou hodnotu, než vrátí člena.  
  
 **X nepoužívejte** pomocí `out` nebo `ref` parametry.  
  
 Pomocí `out` nebo `ref` parametry vyžaduje zkušenosti s ukazatele, pochopení, jak se liší typy hodnot a typy odkazu a zpracování metod s více vrácených hodnot. Navíc rozdíl mezi `out` a `ref` parametry nebyl pochopen široce. Architekti Framework navrhování všem uživatelům by neměl očekávat uživatelům hlavní práci s `out` nebo `ref` parametry.  
  
 **X nesmí** předat odkazové typy odkazem.  
  
 Existují některé omezené výjimky pravidla, jako je například metoda, která slouží k Prohodit odkazy.  
  
### <a name="members-with-variable-number-of-parameters"></a>Členy s proměnný počet parametrů  
 Poskytnutím parametru pole jsou vyjádřeny členy, které může provádět proměnný počet argumentů. Například <xref:System.String> poskytuje následující metody:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Uživatel potom může volat <xref:System.String.Format%2A?displayProperty=nameWithType> metoda následujícím způsobem:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Přidávání do parametr pole jazyce C# params – klíčové slovo změny parametr parametr pole takzvané parametry a poskytuje zástupce k vytvoření dočasného pole.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 To umožňuje uživateli volat metodu předáním elementy pole přímo v seznamu argumentů.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Všimněte si, že params – klíčové slovo lze přidat pouze poslední parametr v seznamu parametrů.  
  
 **✓ ZVAŽTE** přidávání params – klíčové slovo do pole parametry, pokud očekáváte, koncovým uživatelům předat pole s malý počet elementů. Pokud je očekáváno, že velký počet elementů předány společné scénáře, uživatelé budou pravděpodobně není předejte tyto elementy vložené přesto a proto není nutné params – klíčové slovo.  
  
 **X nepoužívejte** pomocí parametry pole, pokud má volající by téměř vždy již vstupu v matici.  
  
 Například by členy s parametry pole bajtů názvem téměř žádné předáním jednotlivých bajtů. Z tohoto důvodu nepoužívejte parametry pole bajtů v rozhraní .NET Framework – klíčové slovo parametry.  
  
 **X nesmí** použijte parametry pole, pokud je pole upraveném člen trvá parametr pole parametry.  
  
 Z důvodu fakt, že mnoho kompilátory zapnout argumenty, které mají člena do dočasné pole v lokalitě volání pole může být dočasný objekt, a proto budou ztraceny všechny změny do pole.  
  
 **✓ ZVAŽTE** pomocí klíčového slova parametry v jednoduchých přetížení, i když ho nelze použít na složitější přetížení.  
  
 Položte otázku, pokud by uživatelé hodnotu s poli parametry ve jedním přetížením i v případě, že ho nebyl v všechny přetížení.  
  
 **PROVEĎTE ✓** zkuste pořadí parametrů, aby bylo možné použít params – klíčové slovo.  
  
 **✓ ZVAŽTE** poskytnutí speciální přetížení a cesty kódu pro volání s malým počtem argumentů rozhraní API velmi náročné na výkon.  
  
 Díky tomu je možné, vyhněte se vytváření pole objektů při volání rozhraní API s malým počtem argumentů. Názvy parametrů formuláři převzetím jednotném čísle parametru pole a přidáním číselnou příponou.  
  
 Měli byste jenom to provést Pokud budete pro zvláštní případ celý kódová cesta, nejen vytvořte pole a volejte metodu obecnější.  
  
 **PROVEĎTE ✓** Uvědomte si, že null by prošel jako argument parametry pole.  
  
 Měli byste ověřit, že pole není null před zpracováním.  
  
 **X nesmí** použít `varargs` metody, které jsou známé jako se třemi tečkami.  
  
 Některé jazyky CLR, jako je C++, podpora alternativní konvence pro předávání seznamy proměnné parametrů názvem `varargs` metody. Konvence nepoužívejte v rozhraní, protože není kompatibilní se specifikací CLS.  
  
### <a name="pointer-parameters"></a>Parametry ukazatele  
 Obecně platí ukazatele neměla v veřejnou oblast Framework dobře navrženou spravovaného kódu. Ve většině případů, by měl být zapouzdřené ukazatele. Ale v některých případech jsou požadovány důvodů interoperabilita ukazatele a použití ukazatele v takových případech je vhodné.  
  
 **PROVEĎTE ✓** alternativu přinášejí kteréhokoli člena, který se použije argument ukazatele, protože ukazatele nejsou kompatibilní se specifikací CLS.  
  
 **X nepoužívejte** provádění nákladné argument kontrola ukazatel argumentů.  
  
 **PROVEĎTE ✓** použijte běžné konvence související ukazatele při návrhu členy s ukazatele.  
  
 Například není třeba předat počáteční index, protože jednoduché aritmetika ukazatele je možné použít k dosažení stejného výsledku.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
