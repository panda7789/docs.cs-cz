---
title: Využití informačních kanálů OData z pracovního postupu
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: 8d08a58cecead105f6e1f580ea40175cac93e417
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780099"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Využití informačních kanálů OData z pracovního postupu

Služby WCF Data Services je součástí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , která umožňuje vytvářet služby, které používají Open Data Protocol (OData) k vystavení a zpracování dat prostřednictvím webu nebo intranetu pomocí sémantiky representational state Transfer (REST). OData zveřejňuje data jako prostředky, které jsou adresovat pomocí identifikátorů URI. Všechny aplikace může interagovat s služby OData na základě dat pokud může odeslat požadavek HTTP a zpracování datového kanálu OData, vrátí datové služby. Kromě toho služeb WCF Data Services obsahuje klientské knihovny, které poskytují pohodlnější a pestřejší programovací prostředí, když využívají informačních kanálů OData z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikací. Toto téma poskytuje přehled o využívání OData kanálu v pracovním postupu a nemusíte psát tyto klientské knihovny.

## <a name="using-the-sample-northwind-odata-service"></a>Pomocí služby Northwind OData vzorku

Příklady v tomto tématu použít ukázkové datové služby umístěné v Northwind [ http://services.odata.org/Northwind/Northwind.svc/ ](https://go.microsoft.com/fwlink/?LinkID=187426). Tato služba je k dispozici jako součást [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248) a poskytuje přístup jen pro čtení k ukázkové databázi Northwind. Pokud se požaduje přístup pro zápis nebo pokud se požaduje místní službu WCF Data Service, můžete pomocí kroků v [WCF Data Services – úvodní příručka](https://go.microsoft.com/fwlink/?LinkID=131076) vytvořte místní službu OData, která poskytuje přístup k databázi Northwind. Pokud budete postupovat podle tohoto rychlého startu, nahraďte místní identifikátor URI pro jaký byl zadán v příkladu kódu v tomto tématu.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Použití datového kanálu OData pomocí klientské knihovny

Služby WCF Data Services obsahuje klientské knihovny, které vám umožní snadněji využívat z datového kanálu OData [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] a klientské aplikace. Tyto knihovny zjednodušují posílat a přijímat zprávy HTTP. Převede uzel se také datovou část zprávy do CLR objektů, které představují entity data. Tyto klientské knihovny funkce dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy umožňují dotazování datové služby a poté pracovat s daty vrácenou entitu jako objekty CLR. Tato část popisuje dva přístupy k vytváření aktivit, které používají tyto klientské knihovny.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Přidat odkaz na službu WCF Data Service

Ke generování klientských knihoven Northwind, můžete použít **přidat odkaz na službu** dialogové okno Visual Studio 2012 a přidejte odkaz na službu OData s názvem Northwind.

![Přidání odkazu na službu](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")

Všimněte si, že neexistují žádné operace služby, vystavený službou a v **služby** seznamu položek představující entity zveřejněné datová služba Northwind. Když se přidá odkaz na službu, bude generovat třídy pro tyto entity a lze v kódu klienta. Příklady v tomto tématu používají tyto třídy a `NorthwindEntities` pro provádění dotazů.

> [!NOTE]
> Další informace najdete v tématu [generování klientské knihovny datové služby (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkID=191611).

### <a name="using-asynchronous-methods"></a>Použití asynchronních metod

Na adresu možné problémy s latencí, které mohou nastat při přístupu k prostředkům prostřednictvím webu, že doporučujeme přístup ke službám WCF Data asynchronně. Tyto klientské knihovny služby WCF Data Services zahrnout asynchronní metody pro vyvolání dotazy, a poskytuje Windows Workflow Foundation (WF) <xref:System.Activities.AsyncCodeActivity> třídy pro vytváření asynchronních aktivit. <xref:System.Activities.AsyncCodeActivity> odvozený od aktivit je možné zapisovat na využít výhod [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tříd, které mají asynchronních metod nebo kód, který se provádí asynchronně můžete umístit do metody a vyvolat pomocí delegáta. Tato část obsahuje dva příklady <xref:System.Activities.AsyncCodeActivity> odvozené aktivity; ten, který používá asynchronní metody klientské knihovny služby WCF Data Services a ten, který používá delegáta.

> [!NOTE]
> Další informace najdete v tématu [asynchronních operací (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193396) a [vytváření asynchronních aktivit](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Použití asynchronních metod klientské knihovny

<xref:System.Data.Services.Client.DataServiceQuery%601> Třída poskytuje <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody pro dotazování služby OData asynchronně. Tyto metody lze volat z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání <xref:System.Activities.AsyncCodeActivity> odvozené třídy. Když <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsání vrátí pracovního postupu můžete přejít nečinnosti (ale není zachována) a dokončení asynchronní práce a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vyvolán modulem runtime.

V následujícím příkladu `OrdersByCustomer` aktivity je definován, že má dva vstupní argumenty. `CustomerId` Argument představuje zákazníka, který identifikuje objednávky, které chcete vrátit, a `ServiceUri` argument představuje identifikátor URI služby OData, aby se dalo dotazovat. Protože aktivity je odvozena z `AsyncCodeActivity<IEnumerable<Order>>` k dispozici je také <xref:System.Activities.Activity%601.Result%2A> výstupní argument, který se používá k vrácení výsledků dotazu. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Přepsání vytvoří dotaz LINQ, který vybere všechny objednávky daného zákazníka. Tento dotaz je zadán jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> předané <xref:System.Activities.AsyncCodeActivityContext>a pak v dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda je volána. Všimněte si, že zpětného volání a stavu, ve kterém jsou předány do dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> jsou ty, které jsou předány v aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> metody. Když dotaz byl dokončen, aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> vyvolání metody. Dotaz je načten z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a pak v dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda je volána. Tato metoda vrátí <xref:System.Collections.Generic.IEnumerable%601> zadaného typu entity; v tomto případě `Order`. Protože `IEnumerable<Order>` je generický typ <xref:System.Activities.AsyncCodeActivity%601>tento `IEnumerable` je nastaven jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> aktivity.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

V následujícím příkladu `OrdersByCustomer` aktivity načte seznam objednávek daného zákazníka a pak <xref:System.Activities.Statements.ForEach%601> aktivita vytváří výčet vrácené objednávky a zapisuje data jednotlivé objednávky do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Při vyvolání tento pracovní postup následující data jsou zapsána do konzoly:

```console
Calling WCF Data Service...
8/25/1997
10/3/1997
10/13/1997
1/15/1998
3/16/1998
4/9/1998
```

> [!NOTE]
> Pokud nejde navázat připojení k serveru OData, obdržíte výjimku podobně jako následující výjimku:
>
> Neošetřená výjimka: System.InvalidOperationException: došlo k chybě při zpracování tohoto požadavku. ---> System.Net.WebException: Nelze se připojit ke vzdálenému serveru---> System.Net.Sockets.SocketException: Pokus o připojení se nezdařila, protože připojená strana neodpověděla řádně po určitou dobu nebo navázané připojení se nezdařilo protože připojený hostitel se nepodařilo odpovědět.

Pokud je potřeba žádné další zpracování dat vrácených dotazem, lze provést v rámci aktivity <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> přepsat. Obě <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> jsou vyvolány pomocí vlákna pracovního postupu a žádný kód v tato přepsání není spuštěn asynchronně. Pokud je rozsáhlé nebo dlouhotrvající další zpracování nebo jsou stránkovány výsledky dotazu, měli byste zvážit přístup popsané v další části, která používá delegáta k provedení dotazu a provádění dalších asynchronní zpracování.

### <a name="using-a-delegate"></a>Použití delegáta

Kromě volání asynchronní metody z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] třídy <xref:System.Activities.AsyncCodeActivity>– na základě aktivity můžete také definovat asynchronní logiku v jednom z jeho metod. Tato metoda je určena pomocí delegáta v rámci aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsat. Po návratu metody, modul runtime vyvolá aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsat. Při volání služby OData z pracovního postupu, tato metoda slouží k dotazování na službu a zadejte jakékoli další zpracování.

V následujícím příkladu `ListCustomers` aktivity je definována. Tato aktivita dotazuje ukázková datová služba Northwind a vrátí `List<Customer>` , který obsahuje všechny zákazníky v databázi Northwind. Asynchronní práce provádí `GetCustomers` metody. Tato metoda dotazuje služby pro všechny zákazníky a pak zkopíruje je do `List<Customer>`. Pak zkontroluje, pokud jsou stránkovány výsledky. Pokud ano, dotazuje službu pro další stránky výsledků, se přidají do seznamu a bude pokračovat, dokud všechna zákaznická data načetla.

> [!NOTE]
> Další informace o stránkování ve službě WCF Data Services najdete v článku. [Postupy: načtení stránkovaných výsledků (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193452).

Jakmile se přidají všichni zákazníci, je vrácena seznamu. `GetCustomers` Zadaná metoda v rámci aktivity <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsat. Protože metoda má návratovou hodnotu `Func<string, List<Customer>>` se určit metodu.

> [!NOTE]
> Pokud vrácená hodnota nemá žádné metody, která provede asynchronní práce <xref:System.Action> se použije namísto <!--zz <xref:System.Func> --> `System.Func`. Příklady vytvoření asynchronní příklad použití obou metod naleznete v tématu [vytváření asynchronních aktivit](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

To <!--zz <xref:System.Func> --> `System.Func` přiřazen <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a potom `BeginInvoke` je volána. Protože metoda k vyvolání nemá přístup k prostředí aktivity argumentů, hodnota `ServiceUri` argument je předán jako první parametr, společně s zpětného volání a stavu, ve kterém byly předány do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Když `GetCustomers` vrátí, modul runtime vyvolá <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kód v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> načte delegáta z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, volání `EndInvoke`a vrátí výsledek, který je uvedený seznam zákazníků vrácená `GetCustomers` metody.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

V následujícím příkladu `ListCustomers` aktivity načte seznam zákazníků a pak <xref:System.Activities.Statements.ForEach%601> aktivity jejich výčtu a zapisuje do konzoly názvu společnosti a kontaktní název každého zákazníka.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Při vyvolání tento pracovní postup následující data jsou zapsána do konzoly. Vzhledem k tomu, že tento dotaz vrací celá řada zákazníků, zobrazí se tady jenom část ve výstupu.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Použití datového kanálu OData bez použití klientské knihovny

OData zveřejňuje data jako prostředky, které jsou adresovat pomocí identifikátorů URI. Při použití klientské knihovny, vytvoří se pro vás tyto identifikátory URI, ale nemáte pomocí klientských knihoven. V případě potřeby služby OData můžete přistupovat přímo bez použití klientské knihovny. Pokud nepoužíváte klientské knihovny umístění služby a požadovaná data jsou určena pomocí identifikátoru URI a výsledky jsou vráceny v reakci na požadavek HTTP. Analýzy těchto nezpracovaných dat můžete pak zpracovány nebo ovládat způsobem požadované. Jedním ze způsobů k načtení výsledků dotazu OData je použití <xref:System.Net.WebClient> třídy. V tomto příkladu se načte jméno kontaktu pro zákazníka reprezentované ALFKI klíč.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Při spuštění tohoto kódu se zobrazí následující výstup do konzoly:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

V pracovním postupu, může být součástí kódu v tomto příkladu <xref:System.Activities.CodeActivity.Execute%2A> přepsání <xref:System.Activities.CodeActivity>– vlastní aktivitě založené na, ale stejné funkce můžete také provést pomocí <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. <xref:System.Activities.Expressions.InvokeMethod%601> Aktivity umožňuje autorům pracovní postup volání statické a instanci metody dané třídy a má také možnost vyvolat určenou metodu asynchronně. V následujícím příkladu <xref:System.Activities.Expressions.InvokeMethod%601> aktivity je nakonfigurován k volání <xref:System.Net.WebClient.DownloadString%2A> metodu <xref:System.Net.WebClient> třídy a vrátí seznam zákazníků.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> můžete volat statické a instanci metody dané třídy. Protože <xref:System.Net.WebClient.DownloadString%2A> je metodu instance <xref:System.Net.WebClient> novou instanci třídy <xref:System.Net.WebClient> třída je určena pro <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` je zadán jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, je identifikátor URI, který obsahuje dotaz zadaný v <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> kolekce a návratová hodnota je přiřazená <xref:System.Activities.Activity%601.Result%2A> hodnotu. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Nastavena na hodnotu `true`, což znamená, že volání metody se spustí asynchronně jde o pracovní postup. V následujícím příkladu je vytvořen pracovní postup, který používá <xref:System.Activities.Expressions.InvokeMethod%601> aktivitu pro dotaz na ukázková data Northwind služby seznam objednávek pro konkrétního zákazníka, a potom vrácená data se zapisují do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Když uživatel vyvolá tento pracovní postup, se zobrazí následující výstup do konzoly. Vzhledem k tomu, že tento dotaz vrátí několik objednávek, pouze části výstupu se zobrazí tady.

```console
Calling WCF Data Service...
Raw data returned:

<?xml version="1.0" encoding="utf-8" standalone="yes"?>*
<feed
xml:base="http://services.odata.org/Northwind/Northwind.svc/"
xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices"
xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"
xmlns="http://www.w3.org/2005/Atom">
<title type="text">Orders\</title>
<id>http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders\</id>
<updated>2010-05-19T19:37:07Z\</updated>
<link rel="self" title="Orders" href="Orders" />
<entry>
<id>http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id>
<title type="text">\</title>
<updated>2010-05-19T19:37:07Z\</updated>
<author>
<name />
</author>
<link rel="edit" title="Order" href="Orders(10643)" />
<link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer" type="application/atom+xml;type=entry" title="Customer" href="Orders(10643)/Customer" />
...
```

V tomto příkladu poskytuje jedna metoda, autoři pracovního postupu aplikace můžete využívat nezpracovaným datům vráceným z služby OData. Další informace o přístupu k datové služby WCF pomocí identifikátorů URI najdete v tématu [přístup k prostředkům datové služby (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193397) a [OData: identifikátor URI konvence](https://go.microsoft.com/fwlink/?LinkId=185564).
