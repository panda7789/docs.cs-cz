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
author: KrzysztofCwalina
ms.openlocfilehash: 5a0f6e0fab5d0f2fe8574e348fc6b8ae726eeb99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617210"
---
# <a name="parameter-design"></a>Návrh parametru
Tato část obsahuje pokyny pro široké parametr návrh, včetně oddíly s pokyny pro kontrolu argumenty. Kromě toho by měla odkazovat na pokynů popsaných v [Naming Parameters](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** používat alespoň odvozený typ parametru, který poskytuje funkci vyžadovanou člena.  
  
 Předpokládejme například, že chcete navrhnout metodu, která vytvoří výčet kolekce a vypíše do konzoly pro každou položku. Tato metoda by měla přijímat <xref:System.Collections.IEnumerable> jako parametr, ne <xref:System.Collections.ArrayList> nebo <xref:System.Collections.IList>, např.  
  
 **X DO NOT** používat vyhrazené parametry.  
  
 Pokud v některé budoucí verzi je potřeba další vstup pro člena, je možné přidat nové přetížení.  
  
 **X DO NOT** mít veřejně vystaven metod, které berou ukazatele, pole ukazatele nebo vícerozměrná pole jako parametry.  
  
 Ukazatele a vícerozměrná pole jsou poměrně obtížné správně použít. V téměř všech případech může být rozhraní API přepracovali tak, vyhnete se tak tyto typy jako parametry.  
  
 **✓ DO** umístit všechny `out` všechny hodnoty ve-následující parametry a `ref` parametry (s výjimkou pole parametrů), i když je výsledkem nekonzistence v parametru řazení mezi přetížení (najdete v části [člena Přetížení](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Parametrů se dají považovat za velmi návratové hodnoty, a jejich seskupováním usnadňuje podpis metody pochopit.  
  
 **✓ DO** být konzistentní názvy parametrů při přepisování členy nebo implementace členů rozhraní.  
  
 Komunikuje se to lépe vztah mezi metodami.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Volba mezi výčtu a logické parametry  
 **✓ DO** použijte výčty, pokud člen byste jinak museli dvě nebo více parametrů logická hodnota.  
  
 **X DO NOT** používat logické hodnoty, pokud jste si naprosto jisti, nikdy bude potřeba více než dvě hodnoty.  
  
 Výčty získáte některé prostor pro budoucí součet hodnot, ale je třeba si uvědomit všechny rozbor aspektů přidání hodnot do výčty, které jsou popsány v [návrh výčtu](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** pomocí logických výrazů pro konstruktor parametry, které jsou hodnoty skutečně dvou stavů a jednoduše slouží k inicializaci logická hodnota vlastnosti.  
  
### <a name="validating-arguments"></a>Validaci argumentů  
 **✓ DO** ověřte argumenty předaný veřejný, chráněný nebo – explicitně implementovaná členy. Vyvolat <xref:System.ArgumentException?displayProperty=nameWithType>, nebo jeden z jejích podtříd, pokud se ověření nezdaří.  
  
 Všimněte si, že skutečné ověřování nemusí nutně dojde v veřejný nebo chráněný člen samotný. K tomu mohlo dojít na nižší úrovni v rutině některé soukromé nebo interní. Nejdůležitější je, že celý plochy, která je vystavena koncovým uživatelům kontroluje argumenty.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> Pokud je předán prázdný argument a člen nepodporuje argumenty null.  
  
 **✓ DO** ověření výčtu parametry.  
  
 Nepředpokládejte, že argumenty výčtu bude v rozsahu definovaném touto výčtového typu. Modul CLR umožňuje i v případě, že hodnota není definována ve výčtovém typu přetypování hodnotu celého čísla na hodnoty výčtu.  
  
 **X DO NOT** použít <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> rozsahu výčtu kontrol.  
  
 **✓ DO** mějte na paměti, že měnitelný argumenty byl změněn. po jejich byly ověřeny.  
  
 Pokud je člen citlivé z hlediska zabezpečení, jsou ukončena. doporučujeme vytvořit kopii a pak ověření a zpracování argument.  
  
### <a name="parameter-passing"></a>Předávání parametrů  
 Z perspektivy návrháře rozhraní framework, jsou tři hlavní skupiny parametry: parametry, podle hodnoty `ref` parametry, a `out` parametry.  
  
 Pokud argument je předat prostřednictvím parametru-hodnota, člen obdrží kopii je skutečný argument předaný v. Pokud je argumentem Typ hodnoty, kopie argumentu je vložen do zásobníku. Pokud je argumentem Typ odkazu, zkopírovat odkaz přejde do zásobníku. Nejoblíbenější jazyky CLR, jako je C#, VB.NET a C++, výchozí k předání parametrů podle hodnoty.  
  
 Pokud argument se předává `ref` parametru, členu přijímá odkaz na skutečný argument předaný. Pokud je argumentem Typ hodnoty, odkaz na argument je vložen do zásobníku. Pokud je argumentem Typ odkazu, odkaz na odkaz je vložen do zásobníku. `Ref` Parametry lze povolit členu, který chcete upravit argumenty předaná volající funkcí.  
  
 `Out` parametry jsou podobné `ref` parametry s několik malých rozdílů. Parametr je zpočátku považován za nepřiřazené a nelze jej načíst v těle členské předtím, než je přiřazen některá z hodnot. Parametr má také přiřadit některá z hodnot před vrácením člena.  
  
 **X AVOID** pomocí `out` nebo `ref` parametry.  
  
 Pomocí `out` nebo `ref` parametry vyžaduje zkušenosti s ukazateli, pochopení, jak se liší typy hodnot a odkazové typy a metody s více návratových zpracování. Také rozdíl mezi `out` a `ref` parametrů není běžně chápán. Architekti Framework návrhu pro širokou veřejnost, by neměli očekávat uživatelům pracovat s `out` nebo `ref` parametry.  
  
 **X DO NOT** předat odkazové typy odkazem.  
  
 Existují některé mohou nastat výjimky z pravidla, jako je například metodu, která je možné přepínat odkazy.  
  
### <a name="members-with-variable-number-of-parameters"></a>Členy s proměnný počet parametrů  
 Tím, že poskytuje jako parametr pole jsou vyjádřeny členy, které můžete provést proměnný počet argumentů. Například <xref:System.String> poskytuje následující metody:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Uživatel potom může volat <xref:System.String.Format%2A?displayProperty=nameWithType> metodu následujícím způsobem:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Přidání C# klíčového slova params na parametr pole parametru se změní na pole parametr params takzvané a poskytuje zástupce vytvořit dočasné pole.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 To umožňuje uživateli volat metodu předáním prvky pole přímo v seznamu argumentů.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Všimněte si, že klíčové slovo params lze přidat pouze pro poslední parametr v seznamu parametrů.  
  
 **✓ CONSIDER** přidávání params – klíčové slovo do pole parametry, pokud očekáváte, koncovým uživatelům předat pole s malý počet elementů. Pokud se očekává, že velký počet prvků se předají v běžných scénářů, uživatelé budou pravděpodobně není předejte tyto prvky vložené přesto a tak klíčové slovo params není nutné.  
  
 **X AVOID** pomocí parametry pole, pokud má volající by téměř vždy již vstupu v matici.  
  
 Například členové s parametry pole bajtů by téměř nikdy volat předáním jednotlivých bajtech. Z tohoto důvodu nepoužívejte parametry pole bajtů v rozhraní .NET Framework – klíčové slovo params.  
  
 **X DO NOT** použijte parametry pole, pokud je pole upraveném člen trvá parametr pole parametry.  
  
 Z důvodu skutečnost, že mnoho kompilátorů zapnout argumenty, které mají člena do přechodného pole na lokalitu volání pole může být dočasný objekt, a proto budou ztraceny všechny změny do pole.  
  
 **✓ CONSIDER** pomocí klíčového slova parametry v jednoduchých přetížení, i když ho nelze použít na složitější přetížení.  
  
 Položte si otázku: Pokud uživatelé by hodnota pole parametry s jedním přetížením i v případě, že nebyl ve všech přetížení.  
  
 **✓ DO** zkuste pořadí parametrů, aby bylo možné použít params – klíčové slovo.  
  
 **✓ CONSIDER** poskytnutí speciální přetížení a cesty kódu pro volání s malým počtem argumentů rozhraní API velmi náročné na výkon.  
  
 Díky tomu je možné se vyhnout, vytvářet objekty array, při volání rozhraní API s malý počet argumentů. Názvy parametrů formuláře singulární podobě parametr pole a přidáním číselnou příponou.  
  
 Byste měli jenom udělat Pokud budete pro zvláštní případy cesta celý kód, ne jenom vytvořit pole a volání obecné metody.  
  
 **✓ DO** Uvědomte si, že null by prošel jako argument parametry pole.  
  
 Měli byste ověřit, že pole není null před zpracováním.  
  
 **X DO NOT** použít `varargs` metody, které jsou známé jako se třemi tečkami.  
  
 Některé jazyky CLR, například C++, podporují alternativní konvence pro předávání seznamy parametrů proměnných volá `varargs` metody. Tato konvence by neměl v rozhraní, použít, protože není kompatibilní se Specifikací CLS.  
  
### <a name="pointer-parameters"></a>Parametry ukazatele  
 Obecně platí ukazatele by se neměl zobrazit ve veřejnou oblast Framework dobře navržené spravovaného kódu. Ve většině případů, by měl být zapouzdřen ukazatele. Ale v některých případech jsou požadovány pro interoperabilitu důvodů ukazatele a pomocí ukazatelů v takových případech je vhodné.  
  
 **✓ DO** alternativu přinášejí kteréhokoli člena, který se použije argument ukazatele, protože ukazatele nejsou kompatibilní se specifikací CLS.  
  
 **X AVOID** provádění nákladné argument kontrola ukazatel argumentů.  
  
 **✓ DO** použijte běžné konvence související ukazatele při návrhu členy s ukazatele.  
  
 Například není nutné předat počáteční index, protože jednoduché aritmetika ukazatele lze použít k dosažení stejného výsledku.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
