---
title: "Kontrakty kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce74cfb9c4e0eb759fb8160ab06fa6fbde60081b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="code-contracts"></a>Kontrakty kódu
Kontrakty kódu poskytují způsob, jak určit předpoklady, vstupních a výstupních podmínek objektu v kódu. Předběžné podmínky jsou uvedeny požadavky, které musí být splněny, při zadávání metody nebo vlastnosti. Vstupních popisují očekávání v době, kdy bude ukončen kód metody nebo vlastnosti. Objekt výstupních podmínek popisují očekávanému stavu pro třídu, která je ve funkčním stavu.  
  
 Kontrakty kódu zahrnují třídy pro označení kódu, statické analyzátor pro analýzu kompilaci a analyzátor modulu runtime. Třídy pro kontrakty kódu najdete v <xref:System.Diagnostics.Contracts> oboru názvů.  
  
 Mezi výhody kontrakty kódu patří následující:  
  
-   Vylepšení testování: kontrakty kódu poskytovat statické ověření kontraktu, kontrola runtime a generování dokumentace.  
  
-   Automatické testovací nástroje: kontrakty kódu můžete použít ke generování smysluplnější testy jednotek tím, smysl testovací argumenty, které nesplňují předběžné podmínky.  
  
-   Statické ověření: statické kontrolu můžete rozhodnout, zda jsou všechny porušení smlouvy bez spuštění programu. Vyhledává implicitní kontrakty, jako je například null dereferences a pole hranice a explicitní smlouvy.  
  
