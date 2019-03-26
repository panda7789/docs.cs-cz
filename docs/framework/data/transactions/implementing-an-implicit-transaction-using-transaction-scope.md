---
title: Implementace implicitní transakce s využitím oboru transakcí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
ms.openlocfilehash: fccfa5b0ef531ac8ecc869d7a248bb4f43a55d2c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375243"
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>Implementace implicitní transakce s využitím oboru transakcí
<xref:System.Transactions.TransactionScope> Třída poskytuje jednoduchý způsob, jak označit bloku kódu jako účasti na transakci, aniž by bylo nutné k interakci se vlastní transakce. Obor transakce můžete vybrat a spravovat okolí transakce automaticky. Z důvodu jeho snadno použitelných a efektivitu, je doporučeno používat <xref:System.Transactions.TransactionScope> třídy při vývoji aplikace transakce.  
  
 Kromě toho není nutné zařazení prostředky explicitně s transakcí. Jakékoli <xref:System.Transactions> můžete zjišťovat existenci transakci okolí Autor oboru a automaticky zařazení správce prostředků (například SQL Server 2005).  
  
## <a name="creating-a-transaction-scope"></a>Vytváření oboru transakce  
 Následující příklad ukazuje, jednoduché použití <xref:System.Transactions.TransactionScope> třídy.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 Obor transakce je spuštěn, jakmile vytvoříte nový <xref:System.Transactions.TransactionScope> objektu.  Jak je znázorněno v ukázce kódu, je doporučeno vytvořit oborů s **pomocí** příkazu. **Pomocí** prohlášení je k dispozici v C# a v jazyce Visual Basic a funguje podobně jako **try... finally** blok k Ujistěte se, že je správně odstraněna oboru.  
  
 Když vytváříte instance <xref:System.Transactions.TransactionScope>, určuje správce transakcí, které transakci se účastnit programu. Poté, co bylo zjištěno, oboru vždy se účastní dané transakce. Je založena na dva faktory: zda okolí transakce je přítomen a hodnota **TransactionScopeOption** parametr v konstruktoru. Okolí transakce je transakce, ve kterém se spustí váš kód. Odkaz na okolí transakce můžete získat voláním statické <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> vlastnost <xref:System.Transactions.Transaction> třídy. Další informace o tom, jak tento parametr se používá, najdete v článku [správa toku transakce pomocí TransactionScopeOption](#ManageTxFlow) části tohoto tématu.  
  
## <a name="completing-a-transaction-scope"></a>Dokončení rozsahu transakce  
 Pokud vaše aplikace dokončí všechny pracovní chce provést v transakci, měli byste zavolat <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> metoda pouze jednou informovat správce transakcí, že je přijatelné potvrzení transakce. Je velmi vhodné umístit volání <xref:System.Transactions.TransactionScope.Complete%2A> jako poslední příkaz v **pomocí** bloku.  
  
 Selhání tuto metodu volat zruší transakce, protože správce transakcí interpretuje jako selhání systému nebo ekvivalent výjimka vyvolána v rámci oboru transakce. Však voláním této metody není zaručit, že transakce probíhal v každé zemi být potvrzeny. Je pouze způsob, jak o tom bude informovat správce transakcí stavu. Po volání <xref:System.Transactions.TransactionScope.Complete%2A> v případě metody okolí transakce může již přistupovat pomocí <xref:System.Transactions.Transaction.Current%2A> vlastnost a pokusili, výsledkem bude výjimky.  
  
 Pokud <xref:System.Transactions.TransactionScope> objektu, původně vytvořil transakci skutečná práce potvrzování transakcí správcem transakcí dojde poté, co poslední řádek kódu **pomocí** bloku. Pokud nebyl vytvořen transakce, potvrzení dochází, pokud <xref:System.Transactions.CommittableTransaction.Commit%2A> je volána metodou vlastníka <xref:System.Transactions.CommittableTransaction> objektu. V tomto okamžiku správce transakcí volá prostředek manažery a informovat je na zápis nebo vrácení zpět, podle toho, jestli <xref:System.Transactions.TransactionScope.Complete%2A> byla volána metoda <xref:System.Transactions.TransactionScope> objektu.  
  
 **Pomocí** příkaz zajistí, že <xref:System.Transactions.TransactionScope.Dispose%2A> metodu <xref:System.Transactions.TransactionScope> objekt, se nazývá i v případě, že dojde k výjimce. <xref:System.Transactions.TransactionScope.Dispose%2A> Metoda označuje konec rozsahu transakce. Výjimky, k nimž došlo po volání této metody nemusí mít vliv na transakci. Tato metoda také obnoví okolí transakci ji předchozího stavu.  
  
 Objekt <xref:System.Transactions.TransactionAbortedException> je vyvolána, pokud obor vytvoří transakce a transakce je přerušená. Objekt <xref:System.Transactions.TransactionInDoubtException> je vyvolána, pokud správce transakcí nelze dosáhnout rozhodnutí o potvrzení. Pokud transakce není vyvolána žádná výjimka.  
  
## <a name="rolling-back-a-transaction"></a>Vrácení transakce zpět  
 Pokud byste chtěli vrácení zpět transakcí, neměli by jste volat <xref:System.Transactions.TransactionScope.Complete%2A> metody v rozsahu transakce. Například může vyvolat výjimku v rámci oboru. Transakce, ve kterém je součástí bude vrácena zpět.  
  
## <a name="ManageTxFlow"></a> Správa toku transakce pomocí TransactionScopeOption  
 Obor transakcí, které mohou být vnořené voláním metody, která používá <xref:System.Transactions.TransactionScope> z v rámci metody, která používá vlastní rozsah, jako je tomu u `RootMethod` metodu v následujícím příkladu  
  
```csharp  
void RootMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          SomeMethod();  
          scope.Complete();  
     }  
}  
  
void SomeMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          scope.Complete();  
     }  
}  
```  
  
 Obor navrchu transakce se nazývá kořenového oboru.  
  
 <xref:System.Transactions.TransactionScope> Třída poskytuje několik přetížených konstruktorů, které přijímají výčet typu <xref:System.Transactions.TransactionScopeOption>, která definuje transakční chování oboru.  
  
 Objekt <xref:System.Transactions.TransactionScope> objekt má tři možnosti:  
  
-   Připojte se k okolí transakce nebo vytvořit novou, pokud neexistuje.  
  
-   Být nových kořenový obor, to znamená, spusťte novou transakci a mají být nové okolí transakce v rámci vlastní rozsah transakce.  
  
-   Neúčastní transakcí vůbec. V důsledku není žádná okolí transakce.  
  
 Pokud dojde k vytvoření oboru s <xref:System.Transactions.TransactionScopeOption.Required>a okolí transakce je přítomen, oboru spojí dané transakce. Je-li na druhé straně není žádná okolí transakce, pak oboru vytvoří novou transakci a Staňte se kořenového oboru. Jedná se o výchozí hodnotu. Při <xref:System.Transactions.TransactionScopeOption.Required> se používá, kód v rámci oboru není nutné, aby chovat odlišně, zda je kořenový adresář nebo právě připojuje okolí transakce. Měla pracovat stejně jako v obou případech.  
  
 Pokud dojde k vytvoření oboru s <xref:System.Transactions.TransactionScopeOption.RequiresNew>, je vždy kořenový oboru. Spustí novou transakci a jeho transakce se změní na nové okolí transakce v rámci oboru.  
  
 Pokud dojde k vytvoření oboru s <xref:System.Transactions.TransactionScopeOption.Suppress>, se nikdy účastní v transakci, bez ohledu na to zda okolí transakce je k dispozici. Obor vytvořena s Tato hodnota vždy mít **null** jako jeho okolí transakce.  
  
 V následující tabulce je uveden výše uvedených možností.  
  
|TransactionScopeOption|Okolí transakce|Rozsah podílí na|  
|----------------------------|-------------------------|-----------------------------|  
|Požadováno|Ne|Nová transakce (bude kořenového adresáře)|  
|Požaduje novou|Ne|Nová transakce (bude kořenového adresáře)|  
|Potlačit|Ne|Žádná transakce|  
|Požadováno|Ano|Okolí transakce|  
|Požaduje novou|Ano|Nová transakce (bude kořenového adresáře)|  
|Potlačit|Ano|Žádná transakce|  
  
 Když <xref:System.Transactions.TransactionScope> objekt spojí existující okolí transakce, uvolnění objektu oboru nesmí končit transakce, pokud obor zruší transakce. Pokud okolí transakce byla vytvořena pomocí kořenového oboru, pouze v případě, že je kořenový obor odstraněn, nemá <xref:System.Transactions.CommittableTransaction.Commit%2A> zavolána v transakci. Pokud transakce byla vytvořena ručně, transakce končí, když je buď bylo přerušeno nebo potvrzené jeho tvůrcem.  
  
 Následující příklad ukazuje <xref:System.Transactions.TransactionScope> objekt, který vytvoří tři vnořených objektů s rozsahem, každá instance s jiným <xref:System.Transactions.TransactionScopeOption> hodnotu.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())   
