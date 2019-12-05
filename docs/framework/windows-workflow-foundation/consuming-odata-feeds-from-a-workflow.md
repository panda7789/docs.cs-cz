---
title: Využívání kanálů OData z pracovního postupu – WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: c9780200d9b7c7bc89797b3c16b22bc38440fccc
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802658"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Využívání kanálů OData z pracovního postupu

WCF Data Services je součást .NET Framework, která umožňuje vytvořit služby, které používají protokol OData (Open Data Protocol) k vystavení a zpracování dat prostřednictvím webu nebo intranetu pomocí sémantiky opětovného přenosu stavu (REST). OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Každá aplikace může komunikovat s datovou službou OData, pokud může odeslat požadavek HTTP a zpracovat datový kanál OData, který vrátí datová služba. Kromě toho WCF Data Services obsahuje klientské knihovny, které poskytují bohatší programovací prostředí při využívání kanálů OData z aplikací .NET Framework. Toto téma poskytuje přehled o tom, jak používat kanál OData v pracovním postupu s a bez použití klientských knihoven.

## <a name="using-the-sample-northwind-odata-service"></a>Použití ukázkové služby OData Northwind

Příklady v tomto tématu používají ukázkovou datovou službu Northwind, která se nachází na <https://services.odata.org/Northwind/Northwind.svc/>. Tato služba je k dispozici jako součást [sady OData SDK](https://www.odata.org/wp-content/uploads/sites/21/odatasdkcodesamples.zip) a poskytuje přístup jen pro čtení k ukázkové databázi Northwind. Pokud je požadován přístup pro zápis nebo pokud potřebujete místní datovou službu WCF, můžete postupovat podle kroků v [rychlém startu WCF Data Services](../data/wcf/quickstart-wcf-data-services.md) a vytvořit místní službu OData, která poskytuje přístup k databázi Northwind. Pokud budete postupovat podle pokynů v rychlém startu, nahraďte místní identifikátor URI pro ten, který je uveden v příkladu kódu v tomto tématu.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Spotřebovávání datového kanálu OData pomocí klientských knihoven

WCF Data Services obsahuje klientské knihovny, které vám umožní snadněji využívat informační kanál OData z .NET Framework a klientských aplikací. Tyto knihovny zjednodušují posílání a přijímání zpráv HTTP. Také přeloží datovou část zprávy na objekty CLR, které představují data entity. Klientské knihovny nástroje jsou dvě základní třídy <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>. Tyto třídy vám umožní dotazovat se na datovou službu a pak pracovat s vrácenými daty entity jako s objekty CLR. Tato část obsahuje dva přístupy k vytváření aktivit, které používají klientské knihovny.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Přidání odkazu na službu do datové služby WCF

K vygenerování klientských knihoven Northwind můžete použít dialogové okno **Přidat odkaz na službu** v aplikaci Visual Studio 2012 k přidání odkazu na službu Northwind OData.

