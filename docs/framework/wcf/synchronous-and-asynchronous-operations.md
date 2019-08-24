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
ms.openlocfilehash: 14bf9c89fd7142746b93cc45af6c2152e8700571
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988537"
---
# <a name="synchronous-and-asynchronous-operations"></a>Synchronní a asynchronní operace
Toto téma popisuje implementaci a volání asynchronních operací služby.  
  
 Mnoho aplikací volá metody asynchronně, protože umožňuje aplikaci dál provádět užitečnou práci, i když je volání metody spuštěno. Služby Windows Communication Foundation (WCF) a klienti se můžou účastnit volání asynchronních operací na dvou různých úrovních aplikace, které poskytují aplikacím WCF ještě větší flexibilitu při maximalizaci propustnosti vyvážené vůči interaktivitě. .  
  
## <a name="types-of-asynchronous-operations"></a>Typy asynchronních operací  
 Všechny kontrakty služeb ve službě WCF bez ohledu na typy parametrů a návratové hodnoty, používají atributy WCF k určení konkrétního vzoru výměny zpráv mezi klientem a službou. Služba WCF automaticky směruje příchozí a odchozí zprávy na příslušnou operaci služby nebo běžící kód klienta.  
  
 Klient má pouze kontrakt služby, který určuje vzor výměny zpráv pro konkrétní operaci. Klienti mohou nabídnout vývojářům libovolný model programování, který si zvolí, pokud je zaznamenán základní vzor výměny zpráv. To je také možné, že mohou služby implementovat operace jakýmkoli způsobem, pokud je zaznamenán zadaný vzor zprávy.  
  
 Nezávislost kontraktu služby od implementace služby nebo klienta umožňuje následující formy asynchronního spuštění v aplikacích WCF:  
  
- Klienti mohou asynchronně vyvolat operace požadavku/odpovědi pomocí synchronní výměny zpráv.  
  
- Služby mohou implementovat operaci žádosti nebo odpovědi asynchronně pomocí synchronní výměny zpráv.  
  
- Výměna zpráv může být jednosměrná, bez ohledu na implementaci klienta nebo služby.  
  
### <a name="suggested-asynchronous-scenarios"></a>Navrhované asynchronní scénáře  
 Použijte asynchronní přístup v implementaci operace služby, pokud implementace služby operace znemožňuje blokující volání, jako je například zpracování vstupně-výstupních operací. Pokud jste v implementaci asynchronní operace, zkuste volat asynchronní operace a metody, aby co nejvíce rozšířily cestu asynchronního volání. Například zavolejte a `BeginOperationTwo()` v rámci `BeginOperationOne()`.  
  
- Použijte asynchronní přístup v klientovi nebo volání aplikace v následujících případech:  
  
