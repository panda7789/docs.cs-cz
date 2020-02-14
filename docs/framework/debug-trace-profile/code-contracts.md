---
title: Kontrakty kódu
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: b60f992cf9d934ed622c89a49c491a80377fb6fe
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216717"
---
# <a name="code-contracts"></a>Kontrakty kódu

Kontrakty kódu poskytují způsob, jak určit předběžné podmínky, následné podmínky a invariantní objektů ve vašem kódu. Předběžné podmínky jsou požadavky, které musí být splněny při zadávání metody nebo vlastnosti. Následné podmínky popisují očekávání v době ukončení metody nebo kódu vlastnosti. Invariantní objekty popisují očekávaný stav pro třídu, která je v dobrém stavu.

Kontrakty kódu zahrnují třídy pro označování kódu, statický analyzátor pro analýzu v době kompilace a analyzátor modulu runtime. Třídy pro kontrakty kódu lze nalézt v oboru názvů <xref:System.Diagnostics.Contracts>.

Mezi výhody kontraktů kódu patří následující:

- Vylepšené testování: smlouvy o kódu poskytují statické ověřování kontraktů, kontrolu za běhu a generování dokumentace.

- Automatické testování nástrojů: kontrakty kódu můžete použít ke generování smysluplných testů jednotek, a to filtrováním nevýznamných testovacích argumentů, které nesplňují předpoklady.

- Statické ověření: statická kontrola se může rozhodnout, jestli nedošlo k narušení kontraktu bez spuštění programu. Kontroluje implicitní kontrakty, jako jsou například odkazy na hodnoty null a hranice pole a explicitní kontrakty.

