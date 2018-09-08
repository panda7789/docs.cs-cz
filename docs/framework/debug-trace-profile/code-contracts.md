---
title: Kontrakty kódu
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7f7a779cc10b32d66a184107359b502cf094979
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222120"
---
# <a name="code-contracts"></a>Kontrakty kódu
Kontrakty kódu poskytují způsob, jak určit předpoklady, vstupních a výstupních objekt podmínek ve vašem kódu. Předběžné podmínky jsou požadavky, které musí být splněny, při zadávání metody nebo vlastnosti. Vstupních popisují očekávání v době, kdy kód metody nebo vlastnosti se ukončí. Objekt výstupních podmínek popisují očekávaný stav pro třídu, která je v dobrém stavu.  
  
 Kontrakty kódu zahrnují třídy pro označení kódu, statické analyzátor pro analýzu v době kompilace a modulu runtime analyzátor. Třídy pro kontrakty kódu najdete v <xref:System.Diagnostics.Contracts> oboru názvů.  
  
 Kontrakty kódu mezi výhody patří následující:  
  
-   Vylepšené testování: kontrakty kódu poskytovat statické ověření kontraktu, kontrola modulu runtime a generování dokumentace.  
  
-   Automatické testovací nástroje: kontrakty kódu můžete použít ke generování lépe vystihuje testování částí filtrováním význam testu argumenty, které nesplňují podmínky.  
  
-   Statické ověření: statické kontroly můžete rozhodnout, jestli se porušení smlouvy bez spuštění programu. Zkontroluje pro implicitní smlouvy, jako je například null přístupů přes ukazatel a pole hranice a explicitní smluv.  
  
