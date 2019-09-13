---
title: Použití akcí k implementaci chování na straně serveru
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 5c71cfe8965cf8edbe07ff7ae4c6be95b437bf80
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894266"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Použití akcí k implementaci chování na straně serveru

Akce OData poskytují způsob, jak implementovat chování, které funguje na zdroji načteném ze služby OData. Například považujete digitální film za prostředek, existuje mnoho věcí, které můžete provádět s digitálním filmem: rezervace, sazba/komentář nebo vrácení se změnami. Jedná se o všechny příklady akcí, které mohou být implementovány datovou službou WCF, která spravuje digitální filmy. Akce jsou popsány v odpovědi OData obsahující prostředek, na kterém lze akci vyvolat. Když uživatel požádá o prostředek, který představuje digitální film, odpověď vrácená službou WCF Data Service obsahuje informace o akcích, které jsou k dispozici pro daný prostředek. Dostupnost akce může záviset na stavu datové služby nebo prostředku. Například když je digitální film rezervován, nemůže být rezervován jiným uživatelem. Klienti mohou vyvolat akci jednoduše zadáním adresy URL. Například `http://MyServer/MovieService.svc/Movies(6)` by identifikoval konkrétní digitální film a `http://MyServer/MovieService.svc/Movies(6)/Checkout` vyvolal akci u konkrétního filmu. Akce umožňují vystavit model služby, aniž by byl váš datový model vystavený. V případě, že budete pokračovat s příkladem služby filmů, možná budete chtít uživateli dovolit Ohodnotit film, ale ne přímo vystavovat data hodnocení jako prostředek. Můžete implementovat míru akce, která uživateli umožní Ohodnotit film, ale ne přímo přístup k datům hodnocení jako prostředek.
  