![Snímek obrazovky zobrazující dialog Přidat odkaz na službu](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Upozorňujeme, že služba nezveřejňuje žádné operace s službami a v seznamu **služeb** jsou položky, které představují entity vystavené službou Northwind data Service. Při přidání odkazu na službu se pro tyto entity vygenerují třídy a dají se použít v kódu klienta. Příklady v tomto tématu používají tyto třídy a třídu `NorthwindEntities` k provádění dotazů.

> [!NOTE]
> Další informace naleznete v tématu [generování klientské knihovny datové služby (WCF Data Services)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Použití asynchronních metod

Pro řešení možných potíží s latencí, ke kterým může dojít při přístupu k prostředkům přes web, doporučujeme WCF Data Services asynchronně přistupovat. Klientské knihovny WCF Data Services zahrnují asynchronní metody pro vyvolání dotazů a programovací model Windows Workflow Foundation (WF) poskytuje třídu <xref:System.Activities.AsyncCodeActivity> pro vytváření asynchronních aktivit. <xref:System.Activities.AsyncCodeActivity> odvozené aktivity lze zapsat, chcete-li využít výhod .NET Frameworkch tříd, které mají asynchronní metody, nebo kód, který má být proveden asynchronně, lze převést do metody a vyvolat pomocí delegáta. V této části najdete dva příklady <xref:System.Activities.AsyncCodeActivity> odvozené aktivity; ten, který používá asynchronní metody WCF Data Services klientských knihoven a druhý, který používá delegáta.

> [!NOTE]
> Další informace naleznete v tématu [asynchronní operace (WCF Data Services)](../data/wcf/asynchronous-operations-wcf-data-services.md) a [Vytváření asynchronních aktivit](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>Použití asynchronních metod klientské knihovny

Třída <xref:System.Data.Services.Client.DataServiceQuery%601> poskytuje metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pro asynchronní dotazování služby OData. Tyto metody lze volat z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> a <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> přepsání <xref:System.Activities.AsyncCodeActivity> odvozené třídy. Když se <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> přepsání vrátí, může pracovní postup přejít nečinný (ale ne zachovat) a po dokončení asynchronní práce, <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> je vyvolána modulem runtime.

V následujícím příkladu je definována aktivita `OrdersByCustomer`, která má dva vstupní argumenty. Argument `CustomerId` představuje zákazníka, který určuje, které objednávky se mají vrátit, a argument `ServiceUri` představuje identifikátor URI služby OData, ke které se má dotazovat. Vzhledem k tomu, že aktivita je odvozena z `AsyncCodeActivity<IEnumerable<Order>>` existuje také <xref:System.Activities.Activity%601.Result%2A> výstupní argument, který se používá k vrácení výsledků dotazu. Přepsání <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> vytvoří dotaz LINQ, který vybere všechny objednávky zadaného zákazníka. Tento dotaz je zadán jako <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> předaného <xref:System.Activities.AsyncCodeActivityContext>a následně je volána metoda <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> dotazu. Všimněte si, že zpětné volání a stav, které jsou předány do <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> dotazů, jsou ty, které jsou předány metodě <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> aktivity. Po dokončení zpracování dotazu je vyvolána metoda <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> aktivity. Dotaz se načte z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a pak se zavolá metoda dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>. Tato metoda vrací <xref:System.Collections.Generic.IEnumerable%601> zadaného typu entity. v tomto případě `Order`. Vzhledem k tomu, že `IEnumerable<Order>` je obecný typ <xref:System.Activities.AsyncCodeActivity%601>, je tato <xref:System.Collections.IEnumerable> nastavena jako <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> aktivity.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

V následujícím příkladu aktivita `OrdersByCustomer` načte seznam objednávek pro zadaného zákazníka a potom aktivita <xref:System.Activities.Statements.ForEach%601> vytvoří výčet vrácených objednávek a zapíše datum jednotlivých objednávek do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Při vyvolání tohoto pracovního postupu jsou do konzoly zapsána následující data:

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
> Pokud nelze navázat připojení k serveru OData, získáte výjimku podobnou této výjimce:
>
> Neošetřená výjimka: System. InvalidOperationException: při zpracování této žádosti došlo k chybě. ---> System .NET. WebException: Nelze se připojit ke vzdálenému serveru---> System .NET. Sockets. SocketException: pokus o připojení se nezdařil, protože připojená strana nereagovala po určitém časovém intervalu správně nebo nebylo navázáno připojení. vzhledem k tomu, že připojení hostitele nedokázalo odpovědět.

Pokud je požadováno jakékoli další zpracování dat vrácených dotazem, je možné je provést v přepsání <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> aktivity. <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> jsou vyvolány pomocí vlákna pracovního postupu a jakýkoliv kód v těchto přepisech neběží asynchronně. Pokud je další zpracování rozsáhlých nebo dlouhotrvajících, nebo jsou výsledky dotazu stránkované, měli byste zvážit přístup popsaný v následující části, který používá delegáta k provedení dotazu a asynchronní provádění dalších zpracování.

### <a name="using-a-delegate"></a>Použití delegáta

Kromě vyvolání asynchronní metody .NET Framework třídy může aktivita založená na <xref:System.Activities.AsyncCodeActivity>definovat také asynchronní logiku v jedné z jeho metod. Tato metoda je určena pomocí delegáta v přepsání <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> aktivity. Když se metoda vrátí, modul runtime vyvolá přepsání <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> aktivity. Při volání služby OData z pracovního postupu lze tuto metodu použít k dotazování služby a k poskytnutí dalšího zpracování.

V následujícím příkladu je definována aktivita `ListCustomers`. Tato aktivita se dotazuje na ukázkovou datovou službu Northwind a vrátí `List<Customer>`, která obsahuje všechny zákazníky v databázi Northwind. Asynchronní práci provádí metoda `GetCustomers`. Tato metoda se dotazuje služby pro všechny zákazníky a pak je zkopíruje do `List<Customer>`. Pak zkontroluje, jestli jsou výsledky stránkované. V takovém případě se dotazuje služby na další stránku výsledků, přidá je do seznamu a pokračuje, dokud nebudou načtena všechna zákaznická data.

> [!NOTE]
> Další informace o stránkování v WCF Data Services naleznete v tématu [How to: Load pageed Results (WCF Data Services)](../data/wcf/how-to-load-paged-results-wcf-data-services.md).

Po přidání všech zákazníků se seznam vrátí. Metoda `GetCustomers` je určena v přepsání <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> aktivity. Vzhledem k tomu, že metoda má návratovou hodnotu, je vytvořen `Func<string, List<Customer>>` pro určení metody.

> [!NOTE]
> Pokud metoda, která provádí asynchronní práci, nemá návratovou hodnotu, je místo <xref:System.Func%601>použita <xref:System.Action>. Příklady vytvoření asynchronního příkladu pomocí obou přístupů naleznete v tématu [Vytváření asynchronních aktivit](creating-asynchronous-activities-in-wf.md).

Tato <xref:System.Func%601> je přiřazena k <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>a je volána `BeginInvoke`. Vzhledem k tomu, že metoda, která má být vyvolána, nemá přístup k prostředí argumentů, hodnota argumentu `ServiceUri` je předána jako první parametr spolu se zpětným voláním a stavem, které byly předány do <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Když `GetCustomers` vrátí, modul runtime vyvolá <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kód v <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> načte delegáta z <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, volá `EndInvoke`a vrátí výsledek, který je seznam zákazníků vrácených z metody `GetCustomers`.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

V následujícím příkladu aktivita `ListCustomers` načte seznam zákazníků a potom ji vytvoří <xref:System.Activities.Statements.ForEach%601> a zapíše název společnosti a kontaktní jméno každého zákazníka do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Při vyvolání tohoto pracovního postupu se do konzoly zapisují následující data. Vzhledem k tomu, že tento dotaz vrací mnoho zákazníků, zobrazí se zde pouze část výstupu.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Spotřebovávání datového kanálu OData bez použití klientských knihoven

OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI. Když použijete klientské knihovny, tyto identifikátory URI se vytvoří za vás, ale nemusíte používat klientské knihovny. V případě potřeby lze ke službě OData získat přímý pøístup bez použití klientských knihoven. Pokud nepoužíváte klientské knihovny, umístění služby a požadovaná data jsou určena identifikátorem URI a výsledky se vrátí v reakci na požadavek HTTP. Tato nezpracovaná data pak můžete zpracovat nebo manipulovat požadovaným způsobem. Jedním ze způsobů, jak načíst výsledky dotazu OData, je použití třídy <xref:System.Net.WebClient>. V tomto příkladu se načte název kontaktu zákazníka reprezentovaný službou Key ALFKI.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Při spuštění tohoto kódu se v konzole zobrazí následující výstup:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

V pracovním postupu může být kód z tohoto příkladu začleněn do <xref:System.Activities.CodeActivity.Execute%2A> přepisu vlastní aktivity založené na <xref:System.Activities.CodeActivity>, ale stejné funkce lze také provést pomocí <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. Aktivita <xref:System.Activities.Expressions.InvokeMethod%601> umožňuje autorům pracovních postupů vyvolat statické a instanční metody třídy a má také možnost asynchronní vyvolání zadané metody. V následujícím příkladu je <xref:System.Activities.Expressions.InvokeMethod%601> aktivita nakonfigurována tak, aby volala metodu <xref:System.Net.WebClient.DownloadString%2A> třídy <xref:System.Net.WebClient> a vrátila seznam zákazníků.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> může volat statické a instanční metody třídy. Vzhledem k tomu, že <xref:System.Net.WebClient.DownloadString%2A> je metoda instance <xref:System.Net.WebClient> třídy, je pro <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>zadána nová instance třídy <xref:System.Net.WebClient>. `DownloadString` je zadán jako <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, identifikátor URI, který obsahuje dotaz, je určen v kolekci <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> a návratová hodnota je přiřazena k hodnotě <xref:System.Activities.Activity%601.Result%2A>. Hodnota <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> je nastavena na hodnotu `true`, což znamená, že volání metody bude spuštěno asynchronně s ohledem na pracovní postup. V následujícím příkladu je vytvořen pracovní postup, který používá aktivitu <xref:System.Activities.Expressions.InvokeMethod%601> k dotazování ukázkové služby dat Northwind na seznam objednávek pro konkrétního zákazníka a následně vracená data budou zapsána do konzoly.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Při vyvolání tohoto pracovního postupu se do konzoly zobrazí následující výstup. Vzhledem k tomu, že tento dotaz vrátí několik objednávek, zobrazí se zde pouze část výstupu.

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

Tento příklad poskytuje jednu metodu, kterou autoři aplikace pracovní postupy můžou použít ke využívání nezpracovaných dat vrácených ze služby OData. Další informace o přístupu WCF Data Services pomocí identifikátorů URI najdete v tématu [přístup k konvencím prostředků datové služby (WCF Data Services)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) a [OData: URI](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).