-   Referenční dokumentace: dokumentace generátor rozšiřuje existující soubory dokumentace XML s informacemi o smlouvě. Existují také šablony stylů, které lze použít s [Sandcastle](https://github.com/EWSoftware/SHFB) tak, aby stránky dokumentace generovaného kontraktu oddíly.  
  
 Všechny jazyky rozhraní .NET Framework mohou okamžitě využívat smluv; nemusíte psát speciální analyzátoru nebo kompilátoru. Doplněk sady Visual Studio vám umožní určit úroveň smlouvy analýzy kódu mají být provedeny. Analyzátory můžou ověřte, zda smlouvách ve správném formátu (kontrolu typu a překlad názvů) a může vytvářet kompilovaný formy smluv ve formátu Microsoft intermediate language (MSIL). Vytváření kontraktů v sadě Visual Studio vám umožní využít standardní informace IntelliSense poskytované nástrojem.  
  
 Většina metod ve třídě smlouvy jsou podmíněně kompilována; To znamená, kompilátor vydává volání těchto metod pouze v případě, že definujete pomocí speciální symbol CONTRACTS_FULL, `#define` směrnice. CONTRACTS_FULL umožňuje zapisovat smlouvy v kódu bez použití `#ifdef` direktivy; můžete vytvářet různé verze, některé u kontraktů a některé bez.  
  
 Nástroje a podrobné pokyny k používání kontrakty kódu najdete v tématu [kontrakty kódu](https://go.microsoft.com/fwlink/?LinkId=152461) na webu MSDN devlabs s názvem.  
  
## <a name="preconditions"></a>Předběžné podmínky  
 Předběžné podmínky můžete vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> metody. Předběžné podmínky určete stav při vyvolání metody. Obvykle se používají k určení platné hodnoty parametrů. Všechny členy, které jsou uvedené v předběžných podmínkách musí být přinejmenším stejně dostupná jako metodu. v opačném případě nemusí být předpoklad srozumitelné všichni volající metody. Podmínka musí mít žádné vedlejší účinky. Analyzátor modul runtime určuje chování za běhu selhání předběžné podmínky.  
  
 Například následující předpoklad vyjadřuje tento parametr `x` musí mít hodnotu null.  
  
 `Contract.Requires( x != null );`  
  
 Pokud váš kód musí vyvolat zvláštní výjimku při selhání předběžné podmínky, můžete použít obecné přetížení <xref:System.Diagnostics.Contracts.Contract.Requires%2A> následujícím způsobem.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Starší verze #requires.  
 Většinu kódu obsahuje nějaké ověření parametru v podobě `if` - `then` - `throw` kódu. Nástroje pro kontrakt rozpoznat tyto příkazy jako předpoklady v následujících případech:  
  
-   Příkazy nacházet před všechny ostatní příkazy v metodě.  
  
-   Celá sada těchto příkazů je následována explicitní <xref:System.Diagnostics.Contracts.Contract> volání metody, jako je například volání <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, nebo <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> metody.  
  
 Když `if` - `then` - `throw` příkazy se zobrazí v tomto formuláři nástroje rozpoznat jako starší verze `requires` příkazy. Pokud žádné jiné smlouvy, postupujte podle `if` - `then` - `throw` pořadí, -end kód <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> metoda.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Všimněte si, že je podmínka v předchozím testu negovaným čítačem předběžné podmínky. (Skutečné Předběžná podmínka by `x != null`.) Předpokladem negovaným čítačem je vysoce omezenou: musí být napsaná, jak je znázorněno v předchozím příkladu; To znamená, měl by obsahovat žádné `else` klauzule a text `then` klauzule musí být jediný `throw` příkazu. `if` Test je v souladu s čistoty a viditelnost pravidla (naleznete v tématu [pokyny k používání](#usage_guidelines)), ale `throw` výraz se vztahuje pouze na čistotě pravidla. Typ výjimky vyvolané však musí být jako viditelný jako způsob, ve kterém dochází kontrakt.  
  
## <a name="postconditions"></a>Vstupních  
 Vstupních jsou kontrakty pro stav metody při jeho ukončení. Neplatná následná se kontroluje jenom před ukončením metody. Chování za běhu se nezdařilo vstupních určuje analyzátor modulu runtime.  
  
 Na rozdíl od předběžné podmínky může následným podmínkám odkazovat na členy s méně viditelnost. Klient nemusí být schopen porozumět nebo učiňte použít některé informace vyjádřené neplatná následná používání soukromý stav, ale to nemá vliv na schopnost klienta pomocí metody správně.  
  
### <a name="standard-postconditions"></a>Standardní vstupních  
 Standardní vstupních můžete vyjádřit pomocí <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> metody. Vstupních express podmínku, která musí být `true` při normálním ukončení metody.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Mimořádné vstupních  
 Mimořádné vstupních jsou následným podmínkám, které by měly být `true` při konkrétní výjimka je vyvolána metoda. Určíte tyto vstupních pomocí <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> metody, stejně jako v následujícím příkladu.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Argument je podmínka, která musí být `true` pokaždé, když výjimka, která je podtypem typu `T` je vyvolána výjimka.  
  
 Existují některé typy výjimek, které je obtížné pro použití v výjimečných neplatná následná. Například pomocí typu <xref:System.Exception> pro `T` vyžaduje metodu zajistit podmínku bez ohledu na typ výjimky, která je vyvolána, i když je přetečení zásobníku nebo jinou výjimku nemožné řízení. Mimořádné vstupních byste měli použít pouze pro konkrétní výjimky, které by mohla být vyvolána při člen volání, například když <xref:System.InvalidTimeZoneException> , je vyvolána <xref:System.TimeZoneInfo> volání metody.  
  
### <a name="special-postconditions"></a>Speciální vstupních  
 Pouze v rámci vstupních lze použít následující metody:  
  
-   Mohou odkazovat na návratové hodnoty metod ve vstupních pomocí výrazu `Contract.Result<T>()`, kde `T` nahrazuje návratový typ metody. Pokud kompilátor nemůže odvodit typ, je nutné ho zadat explicitně. Například nelze odvodit typy pro metody, které nepřebírají žádné argumenty, takže vyžaduje následující neplatná následná kompilátor jazyka C#: `Contract.Ensures(0 <Contract.Result<int>())` metody s návratovým typem `void` nemůže odkazovat na `Contract.Result<T>()` v jejich následným podmínkám.  
  
-   Hodnotu prestate neplatná následná odkazuje na hodnotu výrazu na začátku metody nebo vlastnosti. Používá výraz `Contract.OldValue<T>(e)`, kde `T` je typ `e`. Pokaždé, když je kompilátor může odvodit typ, můžete vynechat argument obecného typu. (Například kompilátor jazyka C# vždy odvodí typ protože přebírá argument.) Existuje několik omezení na co může dojít v `e` a kontext, ve kterých může zobrazit staré výrazu. Původní výraz nemůže obsahovat jiný výraz staré. Co je nejdůležitější staré výrazu musí odkazovat na hodnotu, která byla uložena ve stavu Předběžná podmínka metody. Jinými slovy, musí být výraz, který může být vyhodnocen, dokud je předběžná podmínka metody `true`. Tady je několik instancí tohoto pravidla.  
  
    -   Hodnota musí existovat ve stavu Předběžná podmínka metody. Aby bylo možné odkazovat pole v objektu, předběžné podmínky musí zaručit, že je vždy nenulový.  
  
    -   Nelze se odkazovat na návratovou hodnotu metody v původní výraz:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   Nelze se odkazovat na `out` parametry ve výrazu staré.  
  
    -   Původní výraz nemůže záviset na vazby proměnné kvantifikátor rozsah kvantifikátor závislých na návratovou hodnotu metody:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Původní výraz nemůže odkazovat na parametr anonymního delegáta v <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> volat, pokud se používá jako indexer nebo argument volání metody:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Původní výraz nelze provést, v těle anonymního delegáta hodnotou staré výrazu závislých na některý z parametrů anonymního delegáta, pokud anonymního delegáta je argument <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> metody:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out` Parametry představovat problém, protože kontrakty předcházet tělo metody a většina kompilátorů nejsou povoleny odkazy na `out` ve vstupních parametrů. Pro vyřešení tohoto problému <xref:System.Diagnostics.Contracts.Contract> třída poskytuje <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> metodu, která umožňuje neplatná následná na základě `out` parametru.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         Stejně jako u <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> metodu, můžete vynechat parametr obecného typu pokaždé, když je kompilátor může odvodit typ. Kontrakt RW nahradí volání metody s hodnotou `out` parametru. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Metoda může vyskytovat jenom ve vstupních. Argument metody musí být `out` parametru nebo pole struktury `out` parametru. Je také užitečná při odkazu na pole v neplatná následná struktura konstruktoru.  
  
        > [!NOTE]
        >  V současné době nástrojů pro analýzu kódu kontraktu nekontrolují, zda `out` parametry jsou inicializovány správně a jejich uvedením v neplatná následná ignorovat. Proto v předchozím příkladu, pokud řádku po kontrakt použili hodnotu `x` namísto celého čísla přiřazení k němu, kompilátor by vystavovat správné chyby. Ale na sestavení, ve kterém je preprocesoru symbol CONTRACTS_FULL není definována (takové asa sestavení pro vydání), kompilátor vygeneruje chybu.  
  
## <a name="invariants"></a>Výstupních podmínek  
 Objekt výstupních podmínek jsou podmínky, které by měl mít hodnotu true pro každou instanci třídy pokaždé, když je viditelné pro klienta. Vyjadřují podmínky, za kterých objekt se považuje za správné.  
  
 Invariantní metody jsou označeny se označené <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> atribut. Invariantní metody musejí obsahovat žádný kód s výjimkou pořadí volání <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> metoda jednotlivé invariantní, z nichž každý určuje, jak je znázorněno v následujícím příkladu.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 Výstupních podmínek jsou definovány podmíněně preprocesoru symbol CONTRACTS_FULL. Během kontroly za běhu, jsou kontrolovány výstupních podmínek na konci každé veřejné metody. Pokud invariantní uvádí veřejnou metodu ve stejné třídě, je zakázané invariantní zkontrolujte, jestli by normálně mohlo dojít na konci této veřejné metody. Místo toho kontrola probíhá pouze na konci volání vnější metody dané třídy. Také se to stane, když je třída opětovný vstup z důvodu volání metody na jinou třídu. Výstupních podmínek se kontroluje finalizační metodu objektu a <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementace.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Pokyny k používání  
  
### <a name="contract-ordering"></a>Kontrakt řazení  
 V následující tabulce jsou uvedeny pořadí prvků, které byste měli použít při zápisu kontrakty – metoda.  
  
|`If-then-throw statements`|Zpětně kompatibilní veřejné předběžné podmínky|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Všechny veřejné předběžné podmínky.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny veřejné vstupních (normální).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Všechny veřejné výjimečných následným podmínkám.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny privátní nebo interní vstupních (normální).|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Privátní nebo interní výjimečných vstupních.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Pokud používáte `if` - `then` - `throw` stylu předběžné podmínky bez jiných smluv, umístěte volání <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> označuje, že všechny předchozí, pokud jsou předběžné podmínky kontroly.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Čistota  
 Všechny metody, které jsou volány v rámci smlouvy musí být čistě; To znamená se nesmí aktualizovat žádné stávající stav. Čistě metoda může upravit objekty, které byly vytvořeny po vstupu do čistého metody.  
  
 Kód kontraktu nástroje aktuálně předpokládají, že jsou čistě následujících prvků kódu:  
  
-   Metody, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   Typy, které jsou označené <xref:System.Diagnostics.Contracts.PureAttribute> (atribut platí pro všechny typy metod).  
  
-   Přístupové objekty get vlastnosti.  
  
-   Operátory (statické metody, jejichž názvy začínají písmenem "op" a že máte jeden nebo dva parametry a návratový typ jiný než void).  
  
-   Jakoukoli metodu, jejíž plně kvalifikovaný název začíná řetězcem "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" nebo "System.Type".  
  
-   Některé vyvolání delegáta, za předpokladu, že má atribut samotného typu delegáta <xref:System.Diagnostics.Contracts.PureAttribute>. Typy delegátů <xref:System.Predicate%601?displayProperty=nameWithType> a <xref:System.Comparison%601?displayProperty=nameWithType> jsou považovány za čistě.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Viditelnost  
 Všechny členy, které jsou uvedené ve smlouvě musí být minimálně viditelná jako způsob, ve kterém jsou zobrazeny. Například soukromé pole nelze uvést v předběžné podmínce pro veřejnou metodu; klienty nelze ověřit takovou smlouvu před volají metodu. Ale pokud pole je označeno <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, se vyjímá z těchto pravidel.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití kontrakty kódu.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