-   Referenční dokumentace: dokumentace generátor rozšiřuje existující soubory dokumentace XML s informace o smlouvě. Existují také šablony stylů, které lze použít s [aplikaci Sandcastle](https://github.com/EWSoftware/SHFB) tak, aby stránky generované dokumentace části kontrakt.  
  
 Všechny jazyky rozhraní .NET Framework, můžete okamžitě využít výhod kontrakty; Nemáte k zápisu speciální analyzátor nebo kompilátoru. Doplněk sady Visual Studio vám umožní určit úroveň analýza kódu kontrakt provést. Analyzátory můžete potvrdit, že jsou smluv ve správném formátu (Kontrola typu a překlad názvů) a může vytvářet kompilované formuláře smluv ve formátu Microsoft (MSIL intermediate language). Vytváření smluv v sadě Visual Studio umožňuje využít výhod standardní IntelliSense poskytované nástroj.  
  
 Většinu metod ve třídě, kontrakt podmíněně kompilované; To znamená, kompilátor vydává volání těchto metod jenom v případě, že definujete symbol speciální CONTRACTS_FULL, pomocí `#define` – direktiva. CONTRACTS_FULL umožňuje zapisovat kontrakty ve vašem kódu bez použití `#ifdef` direktivy; může vytvářet různé verze, některé se smlouvami a některé bez.  
  
 Nástroje a podrobné pokyny pro používání kontrakty kódu najdete v tématu [kontrakty kódu](http://go.microsoft.com/fwlink/?LinkId=152461) na webu MSDN DevLabs.  
  
## <a name="preconditions"></a>Předběžné podmínky  
 Předběžné podmínky lze vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metoda. Předběžné podmínky zadejte stav, když je volána metoda. Obecně se používají k určení platné hodnoty parametrů. Všechny členy, které jsou uvedeny v předběžných podmínek musí být přístupné metoda sama; předpoklad, jinak hodnota nemusí být srozumitelné všech volajících metody. Podmínka musí mít žádné vedlejší účinky. Chování běhové selhání předběžné podmínky je určen podle analyzátor modulu runtime.  
  
 Například následující předběžnou vyjadřoval tento parametr `x` musí obsahovat hodnotu null.  
  
 `Contract.Requires( x != null );`  
  
 Pokud váš kód musí konkrétní výjimku vyvolat na selhání předběžné podmínky, můžete použít obecné přetížení <xref:System.Diagnostics.Contracts.Contract.Requires%2A> následujícím způsobem.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Starší verze vyžaduje příkazy  
 Většinu kódu obsahuje některé ověření parametru ve formě `if` - `then` - `throw` kódu. Nástroje pro kontrakt rozpoznat tyto příkazy jako předpoklady v následujících případech:  
  
-   Příkazy se zobrazí před jiné příkazy v metodě.  
  
-   Celá sada těchto příkazů následuje explicitního <xref:System.Diagnostics.Contracts.Contract> volání metody, jako je například volání <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, nebo <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> metoda.  
  
 Když `if` - `then` - `throw` příkazy zobrazí v tomto formuláři je nástroje rozpozná jako zastaralé `requires` příkazy. Pokud postupovat podle žádné jiných smluv `if` - `then` - `throw` pořadí, koncová kód <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metoda.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Všimněte si, že podmínka v předchozím testu posunut předběžnou podmínku. (Skutečné předběžnou by `x != null`.) Posunut předběžné podmínky je vysoce omezenou: musí být napsané, jak je znázorněno v předchozím příkladu; To znamená, měl by obsahovat žádné `else` klauzule a text `then` klauzule musí být jediný `throw` příkaz. `if` Testovací podléhá pravidla čistotu a viditelnost (najdete v části [pokyny týkající se používání](#usage_guidelines)), ale `throw` výrazu je podmíněno pouze čistotu pravidla. Typ výjimky však musí být jako viditelné jako metodu dojde k kontrakt.  
  
## <a name="postconditions"></a>Vstupních  
 Vstupních jsou kontrakty stavu metodu, když ho ukončí. Těsně před ukončení metody se kontroluje koncová podmínka. Chování běhové selhání vstupních je určen podle analyzátor modulu runtime.  
  
 Na rozdíl od předběžných podmínek vstupních odkazy na členy s menší viditelnosti. Klient nemusí mít k pochopení nebo k používání některé z informací vyjádřená koncová podmínka pomocí privátní stavu, ale neovlivňuje to možnost klienta lze pomocí této metody správně.  
  
### <a name="standard-postconditions"></a>Standardní vstupních  
 Standardní vstupních lze vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metoda. Vstupních express podmínku, která musí být `true` při normálním ukončení metody.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Výjimečně vysoké počty vstupních  
 Výjimečně vysoké počty vstupních jsou vstupních, které by měly být `true` při je vyvolána výjimka konkrétní metodou. Zadávat lze tyto vstupních pomocí <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metoda, jak ukazuje následující příklad.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Argument je podmínku, která musí být `true` vždy, když výjimku, která je podtypem `T` je vyvolána výjimka.  
  
 Existují některé typy výjimky, které je obtížné používat ve výjimečných koncová podmínka. Například pomocí typu <xref:System.Exception> pro `T` vyžaduje metoda zaručit podmínku bez ohledu na typ výjimky, která je vyvolána, i když je k přetečení zásobníku nebo jiné možné řízení výjimky. Výjimečně vysoké počty vstupních byste měli použít pouze pro konkrétní výjimky, které mohou být vyvolány, když členem je volána, například když <xref:System.InvalidTimeZoneException> je vyvolána pro <xref:System.TimeZoneInfo> volání metody.  
  
### <a name="special-postconditions"></a>Speciální vstupních  
 Pouze v rámci vstupních lze použít následující metody:  
  
-   Může být metoda návratové hodnoty v vstupních pomocí výrazu `Contract.Result<T>()`, kde `T` je nahrazena návratový typ metody. Když kompilátor není schopen odvození typu, je nutné ho zadat explicitně. Například se nepodařilo odvodit typy pro metody, které nepřebírají žádné argumenty, takže vyžaduje následující koncová podmínka kompilátor jazyka C#: `Contract.Ensures(0 <Contract.Result<int>())` metody s návratovým typem `void` nemůže odkazovat na `Contract.Result<T>()` v jejich vstupních.  
  
-   Hodnotu prestate v koncová podmínka odkazuje na hodnotu výrazu na začátku metody nebo vlastnosti. Používá výraz `Contract.OldValue<T>(e)`, kde `T` je typ `e`. Vždy, když je schopen odvodit typ kompilátor, můžete vynechat argument obecného typu. (Například kompilátor jazyka C# vždy odvodí typ vzhledem k tomu, jak dlouho trvá argument.) Existuje několik omezení na co se může objevit v `e` a kontexty, ve kterých se může zobrazit staré výrazu. Původní výraz nemůže obsahovat další původní výraz. Co je nejdůležitější – původní výraz musí odkazovat na hodnotu, které existovalo v metody předběžnou stavu. Jinými slovy, musí být výraz, který lze vyhodnotit tak dlouho, dokud je předběžnou metody `true`. Tady jsou několik instancí daného pravidla.  
  
    -   Hodnota musí existovat ve stavu metoda předběžnou podmínku. Chcete-li odkazovat na pole v objektu, musí zaručit předběžných podmínek, tento objekt je vždy nesmí být nulová.  
  
    -   Nemůže odkazovat na návratovou hodnotu metody ve staré výrazu:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   Nemůže odkazovat na `out` parametry v původním výrazu.  
  
    -   Původní výraz nemůže záviset na vázané proměnná kvantifikátor, pokud rozsah kvantifikátoru závisí na návratovou hodnotu metody:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Původní výraz nemůže odkazovat na parametr anonymní delegáta v <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> volat, pokud se používá jako indexer nebo argument pro volání metody:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Původní výraz nemůže proběhnout, v těle delegáta anonymní Pokud hodnotu staré výrazu závisí na některý z parametrů anonymní delegáta, není-li anonymní delegát argumentu <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metoda:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out`Parametry představovat problém, protože kontrakty zobrazí před těla metody a většina kompilátory neumožňují odkazy na `out` vstupních parametrů. Chcete tento problém vyřešit <xref:System.Diagnostics.Contracts.Contract> třída poskytuje <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metoda, která umožňuje koncová podmínka na základě `out` parametr.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         Stejně jako u <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metodu, můžete vynechat parametr obecného typu vždy, když je schopen odvodit typ kompilátoru. Kontrakt RW nahradí hodnotu volání metody, které `out` parametr. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Metoda se mohou objevit pouze v vstupních. Argument pro metodu musí být `out` , nebo parametr pole strukturou `out` parametr. Je také užitečná k odkazování na pole v koncová podmínka struktura konstruktoru.  
  
        > [!NOTE]
        >  V současné době nástrojů pro analýzu kontrakt kódu nekontrolují zda `out` parametry jsou správně inicializována a jejich zmínky v koncová podmínka ignorovat. Proto v předchozím příkladu, řádek po kontrakt použití hodnotu `x` místo celé přiřazení k němu, kompilátor by vystavovat opravte chyby. Ale na sestavení, kde je symbol preprocesoru CONTRACTS_FULL není definována (takové asa sestavení pro vydání), kompilátor dojde k chybě.  
  
## <a name="invariants"></a>Výstupních podmínek  
 Objekt výstupních podmínek jsou podmínky, které by měly být vždy, když je objekt viditelný pro klienta pro každou instanci třídy na hodnotu true. Jejich express podmínky, za kterých se považuje za správný objekt.  
  
 Neutrální metody jsou určeny označit s <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atribut. Neutrální metody musejí obsahovat žádný kód s výjimkou pořadí volání <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metoda, z nichž každý určuje jednotlivé neutrální, jak je znázorněno v následujícím příkladu.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 Výstupních podmínek jsou definovány podmíněně symbol preprocesoru CONTRACTS_FULL. Při kontrole, spuštění, se kontroluje výstupních podmínek na konci každé veřejná metoda. Pokud neutrální uvádí veřejná metoda ve stejné třídě, invariantní zkontrolujte, jestli by se stalo normálně na konci této veřejné metody je zakázané. Místo toho kontrola probíhá pouze na konci volání nejkrajnější metody do třídy. Také se to stane, když je třída opětovný vstup z důvodu volání metody na jiné třídy. Výstupních podmínek není zaškrtnuta možnost pro finalizační metody objektu nebo pro všechny metody, které implementují <xref:System.IDisposable.Dispose%2A> metoda.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Pokyny týkající se používání  
  
### <a name="contract-ordering"></a>Kontrakt řazení  
 Následující tabulka uvádí prvky, které byste měli používat při zápisu metoda kontrakty pořadí.  
  
|`If-then-throw statements`|Veřejné předběžné podmínky zpětně kompatibilní|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Všechny veřejné předběžné podmínky.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny veřejné vstupních (normální).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Všechny veřejné výjimečných vstupních.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny privátní nebo interní (normální) vstupních.|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Všechny privátní nebo interní výjimečných vstupních.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Pokud používáte `if` - `then` - `throw` styl předběžné podmínky bez jiných smluv, umístěte volání <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> k označení, že všechny předchozí, pokud byly kontroly předběžné podmínky.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Čistotu  
 Všechny metody, které se nazývají v rámci smlouvy musí být čistý; To znamená že nesmí aktualizovat všechny dříve existující stav. Čistý metoda je dovoleno upravit objekty, které byly vytvořeny po vstupu v čistě metoda.  
  
 Kód kontraktu nástroje aktuálně předpokládají, že jsou čistá následující elementy kódu:  
  
-   Metody, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   Typy, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute> (atribut platí pro všechny metody tohoto typu).  
  
-   Vlastnost získat přístupové objekty.  
  
-   Operátory (statických metod, jejichž název začíná "op" a že máte jeden nebo dva parametry a návratový typ není void).  
  
-   Libovolné metody, jejichž plně kvalifikovaný název začíná řetězcem "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" nebo "System.Type".  
  
-   Žádné vyvolání delegáta, za předpokladu, že je opatřená vlastní typ delegáta <xref:System.Diagnostics.Contracts.PureAttribute>. Typy delegáta <xref:System.Predicate%601?displayProperty=nameWithType> a <xref:System.Comparison%601?displayProperty=nameWithType> jsou považovány za čistý.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Viditelnost  
 Všichni členové uvedených ve smlouvě musí být viditelné jako metodu, ve kterém se zobrazí. Například soukromé pole nelze v uvést předpokladem pro veřejná metoda; klienty nelze ověřit takovou smlouvu, než se volat metodu. Ale pokud je označené pole <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, je vyloučit z těchto pravidel.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití kontrakty kódu.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
