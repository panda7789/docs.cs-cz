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
ms.openlocfilehash: 0b64d45797babff2da1649fb7469684342e65d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="synchronous-and-asynchronous-operations"></a>Synchronní a asynchronní operace
Toto téma popisuje implementace a volání operace asynchronní služby.  
  
 Mnoho aplikací volat metody asynchronně, protože umožní aplikaci pokračovat v provádění užitečné pracovní při volání metody, které běží. Služby Windows Communication Foundation (WCF) a klienti mohou účastnit volání asynchronní operaci na dvou různých úrovních aplikace, které poskytují [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace i větší flexibilitu, chcete-li maximalizovat propustnost porovnán s interaktivity.  
  
## <a name="types-of-asynchronous-operations"></a>Typy asynchronních operací  
 Všechny služby měnící [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bez ohledu na typy parametry a návratové hodnoty, použijte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] atributy zadat vzorce výměny zpráv konkrétní mezi klientem a službou. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automaticky směruje příchozí a odchozí zprávy do příslušné službě operaci nebo spuštění kódu klienta.  
  
 Klient má pouze kontrakt služby, který určuje vzorce výměny zpráv pro konkrétní operaci. Klienti nabízejí jakékoli programovací model, která si vyberou, vývojář tak dlouho, dokud se zjištěnými základní vzorce výměny zpráv. Ano příliš, můžete služby implementovat operations žádným způsobem tak dlouho, dokud se zjištěnými vzoru zadané zprávy.  
  
 Nezávislost služby smlouvy buď z službu nebo implementace klienta umožňuje následující formy asynchronního spuštění v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace:  
  
-   Klienty můžete vyvolat operace žádosti a odpovědi asynchronně pomocí exchange synchronní zprávy.  
  
-   Služby můžete implementovat operaci žádosti a odpovědi asynchronně pomocí exchange synchronní zprávy.  
  
-   Výměny zpráv může být jednosměrné, bez ohledu na implementaci klienta nebo služby.  
  
### <a name="suggested-asynchronous-scenarios"></a>Navrhované asynchronní scénáře  
 Použijte asynchronní přístup v implementaci operace služby, pokud implementace služby operace zavolá blokování, jako je například pracuje vstupně-výstupní operace. Pokud jste v implementaci asynchronní operaci, pokuste se volání asynchronních operací a metody rozšíření cesty asynchronní volání, pokud je to možné. Například volání `BeginOperationTwo()` uvnitř `BeginOperationOne()`.  
  
-   Použijte asynchronní přístup v klientovi nebo volající aplikace v následujících případech:  
  
-   Pokud jsou volání operace z aplikace střední vrstvy. (Další informace o těchto scénářích najdete v tématu [klientské aplikace střední vrstvy](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Pokud jsou volání operace v rámci stránky ASP.NET, použijte asynchronní stránky.  
  
-   Pokud jsou volání operace z jakékoli aplikace, který je zřetězený, jako jsou formuláře systému Windows nebo Windows Presentation Foundation (WPF). Při použití na základě událostí asynchronní volání modelu, výsledek událost se vyvolá při vlákna uživatelského rozhraní, aniž by bylo potřeba zpracovat více vláken, sami přidání odezvy k aplikaci.  
  
-   Obecně platí Pokud máte možnost volby mezi synchronní a asynchronní volání, zvolte asynchronního volání.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implementace operace asynchronní služby  
 Asynchronní operace můžete implementovat pomocí jedné z těchto tří metod:  
  
1.  Asynchronní vzor založený na úlohách  
  
2.  Asynchronní vzor založený na událostech  
  
3.  Asynchronní vzor IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Asynchronní vzor založený na úlohách  
 Asynchronní vzor založený na úlohách je upřednostňovaný způsob, jak implementovat asynchronní operace, protože je nejjednodušší a většina forward přímo. Při použití této metody jednoduše implementovat vaše operace služby a zadejte návratový typ úlohy\<T >, kde T představuje typ vrácený logický provoz. Příklad:  
  
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
  
 Operace SampleMethodTaskAsync vrátí úloh\<řetězec > protože logický provoz vrátí řetězec. Další informace o asynchronní vzor založený na úlohách najdete v tématu [The Task-Based asynchronní vzor](http://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Při použití asynchronní vzor založený na úlohách, T:System.AggregateException může vyvolat, když dojde k výjimce při čekání na dokončení operace. Tato výjimka může dojít u klienta nebo služby  
  
#### <a name="event-based-asynchronous-pattern"></a>Asynchronní vzor založený na událostech  
 Služba, která podporuje asynchronní vzor na základě událostí bude mít jednu nebo více operací s názvem MethodNameAsync. Tyto metody mohou zrcadlení synchronní verze, které provádět stejné operace na aktuální vlákno. Třídy mohou mít i MethodNameCompleted událostí a může mít MethodNameAsyncCancel (nebo jednoduše CancelAsync) metoda. Klient chtějí operaci volat definuje obslužnou rutinu události, která se má volat po dokončení operace  
  
 Následující fragment kódu ukazuje, jak se deklarovat asynchronních operací s použitím asynchronního vzoru založeného na událostech.  
  
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
  
 Další informace o asynchronní vzor založený na událostech najdete v tématu [The Event-Based asynchronní vzor](http://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Asynchronní vzor IAsyncResult  
 Operace služby můžou se implementovat v k asynchronní způsobem pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronní programování vzor a označení `<Begin>` metoda s <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost nastavena na hodnotu `true`. V takovém případě je vystaven asynchronní operaci v metadatech ve stejném tvaru jako synchronní operace: je zpřístupněná jako jednu operaci s zprávu požadavku a odpovědi korelační zprávou. Programovací modely klienta potom si zvolí. Tento vzor může představovat jako synchronní operace nebo některého asynchronní tak dlouho, dokud při vyvolání služby systému exchange zpráv požadavků a odpovědí probíhá.  
  
 Obecně platí s asynchronní povaha v systémech, by neměl být závislý na vláken.  Nejspolehlivějším způsobem předávání dat různé fáze zpracování operace odesílání je použití rozšíření.  
  
 Příklad, naleznete v části [postupy: implementace operace asynchronní služby](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 K definování kontraktu operace `X` se asynchronně spustí bez ohledu na to, jak je volána v aplikaci klienta:  
  
-   Definovat dvě metody pomocí vzoru `BeginOperation` a `EndOperation`.  
  
-   `BeginOperation` Metoda zahrnuje `in` a `ref` parametry pro provoz a vrátí <xref:System.IAsyncResult> typu.  
  
-   `EndOperation` Metoda zahrnuje <xref:System.IAsyncResult> parametr společně s `out` a `ref` parametry a vrátí operace návratový typ.  
  
 Například viz následující metodu.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Pokud chcete vytvořit asynchronní operaci, by se tyto dvě metody:  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationContractAttribute> Atributu se použije pouze `BeginDoWork` metoda. Výsledný smlouva obsahuje jednu operaci WSDL s názvem `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Asynchronní volání na straně klienta  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientská aplikace můžete použít některou ze tří asynchronní volání modelů popsané  
  
 Při použití modelu založený na úlohách, jednoduše volejte operace pomocí – klíčové slovo await, jak je znázorněno v následující fragment kódu.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Použití asynchronního vzoru založeného na událostech pouze vyžaduje přidání, které obslužné rutiny události pro příjem oznámení odpovědi – a výsledný událost se vyvolá při uživatelské rozhraní vlákno automaticky. Pro tento postup, zadat oba seznamy **/async** a **/tcv:Version35** příkaz Možnosti [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následující Příklad.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Když to uděláte, Svcutil.exe generuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] třída klienta s infrastrukturou událostí, která umožňuje volající aplikace k implementaci a přiřadit obslužné rutiny události přijmout odpověď a proveďte příslušnou akci. Úplný příklad najdete v tématu [postupy: asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Na základě událostí asynchronní modelu, ale je k dispozici pouze v [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Kromě toho není podporován i při [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] při [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanálem klienta je vytvořená pomocí <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. S [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanálem klienta objekty, je nutné použít <xref:System.IAsyncResult?displayProperty=nameWithType> objekty k vyvolání vaše operace asynchronně. Chcete-li použít tuto metodu, zadejte **/async** příkaz možnost s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jako v následujícím příkladu.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Tím se vygeneruje kontraktu služby ve které je modelovaná každé operace jako `<Begin>` metoda s <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost nastavena na hodnotu `true` a odpovídající `<End>` metoda. Úplný příklad použití <xref:System.ServiceModel.ChannelFactory%601>, najdete v části [postupy: volání operace asynchronně pomocí postupu kanálu](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 V obou případech aplikace může vyvolat operace asynchronně i v případě, že služba se implementuje synchronně, stejným způsobem, jakým aplikace můžete použít stejný vzor pro vyvolání asynchronně místní synchronní metody. Jak je implementována operaci není důležité pro klienta. Pokud dorazí zprávu odpovědi, její obsah se odesílají do klienta asynchronní <`End`> metoda a klient načte informace.  
  
### <a name="one-way-message-exchange-patterns"></a>Vzory Exchange jednosměrný zpráv  
 Můžete také vytvořit vzorce výměny zpráv asynchronní které Jednosměrná operace (operací, pro kterou <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> je `true` mít žádná korelační odpověď) může odeslat v obou směrech klienta služby nezávisle na druhém nebo straně. (Tato služba využívá vzorce výměny duplexní zpráv s jednosměrný zprávy.) V takovém případě kontrakt služby určuje exchange jednosměrný zpráva, která můžete implementovat stranách jako asynchronní volání nebo implementace, nebo Ne, podle potřeby. Obecně platí když kontrakt výměnou zpráv, jednosměrné, implementace do značné míry lze asynchronní vzhledem k tomu, že jakmile je odeslána zpráva aplikace čekat na odpověď a můžete pokračovat v provádění jinou práci.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Na základě událostí asynchronní klientů a kontrakty zpráv  
 Podle pokynů návrhu pro asynchronní model na základě událostí stavu, že pokud je vrácen více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnost a jiné jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto objektu je, že pokud klient naimportuje metadata pomocí možností na základě událostí asynchronní příkaz a operaci vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.  
  
 Pokud chcete dostávat zprávy objektu jako `Result` vlastnost a mít vrácené hodnoty jako vlastnosti tohoto objektu, použijte **/messageContract** příkaz možnost. Tím se vygeneruje podpisu, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