//Default is Required   
{   
     using(TransactionScope scope2 = new   
      TransactionScope(TransactionScopeOption.Required))   
     {  
     ...  
     }   
  
     using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))   
     {  
     ...  
     }   
  
     using(TransactionScope scope4 = new   
        TransactionScope(TransactionScopeOption.Suppress))   
    {  
     ...  
    }   
}  
```  
  
 Příklad ukazuje bloku kódu, bez jakékoli okolí transakce vytváření nového oboru (`scope1`) s <xref:System.Transactions.TransactionScopeOption.Required>. Rozsah `scope1` je kořenového oboru, který ji vytvoří novou transakci (transakce A) a usnadňuje transakce A okolí transakce. `Scope1` poté vytvoří tři více objektů s jiným <xref:System.Transactions.TransactionScopeOption> hodnotu. Můžete například `scope2` je vytvořen s <xref:System.Transactions.TransactionScopeOption.Required>, a vzhledem k tomu, že existuje okolí transakce, spojení první transakce vytvořené `scope1`. Všimněte si, že `scope3` kořenového oboru novou transakci a že je `scope4` nemá žádné okolí transakce.  
  
 I když ve výchozím nastavení a většinu běžně používá hodnotu <xref:System.Transactions.TransactionScopeOption> je <xref:System.Transactions.TransactionScopeOption.Required>, všechny ostatní hodnoty, má své jedinečné účel.  
  
 <xref:System.Transactions.TransactionScopeOption.Suppress> je užitečné, když chcete zachovat prováděných části kódu a nechcete, aby na zrušení okolí transakce, pokud se nezdaří operace. Například když chcete provádět protokolování nebo auditovat operace, nebo když chcete publikovat události odběratelům bez ohledu na tom, zda váš okolí potvrzení nebo přerušení transakce. Tato hodnota slouží k mít část s kódem netransakční v rámci oboru transakcí, jak je znázorněno v následujícím příkladu.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())  
{  
     try  
     {  
          //Start of non-transactional section   
          using(TransactionScope scope2 = new  
             TransactionScope(TransactionScopeOption.Suppress))  
          {  
               //Do non-transactional work here  
          }  
          //Restores ambient transaction here  
   }  
     catch  
     {}  
   //Rest of scope1  
}  
```  
  
