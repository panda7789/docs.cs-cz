---
title: Použití akcí k implementaci chování na straně serveru
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 515553540053ed0c16085fde06e2cc2d2dedda1e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697773"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Použití akcí k implementaci chování na straně serveru

Akcí OData, které poskytují způsob, jak implementovat chování, která funguje na prostředek získaných ze služby OData. Představme si třeba digitální video jako prostředek, spoustu věcí, které můžou dělat s digitální video: vrácení se změnami, míra/comment nebo vrácení se změnami. Tyto jsou všechny příklady akcí, které mohou být prováděny datové služby WCF, která spravuje digitální video. Akce jsou popsány v odpovědi OData, který obsahuje prostředek, na který lze vyvolat akci. Když uživatel požádá o prostředek, který představuje digitální video odpovědi vrácené ze služby WCF Data Service obsahuje informace o akcích, které jsou k dispozici pro daný prostředek. Dostupnost akce může záviset na stav dat službě nebo prostředku. Pro příklad po digitální video je rezervován jej nelze zarezervovat jiným uživatelem. Klienti mohou vyvolat akci jednoduše tak, že zadáte adresu URL. Například `http://MyServer/MovieService.svc/Movies(6)` by identifikovat konkrétní digitální video a `http://MyServer/MovieService.svc/Movies(6)/Checkout` by měl vyvolat akci u konkrétního videa. Akce umožňují vystavit můžete model služby bez vystavení datového modelu. Příklad služby video budete pokračovat, můžete chtít umožnit uživateli hodnocení filmu, ale zveřejnit přímo jako zdroj dat hodnocení. Je možné implementovat míra akce, aby uživatel mohl hodnocení filmu, ale ne přímo přistupovat k datům hodnocení jako prostředek.
  
## <a name="implementing-an-action"></a>Implementace akce  
 K provedení akce služby je nutné implementovat <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), a [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) rozhraní. <xref:System.IServiceProvider> umožňuje získat vaše implementace služby WCF Data Services [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) umožňuje služeb WCF Data Services k vytvoření, najít, popsat a vyvolání akce služby. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) umožňuje vyvolat kód, který implementuje chování služby akcí a získání požadovaných výsledků, pokud existuje. Mějte na paměti, že služeb WCF Data Services jsou jednotlivá volání služby WCF, nové instance služby vytvoří pokaždé, když je volána služby.  Ujistěte se, že žádná zbytečné práce se provádí při vytvoření služby.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider> obsahuje metodu nazvanou <xref:System.IServiceProvider.GetService%2A>. Tato metoda je volána službou WCF Data Services načíst několik poskytovatelů služeb, včetně zprostředkovatelé metadat služby a akce zprostředkovatelé datových služeb. Když se zobrazí výzva pro poskytovatele dat služeb akci, vrátí vaše [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) implementace.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) obsahuje metody, které umožňují načítat informace o dostupných akcí. Při implementaci [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) metadata jsou rozšířením pro vaši službu, které jsou definovány pomocí svojí služby, provádění [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) s akcemi a zpracování odeslání do těchto akcí podle potřeby.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) je volána k určení akce, které jsou k dispozici pro zadaný prostředek. Tato metoda je volána pouze pro akce, které nejsou vždycky k dispozici. Umožňuje zjistit, zda akce by měla být zahrnut v odpovědi OData na základě stavu požadovaný prostředek nebo stav služby. Jak se provádí tato kontrola je zcela na vás. Pokud je nákladné výpočtu dostupnosti a aktuální prostředek je v informačním kanálu, je přijatelné pro přeskočení kontroly a inzerovat akce. `inFeed` Parametr je nastaven na `true` Pokud aktuální prostředek se vrací je součástí informačního kanálu.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) je volána k vytvoření [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) , obsahuje delegáta, který zapouzdřuje kód, který implementuje chování akce. Tím se vytvoří [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) instance, ale ne vyvolat akci. Akce služby WCF Data mají vedlejší účinky a potřebují pracovat ve spojení s daným poskytovatelem aktualizace a tyto změny uložit na disk. [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) metoda je volána z aktualizace poskytovatele SaveChanges() metoda je volána.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Tato metoda vrátí kolekci [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) instancí, které představují všechny akce, které zpřístupňuje službu WCF Data Service. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) je reprezentace metadat akce, který obsahuje informace, jako je název akce, parametry a její typ vrácené hodnoty.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Tato metoda vrátí kolekci všech [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) instancí, které mohou být vázány na typ parametru určenou vazbu. Jinými slovy, všechny [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx), které může reagovat na zadaný typ prostředku (také nazývané typ parametru vazby). Používá se při služba vrátí prostředek tak, aby obsahovaly informace o akcích, které mohou být vyvolány pro daný prostředek. Tato metoda by měla vrátit jenom akce, které můžete vázat na typ parametru vazby přesné (žádné odvozené typy). Tato metoda je volána jednou každý požadavek na byl zjištěn typ a výsledek je uložen do mezipaměti služby WCF Data Services.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Tato metoda vyhledá zadanou [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) a vrátí `true` Pokud [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) nenajde. Pokud se najde, [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) se vrátí v `serviceAction` `out` parametr.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Toto rozhraní poskytuje způsob, jak provést akci WCF Data Service. Při implementaci IDataServiceInvokable zodpovídáte za 3 věci:  
  
1.  Zaznamenání a potenciálně zařazování parametry  
  
2.  Odesílání parametry tak, aby kód, který ve skutečnosti implementuje akci při volání Invoke()  
  
3.  Ukládání žádné výsledky z Invoke() tak mohou být načteny pomocí GetResult()  
  
 Parametry může být předán jako tokeny. Toto je vzhledem k tomu je možné psát poskytovatele dat služeb pracující s tokeny, které představují prostředky, pokud je to tento případ, budete muset převést (zařazování) tyto tokeny do skutečných prostředků před agresivnějším odesláním do skutečné akce. Po parametru má zařazeno, musí být ve stavu upravit tak, aby všechny změny prostředku, ke kterým dochází při vyvolání akce bude uložený a zapsané na disk.  
  
 Toto rozhraní vyžaduje dvě metody: vyvolání a GetResult. Vyvolání vyvolá delegáta, který implementuje chování akce a vrátí GetResult výsledek akce.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Vyvolání akce WCF Data Service  
 Akce jsou vyvolány pomocí požadavku HTTP POST. Adresa URL určuje prostředek, za nímž následuje název akce. Parametry jsou předány v textu požadavku. Například pokud se služba s názvem MovieService, který vystavený akci názvem míry. Můžete použít následující adresu URL k vyvolání akce míra na konkrétní filmu:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Movies(1) určuje film, který chcete sazba a sazba míra akce. Skutečná hodnota hodnocení bude v textu požadavku HTTP, jak je znázorněno v následujícím příkladu:  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> Výše uvedený ukázkový kód bude fungovat jenom s WCF Data Services 5.2 a vyšší, který má podporu pro formát JSON light. Pokud používáte starší verzi služeb WCF Data Services, je nutné zadat json verbose content-type následujícím způsobem: `application/json;odata=verbose`.  
  
 Případně můžete vyvolat akci pomocí klienta WCF Data Services, jak je znázorněno v následujícím fragmentu kódu.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 Ve výše, fragmentu kódu `MoviesModel` třídy byl vytvořen pomocí Visual Studio a přidejte odkaz na službu WCF Data Service.  
  
## <a name="see-also"></a>Viz také  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Definování datových služeb WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Vývoj a nasazení služeb WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Vlastní zprostředkovatelé datových služeb](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