- Pokud vyvoláte operace z aplikace střední vrstvy. (Další informace o takových scénářích najdete v tématu [klientské aplikace střední vrstvy](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
- Při vyvolávání operací na stránce ASP.NET použijte asynchronní stránky.  
  
- Pokud vyvoláte operace z jakékoli aplikace s jedním vláknem, například model Windows Forms nebo Windows Presentation Foundation (WPF). Při použití asynchronního volání modelu založeného na událostech se událost výsledek vyvolá ve vlákně uživatelského rozhraní, čímž se do aplikace přidá odezva bez nutnosti zpracovávat více vláken sami.  
  
- Obecně, pokud máte možnost volby mezi synchronním a asynchronním voláním, zvolte asynchronní volání.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Implementace asynchronní operace služby  
 Asynchronní operace mohou být implementovány pomocí jedné ze tří následujících metod:  
  
1. Asynchronní vzor založený na úlohách  
  
2. Asynchronní vzor založený na událostech  
  
3. Asynchronní vzor IAsyncResult  
  
#### <a name="task-based-asynchronous-pattern"></a>Asynchronní vzor založený na úlohách  
 Asynchronní vzor založený na úlohách je preferovaný způsob implementace asynchronních operací, protože se jedná o nejjednodušší a nejvíce rovnou dopředně. Chcete-li použít tuto metodu, jednoduše implementujte operaci služby a zadejte návratový typ\<úkolu T >, kde T je typ vrácený logickou operací. Příklad:  
  
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
  
 Operace SampleMethodTaskAsync vrátí řetězec úkolu\<>, protože logická operace vrací řetězec. Další informace o asynchronním vzoru založeném na úlohách naleznete v tématu [asynchronní vzor založený](https://go.microsoft.com/fwlink/?LinkId=232504)na úlohách.  
  
> [!WARNING]
> Při použití asynchronního vzoru založeného na úlohách může být událost T:System.AggregateException vyvolána, pokud dojde k výjimce při čekání na dokončení operace. Tato výjimka může nastat u klienta nebo služeb.  
  
#### <a name="event-based-asynchronous-pattern"></a>Asynchronní vzor založený na událostech  
 Služba, která podporuje asynchronní vzor založený na událostech, bude mít jednu nebo více operací s názvem MethodNameAsync. Tyto metody mohou zrcadlit synchronní verze, které provádějí stejnou operaci v aktuálním vlákně. Třída může mít také událost MethodNameCompleted a může mít metodu MethodNameAsyncCancel (nebo jednoduše CancelAsync). Klient, který chce zavolat operaci, definuje obslužnou rutinu události, která se má volat po dokončení operace.  
  
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
  
 Další informace o asynchronním vzoru založeném na událostech naleznete v tématu [asynchronní vzor založený](https://go.microsoft.com/fwlink/?LinkId=232515)na událostech.  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>Asynchronní vzor IAsyncResult  
 Operace služby může být implementována asynchronním způsobem pomocí .NET Framework asynchronního programovacího vzoru a označením `<Begin>` metody <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> s vlastností nastavenou na `true`. V tomto případě je asynchronní operace vystavena v metadatech ve stejném tvaru jako synchronní operace: Je vystavena jako jediná operace se zprávou požadavku a zprávou s korelační odpovědí. Modely programování klientů pak mají možnost zvolit. Mohou představovat tento model jako synchronní operaci nebo jako asynchronní, tak dlouho, jak je vyvolána služba Výměna zpráv odezvy požadavku.  
  
 Obecně platí, že s asynchronní povahou systémů byste neměli mít závislost na vláknech.  Nejspolehlivějším způsobem, jak předat data do různých fází zpracování odesílání operací, je použít rozšíření.  
  
 Příklad naleznete v tématu [How to: Implementujte asynchronní operaci](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)služby.  
  
 Definování operace `X` kontraktu, která se provede asynchronně bez ohledu na to, jak se zavolá v klientské aplikaci:  
  
- Definujte dvě metody pomocí vzoru `BeginOperation` a. `EndOperation`  
  
- <xref:System.IAsyncResult> Metoda zahrnuje `in` a`ref` parametry pro operaci a vrací typ. `BeginOperation`  
  
- `EndOperation` Metoda zahrnuje`out` parametr i parametry a`ref` a vrací návratový typ operací. <xref:System.IAsyncResult>  
  
 Podívejte se například na následující metodu.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Chcete-li vytvořit asynchronní operaci, budou tyto dvě metody:  
  
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
> Atribut je použit pouze `BeginDoWork` pro metodu. <xref:System.ServiceModel.OperationContractAttribute> Výsledný kontrakt obsahuje jednu operaci WSDL s názvem `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>Asynchronní volání na straně klienta  
 Klientská aplikace WCF může použít kterýkoli ze tří modelů asynchronního volání popsaných výše.  
  
 Při použití modelu založeného na úlohách jednoduše zavolejte operaci pomocí klíčového slova await, jak je znázorněno v následujícím fragmentu kódu.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Použití asynchronního vzoru založeného na událostech vyžaduje pouze přidání obslužné rutiny události pro příjem oznámení o odpovědi – a výsledná událost je vyvolána automaticky ve vlákně uživatelského rozhraní. Chcete-li použít tento přístup, zadejte obě možnosti příkazu **/Async** a **/tcv: Version35** pomocí nástroje pro dodávání [metadat ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak je uvedeno v následujícím příkladu.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Po dokončení Svcutil. exe vygeneruje třídu klienta WCF s infrastrukturou událostí, která umožňuje volající aplikaci implementovat a přiřadit obslužnou rutinu události pro příjem odpovědi a provedení příslušné akce. Úplný příklad naleznete v tématu [How to: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Asynchronní model založený na událostech je však k dispozici pouze v [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Navíc není podporován ani v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] případě, že je kanál klienta WCF vytvořen <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>pomocí. S objekty kanálu klienta WCF je nutné použít <xref:System.IAsyncResult?displayProperty=nameWithType> objekty k asynchronnímu vyvolání svých operací. Chcete-li použít tento přístup, zadejte možnost příkazu **/Async** pomocí nástroje pro dodávání [metadat (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), jak je uvedeno v následujícím příkladu.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Tím se vygeneruje kontrakt služby, ve kterém každá operace je modelována `<Begin>` jako metoda <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> s vlastností nastavenou `true` na a odpovídající `<End>` metodou. Úplný příklad použití <xref:System.ServiceModel.ChannelFactory%601>naleznete v tématu [How to: Asynchronní volání operací pomocí objektu pro vytváření](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kanálů.  
  
 V obou případech mohou aplikace vyvolat operaci asynchronně i v případě, že je služba implementována synchronně a stejným způsobem, jako aplikace může použít stejný vzor k asynchronnímu vyvolání místní synchronní metody. Způsob implementace operace není pro klienta významné; po přijetí zprávy odpovědi se její obsah odešle do asynchronní metody <`End`> klienta a klient tyto informace načte.  
  
### <a name="one-way-message-exchange-patterns"></a>Modely jednosměrového výměny zpráv  
 Můžete také vytvořit vzorec asynchronního výměny zpráv, ve kterém jednosměrné operace (operace, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> pro které není `true` žádná korelační odpověď) může být odesílána v jednom směru klienta nebo služby nezávisle na sobě. Letiště. (Používá se jednosměrné zprávy pro výměnu zpráv.) V tomto případě kontrakt služby určuje jednosměrnou výměnu zpráv, kterou může kterákoli strana implementovat jako asynchronní volání nebo implementace nebo nemusí (případně ne). Obecně platí, že pokud je kontraktem výměna jednosměrných zpráv, implementace mohou být převážně asynchronní, protože jakmile se pošle zpráva, aplikace nečeká na odpověď a může pokračovat v práci.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Asynchronní klienti založené na událostech a kontrakty zpráv  
 Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako `Result` vlastnost se vrátí jedna hodnota a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu. Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu `Result` jako vlastnost a zbytek je <xref:System.EventArgs> vlastnosti objektu  
  
 Chcete-li jako `Result` vlastnost přijmout objekt zprávy a vracet hodnoty jako vlastnosti tohoto objektu, použijte možnost příkazového řádku **/MessageContract** . Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