### <a name="voting-inside-a-nested-scope"></a>Hlasování uvnitř vnořené oboru  
 Přestože vnořené oboru se může připojit k okolí transakce kořenového oboru, voláním metody <xref:System.Transactions.TransactionScope.Complete%2A> v oboru vnořené nemá žádný vliv na kořenového oboru. Pouze v případě, že všechny obory z kořenového oboru dolů poslední vnořené oboru hlasovat potvrzení transakce, transakce budou potvrzeny. Není volání <xref:System.Transactions.TransactionScope.Complete%2A> v oboru vnořené bude mít vliv na kořenového oboru jako okolí transakce bude okamžitě ukončeno.  
  
## <a name="setting-the-transactionscope-timeout"></a>Nastavení časového limitu TransactionScope  
 Některé z přetížených konstruktorů z <xref:System.Transactions.TransactionScope> přijmout hodnoty typu <xref:System.TimeSpan>, která se používá k řízení časový limit transakce. Časový limit nastaven na hodnotu nula znamená neomezený časový limit. Neomezený časový limit je užitečné většinou pro ladění, pokud chcete izolovat problém v obchodní logiky krokování kódu jazyka a nechcete, aby transakce, které můžete ladit vypršení časového limitu při pokusu o nalezení problému. Velmi Vyhněte se pomocí hodnoty neomezený časový limit ve všech ostatních případech, protože přepisuje ochranu proti zablokování transakce.  
  
 Obvykle nastavena <xref:System.Transactions.TransactionScope> časový limit na hodnoty jiné než výchozí v obou případech. První je během vývoje, pokud chcete testovat tak, jak vaše aplikace zpracovává přerušené transakce. Nastavením časového limitu na malou hodnotu (například jeden milisekund) způsobit selhání transakce a můžete tak sledovat svůj kód pro zpracování chyb. Druhý případ, ve kterém nastavíte hodnotu menší než výchozí časový limit je v případě, že budete mít dojem, oboru se zabývá konflikty prostředků, výsledkem zablokování. V takovém případě budete chtít přerušení transakce co nejdříve a čekat výchozí časový limit vypršení platnosti.  
  
 Pokud obor spojí okolí transakce, ale Určuje časový limit menší než okolí transakce je nastavena na, nový, kratší časový limit je vynucovat u <xref:System.Transactions.TransactionScope> objekt a obor musí končit v rámci vnořené dobu určenou, nebo je automaticky transakce zrušena. Je-li časový limit vnořené oboru je větší než který okolí transakce, nemá žádný vliv.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>Nastavení zabezpečení na úroveň izolace TransactionScope  
 Některé z přetížených konstruktorů z <xref:System.Transactions.TransactionScope> přijmout strukturu typu <xref:System.Transactions.TransactionOptions> Chcete-li určit úroveň izolace kromě hodnotu časového limitu. Ve výchozím nastavení, provede transakce s nastavena na úroveň izolace <xref:System.Transactions.IsolationLevel.Serializable>. Jiné než výběrem úroveň izolace <xref:System.Transactions.IsolationLevel.Serializable> se obvykle používá pro čtení velkými nároky na výkon systémů. To vyžaduje důkladného porozumění zpracování teorií a sémantika vlastní transakce, problematika souběžnosti a důsledky pro systém konzistence transakcí.  
  
 Kromě toho nejsou všechny správce prostředků nepodporují všechny úrovně izolace a uživatelé mohou zvolit, zda k účasti v transakci na vyšší úrovni než který je nakonfigurován.  
  
 Každou úroveň izolace kromě <xref:System.Transactions.IsolationLevel.Serializable> se nekonzistence vyplývající z jiné transakce přístupu stejné informace. Rozdíl mezi úrovních různé izolace je způsobem, čtení a zápisu uzamčení se používají. Zámek mohou konat pouze v případě, že transakce přistupuje k datům ve Správci zdrojů nebo můžete budou konat, dokud nebude transakce potvrzena nebo zrušena. Je lepší pro propustnost ten konzistence. Dva druhy zámků a dva druhy operací (čtení a zápis) udává čtyři úrovně basic izolace. Další informace naleznete v tématu <xref:System.Transactions.IsolationLevel>.  
  
 Při použití vnořených <xref:System.Transactions.TransactionScope> objekty, musí být nakonfigurován obory všech vnořených používat přesně stejnou úroveň izolace, aby bylo možné připojit se k okolí transakce. Pokud vnořený <xref:System.Transactions.TransactionScope> objekt se pokusí připojit okolí transakce ještě určuje na úroveň izolace jiný <xref:System.ArgumentException> je vyvolána.  
  
## <a name="interop-with-com"></a>Vzájemná funkční spolupráce s modelu COM +  
 Když vytvoříte nový <xref:System.Transactions.TransactionScope> instance, můžete použít <xref:System.Transactions.EnterpriseServicesInteropOption> výčet v jednom z konstruktorů k určení, jak pracovat s modelu COM +. Další informace najdete v části [interoperabilita se službami Enterprise Services a transakcemi COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Transactions.Transaction.Clone%2A>
- <xref:System.Transactions.TransactionScope>
