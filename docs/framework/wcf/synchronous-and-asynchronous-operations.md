---
title: Synchronní a asynchronní operace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143210"
---
# <a name="synchronous-and-asynchronous-operations"></a>Synchronní a asynchronní operace
Toto téma popisuje implementaci a volání operací asynchronní služby.  
  
 Mnoho aplikací volat metody asynchronně, protože umožňuje aplikaci pokračovat v provádění užitečné práce při spuštění volání metody. Služby a klienti WCF (Windows Communication Foundation) se mohou účastnit volání asynchronních operací na dvou různých úrovních aplikace, které poskytují aplikacím WCF ještě větší flexibilitu pro maximalizaci propustnosti vyváženou interaktivitou .  
  
## <a name="types-of-asynchronous-operations"></a>Typy asynchronních operací  
 Všechny smlouvy o poskytování služeb v WCF, bez ohledu na typy parametrů a vrácené hodnoty, použijte atributy WCF k určení konkrétního vzoru výměny zpráv mezi klientem a službou. WCF automaticky směruje příchozí a odchozí zprávy do příslušné operace služby nebo spuštěný kód klienta.  
  
 Klient vlastní pouze servisní smlouvu, která určuje vzor výměny zpráv pro určitou operaci. Klienti mohou nabídnout vývojáři libovolný programovací model, který zvolí, tak dlouho, dokud je dodržen základní vzor výměny zpráv. Stejně tak služby mohou provádět operace jakýmkoli způsobem, pokud je dodržen zadaný vzor zprávy.  
  
 Nezávislost smlouvy o poskytování služeb na implementaci služby nebo klienta umožňuje následující formy asynchronního provádění v aplikacích WCF:  
  
- Klienti mohou vyvolat operace požadavku a odpovědi asynchronně pomocí synchronní výměny zpráv.  
  
- Služby mohou implementovat operaci požadavku a odpovědi asynchronně pomocí synchronní výměny zpráv.  
  
- Výměny zpráv může být jednosměrné, bez ohledu na implementaci klienta nebo služby.  
  
### <a name="suggested-asynchronous-scenarios"></a>Navrhované asynchronní scénáře  
 Použijte asynchronní přístup v implementaci operace služby, pokud implementace služby operace provede blokování volání, jako je například provádění vstupně-va., jako je například provádění vstupně-va. Pokud jste v implementaci asynchronní operace, zkuste volat asynchronní operace a metody rozšířit cestu asynchronní volání co nejvíce. Například volání `BeginOperationTwo()` a `BeginOperationOne()`zevnitř .  
  
- Použijte asynchronní přístup v klientské nebo volající aplikaci v následujících případech:  
  
- Pokud se odvoláváte na operace z aplikace střední vrstvy. (Další informace o těchto scénářích naleznete v tématu [klientské aplikace střední vrstvy](./feature-details/middle-tier-client-applications.md).)  
  
- Pokud vyvoláte operace v rámci ASP.NET stránky, použijte asynchronní stránky.  
  
- Pokud vyvoláváte operace z libovolné aplikace, která je s jedním zřetězením, jako jsou například Windows Forms nebo Windows Presentation Foundation (WPF). Při použití modelu asynchronnívolání založené na událostech je událost výsledku vyvolána ve vlákně uživatelského rozhraní a přidává odezvu do aplikace, aniž byste museli zpracovávat více vláken sami.  
  
- Obecně platí, že pokud máte na výběr mezi synchronní a asynchronní volání, zvolte asynchronní volání.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implementace operace asynchronní služby  
 Asynchronní operace lze implementovat pomocí jedné ze tří následujících metod:  
  
1. Asynchronní vzor založený na úlohách  
  
2. Asynchronní vzor založený na událostech  
  