- Referenční dokumentace: generátor dokumentace rozšiřuje stávající soubory dokumentace XML o informace o kontraktech. K dispozici jsou také šablony stylů, které lze použít s [Sandcastle](https://github.com/EWSoftware/SHFB) , aby vygenerované stránky dokumentace měly oddíly smluv.

Všechny jazyky .NET Framework můžou okamžitě využít výhod smluv. Nemusíte psát speciální analyzátor nebo kompilátor. Doplněk sady Visual Studio umožňuje určit úroveň analýzy kontraktu kódu, který se má provést. Analyzátory si můžou ověřit, jestli jsou kontrakty ve správném formátu (kontrola typu a překlad názvů), a můžou vytvořit zkompilovanou formu smluv ve formátu MSIL (Microsoft Intermediate Language). Kontrakty vytváření v aplikaci Visual Studio umožňují využít standardní technologii IntelliSense poskytovanou nástrojem.

Většina metod ve třídě smlouvy je podmíněně zkompilována; To znamená, že kompilátor emituje volání těchto metod pouze v případě, že definujete speciální symbol CONTRACTS_FULL pomocí direktivy `#define`. CONTRACTS_FULL umožňuje psát smlouvy v kódu bez použití direktiv `#ifdef`. můžete vydávat různá buildy, některé se smlouvou a některé bez.

Nástroje a podrobné pokyny k používání kontraktů kódu najdete v tématu [kontrakty kódu](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) na webu Visual Studio Marketplace.

## <a name="preconditions"></a>Předběžné podmínky

Předběžné podmínky můžete vyjádřit pomocí metody <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType>. Předběžné podmínky určují stav při vyvolání metody. Obvykle se používají k zadání platných hodnot parametrů. Všechny členy, kteří jsou uvedeni v předběžných podmínkách, musí být alespoň tak přístupné jako samotná metoda; v opačném případě nemusí být předběžná podmínka srozumitelná všem volajícím metody. Podmínka nesmí mít žádné vedlejší účinky. Chování při neúspěšných předběžných podmínkách za běhu je určeno analyzátorem modulu runtime.

Například následující předběžná podmínka vyjadřuje, že parametr `x` nesmí mít hodnotu null.

```csharp
Contract.Requires(x != null);
```

Pokud váš kód musí vyvolat určitou výjimku při selhání předběžné podmínky, můžete použít obecné přetížení <xref:System.Diagnostics.Contracts.Contract.Requires%2A> následujícím způsobem.

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a>Starší verze vyžadují příkazy

Většina kódu obsahuje několik ověření parametrů ve formě `if`-`then`-kódu `throw`. Nástroje kontraktu tyto příkazy rozpoznají jako předpoklady v následujících případech:

- Příkazy se zobrazí před všemi ostatními příkazy v metodě.

- Celá sada takových příkazů je následována explicitním voláním <xref:System.Diagnostics.Contracts.Contract> metody, například voláním metody <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>nebo <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>.

Pokud se v tomto formuláři zobrazí `if`-`then`-příkazy `throw`, nástroj je rozpoznává jako příkazy starší verze `requires`. Pokud `if`-`then`-`throw` sekvence žádné jiné smlouvy, ukončete kód pomocí metody <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType>.

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

Všimněte si, že podmínka v předchozím testu je předběžnou podmínkou. (Skutečná podmínka by byla `x != null`.) Předběžná podmínka typu negace je vysoce omezená: musí být zapsaná, jak je znázorněno v předchozím příkladu; To znamená, že by neměl obsahovat žádné klauzule `else` a tělo klauzule `then` musí být jeden `throw` příkaz. Test `if` podléhá pravidlům čistoty i viditelnosti (viz [pokyny pro použití](#usage_guidelines)), ale výraz `throw` se vztahuje pouze na pravidla čistoty. Nicméně typ vyvolané výjimky musí být viditelný jako metoda, ve které se kontrakt vyskytuje.

## <a name="postconditions"></a>Následné podmínky

Následné podmínky jsou kontrakty pro stav metody, když se ukončí. Následná podmínka je kontrolován těsně před ukončením metody. Chování za běhu neúspěšného následné podmínky je určeno analyzátorem runtime.

Na rozdíl od předběžných podmínek může následné podmínky odkazovat na členy s méně viditelností. Klient nemusí být schopen pochopit nebo využít některé informace vyjádřené následná podmínka pomocí privátního stavu, ale nemá vliv na schopnost klienta používat metodu správně.

### <a name="standard-postconditions"></a>Následné podmínky úrovně Standard

Můžete vyjádřit standardní následné podmínky pomocí metody <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>. Následné podmínky vyjadřuje podmínku, která musí být `true` při normálním ukončení metody.

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a>Výjimečný následné podmínky

Výjimečné následné podmínky jsou následné podmínky, které by měly být `true`, když je konkrétní výjimka vyvolána metodou. Tyto následné podmínky můžete zadat pomocí metody <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType>, jak ukazuje následující příklad.

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

Argument je podmínka, která musí být `true` vždy, když je vyvolána výjimka, která je podtypem `T`.

Existují některé typy výjimek, které je obtížné použít ve výjimečných následná podmínka. Například použití typu <xref:System.Exception> pro `T` vyžaduje metodu pro zaručení podmínky bez ohledu na typ výjimky, která je vyvolána, i v případě, že se jedná o přetečení zásobníku nebo jiná neproveditelná výjimka. Měli byste použít výjimečnou následné podmínky pouze pro konkrétní výjimky, které mohou být vyvolány při volání člena, například když je vyvolána <xref:System.InvalidTimeZoneException> pro volání metody <xref:System.TimeZoneInfo>.

### <a name="special-postconditions"></a>Speciální následné podmínky

V rámci následné podmínky lze použít následující metody:

- Můžete odkazovat na návratové hodnoty metody v následné podmínky pomocí výrazu `Contract.Result<T>()`, kde `T` je nahrazen návratovým typem metody. Pokud kompilátor nemůže odvodit typ, je nutné jej explicitně poskytnout. C# Kompilátor například nemůže odvodit typy pro metody, které neberou žádné argumenty, takže vyžaduje následující následná podmínka `Contract.Ensures(0 <Contract.Result<int>())`: metody s návratovým typem `void` nemůže odkazovat na `Contract.Result<T>()` ve svých následné podmínky.

- Hodnota představení v následná podmínka odkazuje na hodnotu výrazu na začátku metody nebo vlastnosti. Používá výraz `Contract.OldValue<T>(e)`, kde `T` je typ `e`. Argument obecného typu můžete vynechat vždy, když kompilátor dokáže odvodit svůj typ. (Například C# kompilátor vždy odvodí typ, protože přebírá argument.) Existuje několik omezení na to, co se může stát v `e` a kontexty, ve kterých se může zobrazit starý výraz. Starý výraz nemůže obsahovat jiný starý výraz. Co je důležité, Starý výraz musí odkazovat na hodnotu, která existovala ve stavu předběžné podmínky metody. Jinými slovy, musí být výraz, který lze vyhodnotit, pokud je předběžná podmínka metody `true`. Tady je několik instancí tohoto pravidla.

  - Hodnota musí existovat ve stavu předběžné podmínky metody. Aby bylo možné odkazovat na pole v objektu, předběžné podmínky musí zaručit, že objekt je vždycky null.

  - Nejde odkazovat na návratovou hodnotu metody ve starém výrazu:

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - Nejde odkazovat na parametry `out` ve starém výrazu.

  - Starý výraz nemůže být závislý na vázané proměnné kvantifikátoru, pokud rozsah kvantifikátoru závisí na návratové hodnotě metody:

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - Starý výraz nemůže odkazovat na parametr anonymního delegáta ve <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A> volání, pokud se nepoužívá jako indexer nebo argument pro volání metody:

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - V těle anonymního delegáta se nemůže vyskytovat starý výraz, pokud hodnota starého výrazu závisí na jakémkoli z parametrů anonymního delegáta, pokud anonymní delegát není argumentem metody <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> nebo <xref:System.Diagnostics.Contracts.Contract.Exists%2A>:

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - parametry `Out` prezentují problém, protože kontrakty se zobrazují před tělem metody a většina kompilátorů nepovoluje odkazy na `out` parametrů v následné podmínky. Chcete-li tento problém vyřešit, třída <xref:System.Diagnostics.Contracts.Contract> poskytuje metodu <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A>, která umožňuje následná podmínka na základě parametru `out`.

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      Stejně jako u metody <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> můžete vynechat parametr obecného typu, kdykoli kompilátor dokáže odvodit svůj typ. Přepis kontraktu nahrazuje volání metody hodnotou parametru `out`. Metoda <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> se může vyskytovat pouze v následné podmínky. Argumentem metody musí být parametr `out` nebo pole struktury `out` parametr. Ta je užitečná také při odkazování na pole v následná podmínka konstruktoru struktury.

      > [!NOTE]
      > V současné době nástroje pro analýzu kontraktů kódu nekontrolují, jestli jsou parametry `out` správně inicializované a neodpovídají jejich zmínkám v následná podmínka. Proto v předchozím příkladu, pokud řádek po kontraktu použil hodnotu `x` namísto přiřazení celého čísla, kompilátor nevydá správnou chybu. Nicméně v sestavení, kde není definován symbol preprocesoru CONTRACTS_FULL (takové sestavení pro vydání ASA), kompilátor vydá chybu.

## <a name="invariants"></a>Invariantní

Invariantní objektu jsou podmínky, které by měly platit pro každou instanci třídy vždy, když je objekt viditelný pro klienta. Vyjadřují podmínky, za kterých se objekt považuje za správný.

Invariantní metody jsou označeny příznakem atributu <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute>. Invariantní metody nesmí obsahovat žádný kód s výjimkou sekvence volání metody <xref:System.Diagnostics.Contracts.Contract.Invariant%2A>, každý z nich určuje jednotlivé invariantní, jak je znázorněno v následujícím příkladu.

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

Invariantní jsou podmíněně definované symbolem preprocesoru CONTRACTS_FULL. Během kontroly za běhu jsou nevarianty kontrolovány na konci každé veřejné metody. Pokud invariantní zmiňuje veřejnou metodu ve stejné třídě, invariantní kontroly, které by normálně probíhaly na konci této veřejné metody, jsou zakázané. Místo toho je tato kontrolu provedena pouze na konci nejvzdálenějšího volání metody této třídy. K tomu dojde také v případě, že je třída znovu zadána z důvodu volání metody v jiné třídě. Invariantní nejsou kontrolovány pro finalizační metodu objektu a implementaci <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a>Pokyny k používání

### <a name="contract-ordering"></a>Pořadí smluv

Následující tabulka ukazuje pořadí prvků, které byste měli použít při psaní kontraktů metod.

|`If-then-throw statements`|Zpětně kompatibilní veřejné předběžné podmínky|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Všechny veřejné podmínky.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny veřejné (normální) následné podmínky.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Všechny veřejné výjimečné následné podmínky.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Všechny soukromé/interní (normální) následné podmínky.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Všechny soukromé/interní výjimečné následné podmínky.|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Pokud používáte `if`-`then`-`throw` předběžné podmínky bez jakýchkoli jiných kontraktů, umístěte volání do <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>, abyste označili, že všechny předchozí kontroly v případě, že se kontrolují předpoklady.|

<a name="purity"></a>

### <a name="purity"></a>Čistotě

Všechny metody, které jsou volány v rámci kontraktu, musí být čisté; To znamená, že nesmí aktualizovat žádný stávající stav. Metoda Pure může upravovat objekty, které byly vytvořeny po vstupu do metody Pure.

Nástroje pro kontrakt kódu aktuálně předpokládají, že následující prvky kódu jsou čisté:

- Metody, které jsou označeny <xref:System.Diagnostics.Contracts.PureAttribute>.

- Typy, které jsou označeny <xref:System.Diagnostics.Contracts.PureAttribute> (atribut platí pro všechny metody typu).

- Přistupující objekty pro získání vlastnosti

- Operátory (statické metody, jejichž názvy začínají na "op" a které mají jeden nebo dva parametry a návratový typ jiný než void).

- Libovolná metoda, jejíž plně kvalifikovaný název začíná řetězcem "System. Diagnostics. Contracts. Contract", "System. String", "System. IO. Path" nebo "System. Type".

- Jakýkoli vyvolaný delegát za předpokladu, že samotný typ delegáta má atribut <xref:System.Diagnostics.Contracts.PureAttribute>. Typy delegátů <xref:System.Predicate%601?displayProperty=nameWithType> a <xref:System.Comparison%601?displayProperty=nameWithType> jsou považovány za čistě.

<a name="visibility"></a>

### <a name="visibility"></a>Viditelnost

Všichni členové uvedení ve kontraktu musí být alespoň tak viditelné jako metoda, ve které se vyskytují. Například soukromé pole nelze uvést v předběžné podmínce pro veřejnou metodu; Klienti nemohou takový kontrakt ověřit před voláním metody. Pokud je však pole označeno jako <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, je z těchto pravidel vyloučeno.

## <a name="example"></a>Příklad

Následující příklad ukazuje použití kontraktů kódu.

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