## <a name="implementing-an-action"></a>Implementace akce  
 Chcete-li implementovat akci služby <xref:System.IServiceProvider>, musíte implementovat rozhraní, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))a [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) . <xref:System.IServiceProvider>umožňuje WCF Data Services získat implementaci [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)). [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) umožňuje WCF Data Services vytvořit, najít, popsat a vyvolat akce služby. [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) umožňuje vyvolat kód, který implementuje chování akcí služby a získá výsledky, pokud existují. Mějte na paměti, že WCF Data Services jsou služby WCF vázané na volání, nová instance služby se vytvoří pokaždé, když je služba volána.  Ujistěte se, že při vytvoření služby není provedena žádná nepotřebná práce.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider>obsahuje metodu s názvem <xref:System.IServiceProvider.GetService%2A>. Tato metoda je volána WCF Data Services k načtení řady poskytovatelů služeb, včetně poskytovatelů služeb metadat a zprostředkovatelů akcí datových služeb. Po zobrazení výzvy pro poskytovatele akcí datové služby vraťte implementaci [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) .  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) obsahuje metody, které umožňují načíst informace o dostupných akcích. Při implementaci [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) rozšiřujete metadata pro vaši službu, která je definována implementací služby [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) vaší služby, s akcemi a zpracováním odesílání pro tyto akce jako přiměřený.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 Je volána [Metoda AdvertiseServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) , která určuje, jaké akce jsou pro zadaný prostředek k dispozici. Tato metoda je volána pouze pro akce, které nejsou vždy k dispozici. Slouží ke kontrole, zda by měla být akce v odpovědi OData obsažena v závislosti na stavu požadovaného prostředku nebo stavu služby. Způsob, jakým je tato kontroly dokončena, je zcela na vás. Pokud je pro výpočet dostupnosti nákladné a aktuální prostředek je v informačním kanálu, je přijatelné Přeskočit kontrolu a inzerovat akci. Parametr je nastaven na `true` hodnotu, pokud je aktuální vracený prostředek součástí informačního kanálu. `inFeed`  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) se volá za účelem vytvoření [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , který obsahuje delegát, který zapouzdřuje kód, který implementuje chování akce. Tím se vytvoří instance [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , ale akce nevyvolá. Akce datové služby WCF mají vedlejší účinky a potřebují pracovat společně se zprostředkovatelem aktualizací, aby se tyto změny uložily na disk. Metoda [IDataServiceInvokable. Invoke](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) je volána z metody SaveChanges () poskytovatele aktualizace.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Tato metoda vrátí kolekci instancí [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) , které reprezentují všechny akce, které zpřístupňuje datová služba WCF. [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) je reprezentace metadat pro akci, která obsahuje informace, jako je název akce, její parametry a její návratový typ.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Tato metoda vrátí kolekci všech instancí [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) , které mohou být vázány na zadaný typ parametru vazby. Jinými slovy všechny [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))s, které mohou fungovat na zadaném typu prostředku (označované také jako typ parametru vazby). Tato možnost se používá, pokud služba vrací prostředek, aby obsahovala informace o akcích, které mohou být pro daný prostředek vyvolány. Tato metoda by měla vracet pouze akce, které mohou být vázány na přesný typ parametru vazby (žádné odvozené typy). Tato metoda se volá jednou pro každý typ a výsledek je uložený v mezipaměti WCF Data Services.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Tato metoda vyhledá zadaný [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) a vrátí `true` , pokud se najde [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) . Pokud se najde, vrátí se [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) v `serviceAction` `out` parametru.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Toto rozhraní poskytuje způsob, jak spustit akci služby WCF Data Service. Při implementaci IDataServiceInvokable zodpovídáte za 3 věci:  
  
1. Zachytávání a potenciálně zařazování parametrů  
  
2. Odesílání parametrů do kódu, který ve skutečnosti implementuje akci při volání metody Invoke ()  
  
3. Uložení jakýchkoli výsledků z vyvolání (), aby je bylo možné načíst pomocí getResult ()  
  
 Parametry mohou být předány jako tokeny. Je to proto, že je možné napsat poskytovatele datové služby, který funguje s tokeny, které reprezentují prostředky, pokud se jedná o případ, že budete možná potřebovat převést (zařadit) tyto tokeny na skutečné prostředky a teprve potom odeslat aktuální akci. Po zařazení parametru musí být v upravitelném stavu, aby se všechny změny prostředku, ke kterým dojde při vyvolání akce, ukládaly a zapsaly na disk.  
  
 Toto rozhraní vyžaduje dvě metody: Invoke a GetResult. Invoke vyvolá delegáta, který implementuje chování akce a GetResult Vrátí výsledek akce.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Vyvolání akce datové služby WCF  
 Akce jsou vyvolány pomocí požadavku HTTP POST. Adresa URL Určuje prostředek následovaný názvem akce. Parametry jsou předány v těle žádosti. Například pokud existovala služba s názvem MovieService, která vystavila akci s názvem Rate. Pomocí následující adresy URL můžete na konkrétním videu vyvolat míru akce:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Filmy (1) určuje film, který chcete ohodnotit, a rychlost Určuje akci. Skutečná hodnota hodnocení bude v těle požadavku HTTP, jak je znázorněno v následujícím příkladu:  
  
```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> Výše uvedený vzorový kód bude fungovat jenom s WCF Data Services 5,2 a novějším, které mají podporu pro světlo JSON. Pokud používáte starší verzi WCF Data Services, je nutné zadat podrobný obsah typu verbose JSON následujícím způsobem: `application/json;odata=verbose`.  
  
 Alternativně můžete vyvolat akci pomocí klienta WCF Data Services, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 Ve fragmentu kódu výše byl `MoviesModel` třída generována pomocí sady Visual Studio, aby přidat odkaz na službu k datové službě WCF.  
  
## <a name="see-also"></a>Viz také:

- [WCF Data Services 4.5](index.md)
- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Vývoj a nasazení služeb WCF Data Services](developing-and-deploying-wcf-data-services.md)
- [Vlastní zprostředkovatelé datových služeb](custom-data-service-providers-wcf-data-services.md)
