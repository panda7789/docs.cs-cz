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
ms.openlocfilehash: c2948cf76f7763eae51689973346965bc6c720a8
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006993"
---
# <a name="synchronous-and-asynchronous-operations"></a>Synchronní a asynchronní operace
Toto téma popisuje implementace a volání operace asynchronní služby.  
  
 Mnoho aplikací volat metody asynchronně, protože umožní aplikaci pokračovat v provádění užitečné práce při volání metody, které běží. Služby Windows Communication Foundation (WCF) a klienti mohou účastnit volání asynchronní operaci na dvě různé úrovně aplikace, které poskytují ještě větší flexibilita díky maximalizuje propustnost porovnán s interaktivitu aplikací služby WCF .  
  
## <a name="types-of-asynchronous-operations"></a>Typy asynchronních operací  
 Všechny služby smluv ve službě WCF, bez ohledu na to typů parametrů a návratové hodnoty, použijte k určení vzoru výměny konkrétní zpráv mezi klientem a službou WCF atributy. WCF automaticky směruje příchozí a odchozí zprávy do příslušné službě operaci nebo se spuštěním kódu klienta.  
  
 Klient má pouze kontraktu služby, který určuje vzorce výměny zpráv pro určitou operaci. Klienti nabízí vývojářům libovolný programovací model, která si vyberou, tak dlouho, dokud se vyskytuje základní vzorce výměny zpráv. Tedy příliš, můžete služby implementovat operace jakýmkoli způsobem tak dlouho, dokud se vyskytuje vzor určenou zprávu.  
  
 Nezávislost kontrakt služby od implementace služby nebo klienta umožňuje následující formy asynchronní provádění ve službě WCF aplikací:  
  
-   Klienty můžete vyvolat operace požadavku/odpovědi asynchronně pomocí synchronní zprávy exchange.  
  
-   Služby můžete implementovat operaci požadavku nebo odpovědi asynchronně pomocí synchronní zprávy exchange.  
  
-   Výměny zpráv může být jednosměrné, bez ohledu na implementaci klienta nebo služby.  
  
### <a name="suggested-asynchronous-scenarios"></a>Navrhované asynchronní scénáře  
 Pokud implementace služby operace provede blokovacího hovoru, jako je vytváření pracovních I/O, použijte asynchronní přístup při provádění operace služby. Když jste v implementaci asynchronní operace, zkuste pro volání asynchronní operace a metody rozšíření cesty asynchronní volání, pokud je to možné. Například volání `BeginOperationTwo()` zevnitř `BeginOperationOne()`.  
  
-   Použijte asynchronní přístup v klientovi nebo volající aplikace v následujících případech:  
  
