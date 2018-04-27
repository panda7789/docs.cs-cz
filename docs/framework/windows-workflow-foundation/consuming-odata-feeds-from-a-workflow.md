---
title: Využívání OData informační kanály z pracovního postupu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2057e2b1c03a1ebcd68d7d59be8839171305707f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Využívání OData informační kanály z pracovního postupu
Služby WCF Data Services je součástí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , umožňuje vytvářet služby, které používají Open Data Protocol (OData) vystavení a spotřebování data prostřednictvím webu nebo intranetu pomocí sémantiky representational stavu transfer (REST). OData zpřístupní data jako prostředky, které jsou adresovat pomocí identifikátory URI. Všechny aplikace mohou komunikovat s služby OData na základě dat Pokud můžete odeslat požadavek HTTP a zpracování datového kanálu OData, vrátí datové služby. Kromě toho služby WCF Data Services zahrnuje klientské knihovny, které poskytují bohatší programovací prostředí spotřebuje informační kanály OData z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikace. Toto téma poskytuje přehled o využívání OData kanálu v pracovním postupu s i bez použití knihovny klienta.  
  
## <a name="using-the-sample-northwind-odata-service"></a>Pomocí služby Northwind OData ukázka  
 V příkladech v tomto tématu použijte ukázku, která Northwind služba data nachází v [ http://services.odata.org/Northwind/Northwind.svc/ ](http://go.microsoft.com/fwlink/?LinkID=187426). Tato služba je k dispozici jako součást [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185248) a poskytuje přístup jen pro čtení k ukázkové databázi Northwind. Pokud se požaduje přístup pro zápis, nebo pokud se požaduje místní služby WCF Data Service, můžete provést kroky pro z [WCF Data Services rychlý Start](http://go.microsoft.com/fwlink/?LinkID=131076) vytvořit místní služba OData, která poskytuje přístup k databázi Northwind. Pokud budete postupovat podle rychlé spuštění, nahraďte místní identifikátor URI pro zadanému v ukázkový kód v tomto tématu.  
  
## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Využívání datového kanálu OData pomocí klientské knihovny  
 Služby WCF Data Services zahrnuje klientské knihovny, které vám umožní snadno využívat z datového kanálu OData [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] a klientské aplikace. Tyto knihovny zjednodušují odesílání a přijímání zpráv protokolu HTTP. Také se převede datové části zprávy do CLR objektů, které představují entity data. Knihovny klienta funkce dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy umožňují dotazování datové služby a pak pracovat s daty vrácenou entitu jako objekty CLR. Tato část obsahuje dva přístupy k vytváření aktivit, které používají knihovny klienta.  
  
### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Přidání odkazu na službu WCF Data Service  
 Chcete-li vygenerovat Northwind klientské knihovny, můžete použít **přidat odkaz na službu** dialogovém okně [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] se přidat odkaz na službu Northwind OData.  
  
 ![Přidat odkaz na službu](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")  
  
 Všimněte si, že neexistují žádné operace služby vystavený službou a v **služby** položky seznamu jsou představující entity zveřejněné službu Northwind data. Při přidání odkazu na službu pro tyto entity se generují třídy, a použít v kódu klienta. V příkladech v tomto tématu použijte tyto třídy a `NorthwindEntities` třída provádět dotazy.  
  
> [!NOTE]
>  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Generování dat služby klientské knihovny (služby WCF Data Services)](http://go.microsoft.com/fwlink/?LinkID=191611).  
  
### <a name="using-asynchronous-methods"></a>Použití asynchronních metod  
 K odstranění problémů možnou latenci, které mohou nastat při přístupu k prostředkům prostřednictvím webu, že doporučujeme, abyste přístup ke službám WCF Data asynchronně. Knihovny klienta služby WCF Data Services zahrnout asynchronní metody pro vyvolání dotazy, a poskytuje Windows Workflow Foundation (WF) <xref:System.Activities.AsyncCodeActivity> třídu pro vytváření asynchronní aktivity. <xref:System.Activities.AsyncCodeActivity> odvozené aktivity je možné zapsat do využít výhod [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tříd, které mají asynchronní metody nebo kód, který se spustí asynchronně můžete umístit do metody a vyvolána pomocí delegáta. Tato část obsahuje dva příklady <xref:System.Activities.AsyncCodeActivity> odvozené aktivity; ten, který používá asynchronní metody knihoven klienta datových služeb WCF a jeden, který používá delegáta.  
  
> [!NOTE]
>  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Asynchronní operace (služby WCF Data Services)](http://go.microsoft.com/fwlink/?LinkId=193396) a [vytváření asynchronní aktivit](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
### <a name="using-client-library-asynchronous-methods"></a>Pomocí klientské knihovny asynchronních metod  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Třída poskytuje <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody pro dotazování služby OData asynchronně. Tyto metody lze volat z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání <xref:System.Activities.AsyncCodeActivity> odvozené třídy. Když <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsání vrátí pracovního postupu můžete přejít nečinnosti (ale nezachovají) a při dokončení asynchronní pracovní <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vyvolání modulem runtime.  
  
 V následujícím příkladu se `OrdersByCustomer` aktivity je definovaný, má dva vstupní argumenty. `CustomerId` Argument představuje zákazníka, který identifikuje které objednávky vrátit, a `ServiceUri` argument představuje identifikátor URI služby OData má být dotazován. Protože aktivity odvozen z `AsyncCodeActivity<IEnumerable<Order>>` k dispozici je také <xref:System.Activities.Activity%601.Result%2A> výstup argument, který se používá k vrácení výsledků dotazu. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Přepsání vytvoří dotaz LINQ, který vybere všechny objednávky zadané zákazníka. Tento dotaz je zadán jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> z předaný <xref:System.Activities.AsyncCodeActivityContext>a pak dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda je volána. Všimněte si, že zpětného volání a stavu, který se předávají do dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> jsou ty, které jsou předané do aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metoda. Pokud dotaz byl dokončen, aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metoda je volána. Dotaz se načítají z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a pak dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda je volána. Tato metoda vrátí <xref:System.Collections.Generic.IEnumerable%601> zadaného typu entity; v tomto případě `Order`. Vzhledem k tomu `IEnumerable<Order>` je obecný typ <xref:System.Activities.AsyncCodeActivity%601>tento `IEnumerable` je nastaven jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> aktivity.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]  
  
 V následujícím příkladu `OrdersByCustomer` aktivity načte seznam objednávky zadané zákazníka a potom <xref:System.Activities.Statements.ForEach%601> aktivity zobrazí vrácený objednávky a zapisuje data každý pořadí ke konzole.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]  
  
 Po vyvolání tento pracovní postup následující data jsou zapsána do konzoly:  
  
 **Volání služby WCF Data Service...**  
**8/25/1997**   
**10/3/1997**   
**10/13/1997**   
**1/15/1998**   
**3/16/1998**   
**4/9/1998**    
> [!NOTE]
>  Pokud nelze navázat připojení k serveru OData, zobrazí se výjimka podobná následující výjimky:  
>   
>  Neošetřená výjimka: System.InvalidOperationException: při zpracování této žádosti došlo k chybě. ---> System.Net.WebException: Nelze se připojit ke vzdálenému serveru---> System.Net.Sockets.SocketException: Pokus o připojení se nezdařila, protože připojená strana nereagovala správně po uplynutí doby nebo navázáno připojení se nezdařilo. protože připojen hostitele se nepodařilo reagovat.  
  
 Pokud je potřeba žádné další zpracování dat vrácených dotazem, lze provést v rámci aktivity <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> přepsat. Obě <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> jsou vyvolány pomocí vlákno pracovního postupu, a spuštěním kódu tato přepsání není spuštěn asynchronně. Pokud je další zpracování rozsáhlých nebo dlouhotrvající nebo výsledky dotazu jsou stránkovaného fondu, měli byste zvážit přístup popsané v další části, který používá delegáta k provedení dotazu a provést další zpracování asynchronně.  
  
### <a name="using-a-delegate"></a>Použití delegáta  
 Kromě vyvolání asynchronní metody [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] třídy, <xref:System.Activities.AsyncCodeActivity>– na základě aktivity můžete také definovat asynchronní logiku v jednom z její metody. Tato metoda je určena pomocí delegáta v rámci aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsat. Když metoda vrátí, modul runtime vyvolá aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsat. Při volání služby OData z pracovního postupu, tato metoda slouží k dotazování na službu a zadejte jakékoli další zpracování.  
  
 V následujícím příkladu `ListCustomers` aktivity je definována. Tato aktivita dotazuje službu ukázka Northwind data a vrátí `List<Customer>` obsahující všechny zákazníky v databázi Northwind. Asynchronní pracovní provádí `GetCustomers` metoda. Tato metoda dotazuje službu pro všechny zákazníky a pak zkopíruje je do `List<Customer>`. Pak zkontroluje, pokud jsou výsledky stránkovaného fondu. Pokud ano, dotazuje službu pro další stránky výsledků, se přidají do seznamu a bude pokračovat, dokud všechny zákaznická data načíst.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)] stránkování v datových služeb WCF, najdete v článku. [Postupy: načtení stránkovaného výsledky (služby WCF Data Services)](http://go.microsoft.com/fwlink/?LinkId=193452).  
  
 Jakmile jsou přidány všechny zákazníky, je vrácena v seznamu. `GetCustomers` Metoda je zadán v rámci aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsat. Vzhledem k tomu, že metoda má návratovou hodnotu, `Func<string, List<Customer>>` se vytvoří určíte metodu.  
  
> [!NOTE]
>  Pokud metoda, která provede asynchronní práci nemá návratovou hodnotu <xref:System.Action> se používá místo <!--zz <xref:System.Func> --> `System.Func`. Příklady vytváření příklad asynchronní pomocí obou přístupů najdete v tématu [vytváření asynchronní aktivity](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 To <!--zz <xref:System.Func> --> `System.Func` je přiřazena k <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a potom `BeginInvoke` je volána. Vzhledem k tomu, že metoda k vyvolání nemá přístup k prostředí aktivity argumentů, hodnota `ServiceUri` argument předaný jako první parametr, společně s zpětného volání a stavu, který byly předány do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Když `GetCustomers` vrací, běhové prostředí vyvolá <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kód v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> načte delegáta z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, volání `EndInvoke`a vrátí výsledek, který je do seznamu zákazníků vrácená z `GetCustomers` metoda.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]  
  
 V následujícím příkladu `ListCustomers` aktivity načte seznam zákazníků a potom <xref:System.Activities.Statements.ForEach%601> aktivity jejich výčtu a zapíše název společnosti a jméno kontaktní osoby z každého zákazníka a do konzoly.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]  
  
 Po vyvolání tento pracovní postup následující data jsou zapsána do konzoly. Vzhledem k tomu, že tento dotaz vrací mnoho zákazníků, zobrazí se zde jenom část výstupu.  
  
 **Volání služby WCF Data Service...**  