3. Asynchronní vzor IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Asynchronní vzor založený na úlohách  
 Asynchronní vzor založený na úlohách je upřednostňovaným způsobem implementace asynchronních operací, protože je nejjednodušší a nejpřímější. Chcete-li použít tuto metodu jednoduše implementovat\<operaci služby a zadejte návratový typ úkolu T>, kde T je typ vrácený logickou operací. Například:  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 Operace SampleMethodTaskAsync vrátí\<řetězec úlohy> protože logická operace vrátí řetězec. Další informace o asynchronním vzoru založeném na úlohách naleznete [v tématu Asynchronní vzor založený na úlohách](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
> Při použití asynchronní vzor založený na úlohách T:System.AggregateException může být vyvolána, pokud dojde k výjimce při čekání na dokončení operace. Tato výjimka může nastat u klienta nebo služeb.  
  
#### <a name="event-based-asynchronous-pattern"></a>Asynchronní vzor založený na událostech  
 Služba, která podporuje asynchronní vzorek založený na událostech, bude mít jednu nebo více operací s názvem MethodNameAsync. Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně. Třída může mít také MetodNameCompleted událost a může mít MethodNameAsyncCancel (nebo jednoduše CancelAsync) metoda. Klient, který chce volat operaci, definuje obslužnou rutinu události, která má být volána po dokončení operace.  
  
 Následující fragment kódu ukazuje, jak deklarovat asynchronní operace pomocí asynchronního vzoru založeného na událostech.  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Další informace o asynchronním vzoru založeném na událostech naleznete [v tématu Asynchronní vzor založený na událostech](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult asynchronní vzor  
 Operaci služby lze implementovat asynchronním způsobem pomocí vzoru asynchronního programování `<Begin>` rozhraní .NET Framework a označením metody <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastností nastavenou na `true`. V tomto případě je asynchronní operace vystavena v metadatech ve stejném tvaru jako synchronní operace: Je vystavena jako jedna operace se zprávou požadavku a korelační zprávou odpovědi. Klientské programovací modely pak mají na výběr. Mohou představovat tento vzor jako synchronní operace nebo jako asynchronní, tak dlouho, dokud je služba vyvolána výměna zpráv požadavek odpověď probíhá.  
  
 Obecně platí, že s asynchronní povahu systémů, neměli byste mít závislost na vláknech.  Nejspolehlivějším způsobem předávání dat do různých fází zpracování expedice operace je použití rozšíření.  
  
 Příklad najdete v [tématu How to: Implementace operace asynchronní služby](how-to-implement-an-asynchronous-service-operation.md).  
  
 Chcete-li definovat `X` operaci smlouvy, která je provedena asynchronně bez ohledu na to, jak je volána v klientské aplikaci:  
  
- Definujte dvě metody `BeginOperation` `EndOperation`pomocí vzoru a .  
  
- Metoda `BeginOperation` obsahuje `in` `ref` a parametry pro operaci <xref:System.IAsyncResult> a vrátí typ.  
  
- Metoda `EndOperation` obsahuje <xref:System.IAsyncResult> parametr, jakož `out` i `ref` parametry a vrátí návratový typ operací.  
  
 Podívejte se například na následující metodu.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Chcete-li vytvořit asynchronní operaci, dvě metody by byly:  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> Atribut <xref:System.ServiceModel.OperationContractAttribute> je použit pouze `BeginDoWork` pro metodu. Výsledná smlouva má jednu operaci `DoWork`WSDL s názvem .  
  
### <a name="client-side-asynchronous-invocations"></a>Asynchronní vyvolání na straně klienta  
 Klientská aplikace WCF může používat libovolný ze tří asynchronních volajících modelů popsaných dříve  
  
 Při použití modelu založeného na úlohách jednoduše zavolejte operaci pomocí klíčového slova await, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Použití asynchronního vzoru založeného na událostech vyžaduje pouze přidání obslužné rutiny události pro příjem oznámení o odpovědi a výsledná událost je vyvolána ve vlákně uživatelského rozhraní automaticky. Chcete-li použít tento přístup, zadejte možnosti příkazu **/async** a **/tcv:Version35** pomocí [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Když toto provedete, Svcutil.exe generuje WCF třídy klienta s infrastrukturou událostí, která umožňuje volající aplikace implementovat a přiřadit obslužnou rutinu události pro příjem odpovědi a přijmout příslušnou akci. Úplný příklad najdete v [tématu Postup: Volání operací služby asynchronně](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Asynchronní model založený na událostech je však k dispozici pouze v rozhraní .NET Framework 3.5. Kromě toho není podporována ani v rozhraní .NET Framework 3.5 při <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>vytvoření kanálu klienta WCF pomocí . S wcf objekty kanálu <xref:System.IAsyncResult?displayProperty=nameWithType> klienta, musíte použít objekty vyvolat operace asynchronně. Chcete-li použít tento přístup, zadejte **/async** příkaz možnost s [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 Tím se vygeneruje servisní smlouva, ve `<Begin>` které je <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> každá `true` operace modelována jako metoda s vlastností nastavenou na a odpovídající `<End>` metodou. Úplný příklad pomocí <xref:System.ServiceModel.ChannelFactory%601>aplikace naleznete v tématu [How to: Call Operations Asynchronně Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 V obou případech aplikace můžete vyvolat operaci asynchronně i v případě, že služba je implementována synchronně, stejným způsobem, že aplikace můžete použít stejný vzor vyvolat asynchronně místní synchronní metody. Jak je operace implementována, není pro klienta významná. když přijde zpráva odpovědi, jeho obsah je odeslán asynchronní `End` <> metody klienta a klient načte informace.  
  
### <a name="one-way-message-exchange-patterns"></a>Vzorové vzory výměny jednosměrných zpráv  
 Můžete také vytvořit vzor asynchronní výměny zpráv, ve kterém jednosměrné operace (operace, pro které <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> nemá `true` žádnou korelační odpověď) mohou být odeslány v obou směrech klientem nebo službou nezávisle na druhé straně. (Používá duplexní vzor výměny zpráv s jednosměrné zprávy.) V tomto případě smlouva o poskytování služeb určuje jednosměrnou výměnu zpráv, kterou může kterákoli strana implementovat jako asynchronní volání nebo implementace, nebo podle potřeby ne. Obecně platí, že pokud je smlouva výměnou jednosměrných zpráv, implementace mohou být do značné míry asynchronní, protože po odeslání zprávy aplikace nečeká na odpověď a může pokračovat v jiné práci.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Asynchronní klienti a smlouvy se zprávami založené na událostech  
 Pokyny pro návrh pro asynchronní model založený na událostech uvádějí, že pokud je `Result` vrácena více než jedna <xref:System.EventArgs> hodnota, je vrácena jedna hodnota jako vlastnost a ostatní jsou vráceny jako vlastnosti objektu. Jedním z výsledků je, že pokud klient importuje metadata pomocí možností asynchronního příkazu založené <xref:System.EventArgs> na událostech `Result` a operace vrátí více <xref:System.EventArgs> než jednu hodnotu, výchozí objekt vrátí jednu hodnotu jako vlastnost a zbytek jsou vlastnosti objektu.  
  
 Pokud chcete přijmout objekt zprávy `Result` jako vlastnost a mít vrácené hodnoty jako vlastnosti na tento objekt, použijte parametr příkazu **/messageContract.** Tím se vygeneruje podpis, který `Result` vrátí <xref:System.EventArgs> zprávu odpovědi jako vlastnost na objektu. Všechny vnitřní vrácené hodnoty jsou pak vlastnosti objektu zprávy odpovědi.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