-   Pokud jsou volání operace z aplikace střední vrstvy. (Další informace o těchto scénářích najdete v tématu [klientské aplikace střední vrstvy](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Pokud vyvoláváte operace v rámci stránky ASP.NET, použijte asynchronní stránky.  
  
-   Pokud jsou volání operace z jakékoliv aplikace, která je jedinou vláken, jako jsou formuláře Windows nebo Windows Presentation Foundation (WPF). Při použití založený na událostech asynchronní volání modelu, výsledek událost je aktivována na vlákně uživatelského rozhraní, přidání rychlost odezvy do aplikace, aniž by bylo potřeba zpracovávat více vláken, sami.  
  
-   Obecně platí Pokud máte možnost volby mezi synchronní a asynchronní volání, zvolte asynchronního volání.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implementace operace asynchronní služby  
 Asynchronní operace lze provést pomocí jedné z těchto tří metod:  
  
1.  Asynchronní vzor založený na úlohách  
  
2.  Asynchronní vzor založený na událostech  
  
3.  Asynchronní vzor IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Asynchronní vzor založený na úlohách  
 Asynchronní vzor založený na úlohách je preferovaný způsob, jak implementovat asynchronní operace, protože je nejjednodušší a většina přímočaré. Chcete-li tuto metodu použijte, jednoduše implementovat vaše operace služby a určit návratový typ úlohy\<T >, kde T je typ vrácený logické operace. Příklad:  
  
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
  
 Operace SampleMethodTaskAsync vrátí úkol\<řetězec > protože logické operace vrátí hodnotu typu string. Další informace o asynchronní vzor založený na úlohách najdete v tématu [asynchronní vzor The Task-Based](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Při použití asynchronního vzoru založeného na úlohách, T:System.AggregateException může být vyvolána, pokud dojde k výjimce při čekání na dokončení operace. Tato výjimka může dojít u klienta nebo služby  
  
#### <a name="event-based-asynchronous-pattern"></a>Asynchronní vzor založený na událostech  
 Služba, která podporuje asynchronní vzor založený na událostech bude mít jednu nebo více operací s názvem MethodNameAsync. Tyto metody mohou zrcadlí synchronní verze, které provádět stejnou operaci i u aktuálního vlákna. Třídy mohou mít i MethodNameCompleted událostí a může mít MethodNameAsyncCancel (nebo jednoduše CancelAsync) metody. Klient chtějí volat operaci budou definovat obslužnou rutinu události, která se má volat po dokončení operace  
  
 Následující fragment kódu ukazuje, jak deklarovat asynchronních operací s použitím asynchronního vzoru založeného na událostech.  
  
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
  
 Další informace o asynchronní vzor založený na událostech najdete v tématu [asynchronní vzor The Event-Based](https://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Asynchronní vzor IAsyncResult  
 Operace služby je možné implementovat v asynchronním způsobem pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronní programovací model a označení `<Begin>` metodu <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> nastavenou na `true`. V takovém případě je asynchronní operace přístupný v metadatech ve stejné podobě jako synchronní operace: je vystavena jako jednu operaci s zprávu požadavku a korelační odpověď. Programovací modely Klient pak mít možnost volby. Tento model může představovat jako synchronní operace nebo některý asynchronní tak dlouho, dokud při vyvolání služby probíhá výměna zpráv žádost odpověď.  
  
 Obecně platí s asynchronní povaze v systémech, neměla by mít závislost na vlákna.  Nejspolehlivější způsob předání dat, jak různé fáze zpracování operace odeslání je použít rozšíření.  
  
 Příklad najdete v tématu [postupy: implementace operace asynchronní služby](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 K definování operace kontraktu `X` , který se provedl asynchronně bez ohledu na to, jak je volána v klientské aplikaci:  
  
-   Definovat dvě metody, pomocí vzoru `BeginOperation` a `EndOperation`.  
  
-   `BeginOperation` Metoda obsahuje `in` a `ref` parametry operace a vrátí <xref:System.IAsyncResult> typu.  
  
-   `EndOperation` Obsahuje metodu <xref:System.IAsyncResult> parametr i na `out` a `ref` parametry a vrací operace návratový typ.  
  
 Podívejte se například následující metodu.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 K vytvoření asynchronní operace, by tyto dvě metody:  
  
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
>  <xref:System.ServiceModel.OperationContractAttribute> Atributu se použije pouze `BeginDoWork` metody. Výsledný smlouva obsahuje WSDL operací s názvem `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Asynchronní volání na straně klienta  
 WCF klientské aplikace můžou používat kterýkoli z tři asynchronní volání modely je popsáno výše  
  
 Při použití modelu založeného na úlohách, jednoduše zavolejte operaci using – klíčové slovo await, jak je znázorněno v následujícím fragmentu kódu.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Použití asynchronního vzoru založeného na událostech pouze vyžaduje přidání, která je vyvolána obslužná rutina události upozornění na odpověď – a výsledné události na vlákně uživatelského rozhraní automaticky. Chcete-li tuto metodu použijte, zadejte oba **/async** a **/tcv:Version35** možnosti pomocí příkazu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následující Příklad.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Když to uděláte, Svcutil.exe vygeneruje třídy klienta WCF s vaší stávající infrastrukturou událost, která umožňuje volající aplikace k implementaci a přiřadit obslužnou rutinu události pro příjem odpovědi a proveďte příslušnou akci. Kompletní příklad naleznete v tématu [postupy: asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Asynchronní model založený na událostech, ale je k dispozici pouze v [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Kromě toho se nepodporuje i při [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] při vytvoření kanálu klienta WCF pomocí <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. S objekty kanálu klienta WCF, je nutné použít <xref:System.IAsyncResult?displayProperty=nameWithType> objekty k vyvolání operace asynchronně. Chcete-li použít tuto metodu, zadejte **/async** možnost pomocí příkazu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Tím se vygeneruje kontraktu služby ve které je každá operace modelovaná jako `<Begin>` metodu s <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost nastavena na `true` a odpovídající `<End>` metoda. Úplný příklad použití <xref:System.ServiceModel.ChannelFactory%601>, naleznete v tématu [postupy: volání operace asynchronně pomocí objektu pro vytváření kanálů](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 V obou případech se aplikace může vyvolat operaci asynchronně i v případě, že služba se implementuje synchronně, stejným způsobem, který aplikace může používat stejný vzor pro vyvolání asynchronně místní synchronní metody. Jak implementovat operace není důležité pro klienta. Při doručení zprávy s odpovědí, jeho obsah je odeslán na straně klienta asynchronní <`End`> metoda a klient načte informace.  
  
### <a name="one-way-message-exchange-patterns"></a>Jednosměrná zpráva Exchange vzory  
 Vzor asynchronních zpráv exchange můžete také vytvořit v jednosměrné operace, které (operace, pro kterou <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> je `true` mít žádné korelační reakce) může odeslat v obou směrech klienta nebo služby nezávisle na druhém na straně. (Tato služba využívá vzoru výměny zpráv duplexní s jednosměrné zprávy.) V tomto případě určuje kontrakt služby jednosměrná zpráva systému exchange, který může implementovat buď na straně jako byla zahájena asynchronní volání nebo implementací, nebo Ne, podle potřeby. Obecně platí výměny jednosměrné zprávy po kontrakt implementace do značné míry lze asynchronní vzhledem k tomu, jakmile je odeslána zpráva aplikace nečeká na odpověď a můžete pokračovat v provádění jiné práce.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Asynchronní klienty založené na události a kontrakty zpráv  
 Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.  
  
 Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte **/messageContract** možnost příkazu. Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