**Alfreds Futterkiste, obraťte se na: Anders Marie**   
**ANA Trujillo Emparedados y helados, obraťte se na: Ana Trujillo**   
**Antonio Moreno Taquería, obraťte se na: Antonio Moreno**   
**Obraťte se na kolem roh,: Thomas Hardy**   
**Berglunds snabbköp, obraťte se na: Jana Berglund**   
**...**    
## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Využívání datového kanálu OData bez použití knihovny klienta  
 OData zpřístupní data jako prostředky, které jsou adresovat pomocí identifikátory URI. Při použití klientské knihovny, vytvoří se tyto identifikátory URI pro vás, ale není nutné použít knihovny klienta. V případě potřeby služby OData lze přistupovat přímo bez použití knihovny klienta. Pokud nepoužíváte knihovny klienta umístění služby a k požadovaným datům jsou zadány identifikátorem URI a výsledky jsou vráceny v odpovědi na požadavek HTTP. Tato nezpracovaná data pak můžete ji zpracovat nebo s nimi manipulovat, požadované způsobem. Je možné načíst výsledky dotazu OData pomocí <xref:System.Net.WebClient> třídy. V tomto příkladu je jméno kontaktu pro zákazníka reprezentována klíč ALFKI načteny.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]  
  
 Při spuštění tohoto kódu se zobrazí následující výstup do konzoly:  
  
 **Nezpracovaná data vrácená:**  
**\<? xml verze = "1.0" kódování = "znakové sady utf-8" samostatné = "yes"? >**   
**\<Kontakt xmlns = "http://schemas.microsoft.com/ado/2007/08/dataservices" > Marie Anders\</ContactName >** v pracovním postupu, může být součástí kód z tohoto příkladu <xref:System.Activities.CodeActivity.Execute%2A> přepsat z <xref:System.Activities.CodeActivity>– na základě vlastní aktivitu, ale stejné funkce můžete také provést pomocí <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. <xref:System.Activities.Expressions.InvokeMethod%601> Aktivity umožňuje autorům pracovního postupu a vyvolání statické metody třídy instance a má také možnost asynchronně vyvolat určenou metodu. V následujícím příkladu se <xref:System.Activities.Expressions.InvokeMethod%601> aktivity je nakonfigurován k volání <xref:System.Net.WebClient.DownloadString%2A> metodu <xref:System.Net.WebClient> třídy a vrátí seznam zákazníků.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> můžete volat statické a instance metody třídy. Vzhledem k tomu, <xref:System.Net.WebClient.DownloadString%2A> je metoda instance služby <xref:System.Net.WebClient> třídy, novou instanci třídy <xref:System.Net.WebClient> třída je určena pro <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` je zadán jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, zadaný identifikátor URI, který obsahuje dotaz v <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> je k přiřazené kolekce a návratovou hodnotu <xref:System.Activities.Activity%601.Result%2A> hodnotu. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Nastavena na hodnotu `true`, což znamená, že volání metody se spustí asynchronně s ohledem na pracovním postupu. V následujícím příkladu je pracovní postup vytvořený používající <xref:System.Activities.Expressions.InvokeMethod%601> aktivity k dotazování ukázková data Northwind službu seznam objednávky pro konkrétního zákazníka a pak je vrácená data zapsána do konzoly.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]  
  
 Po vyvolání tento pracovní postup se zobrazí následující výstup do konzoly. Vzhledem k tomu, že tento dotaz vrací několik objednávek, zobrazí se zde jenom část výstupu.  
  
 **Volání služby WCF Data Service...**  
**Nezpracovaná data vrácená:**   
**\<? xml verze = "1.0" kódování = "znakové sady utf-8" samostatné = "yes"? >**   
**\<informační kanál**   
 **XML:Base = "http://services.odata.org/Northwind/Northwind.svc/"**  
 **xmlns:d = "http://schemas.microsoft.com/ado/2007/08/dataservices"**  
 **xmlns:m = "http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"**  
 **atribut xmlns = "http://www.w3.org/2005/Atom" >**  
 **\<Typ title = "text" > objednávky \< /title >**  
 **\<ID >http://services.odata.org/Northwind/Northwind.svc/Customers("ALFKI") / řadí\</id >**  
 **\<Aktualizovat > 2010-05-19T19:37:07Z\</ aktualizovány >**  
 **\<odkaz relativní = "vlastní" title = "Objednávky" href = "Objednávky" / >**  
 **\<Položka >**  
 **\<ID >http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id >**  
 **\<Typ title = "text" > \< /title >**  
 **\<Aktualizovat > 2010-05-19T19:37:07Z\</ aktualizovány >**  
 **\<Autor >**  
 **\<název / >**  
 **\</ author >**  
 **\<odkaz relativní = "edit" title = "Order" href="Orders(10643)" / >**  
 **\<odkaz relativní = "http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer"**  
 **typ = "application/atom + xml; zadejte = entry" title = "Zákazník" href = "Objednávky (10643) nebo zákazníka" / >**  
**...**  Tento příklad obsahuje jednu metodu, pomocí aplikace autoři pracovního postupu můžete využívat nezpracovaná data vrácená z služby OData. [!INCLUDE[crabout](../../../includes/crabout-md.md)] přístup ke službám WCF Data pomocí identifikátory URI, najdete v části [přístup k prostředkům služby dat (služby WCF Data Services)](http://go.microsoft.com/fwlink/?LinkId=193397) a [OData: identifikátor URI konvence](http://go.microsoft.com/fwlink/?LinkId=185564).
