---
title: "Použití akcí k implementaci chování na straně serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d5f3a949e8cade47876bb578725a130ef7dac934
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Použití akcí k implementaci chování na straně serveru
Akcí OData, které poskytují způsob, jak implementovat chování, který funguje na prostředek načíst ze služby OData.  Například vezměte v úvahu digitální film jako prostředek, je mnoho věcí, které může provádět s digitální video: rezervace, míry nebo komentář nebo vrácení se změnami. Toto jsou příklady všechny akce, které mohou být prováděny WCF Data Service, která spravuje digitální filmy. Akce jsou popsané v odpovědi OData obsahující prostředků, na který lze vyvolat akci. Když uživatel požádá o prostředek, který představuje digitální film odpověď vrácená služby WCF Data Service obsahuje informace o akcích, které jsou k dispozici pro tento prostředek. Dostupnost akce mohou záviset na stav služby data nebo prostředků. Pro příklad, jakmile ji je rezervována digitální film nelze rezervována jiným uživatelem. Klienty můžete vyvolat akci jednoduše tak, že zadáte adresu URL. Například by http://MyServer/MovieService.svc/Movies (6) určit konkrétní digitální film a http://MyServer/MovieService.svc/Movies (6) / Checkout by vyvolání akce na konkrétní film. Akce vám umožní vystavit můžete povolit model služby bez vystavení datového modelu. Pokračování službu příkladu film s, můžete chtít umožnit uživateli hodnocení filmu, ale ne přímo vystavit data hodnocení jako prostředek. Míra akce chcete umožnit uživatelům hodnocení filmu, ale není přímo přistupovat ke hodnocení data jako prostředek může implementovat.  
  
## <a name="implementing-an-action"></a>Implementace akce  
 K implementaci akce služby, je nutné implementovat <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), a [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) rozhraní. <xref:System.IServiceProvider>umožňuje získat vaši implementaci služby WCF Data Services [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) umožňuje součásti WCF Data Services k vytvoření, hledání, popis a vyvolání akce služby. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) umožňuje vyvolání kód, který implementuje chování se akce služby a získat výsledky, pokud existuje. Mějte na paměti, že jsou služby WCF Data Services za volání služby WCF, novou instanci služby se vytvoří pokaždé, když je volána službu.  Zajistěte, aby že žádné nepotřebné práci při vytváření služby.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider>obsahuje metodu s názvem <xref:System.IServiceProvider.GetService%2A>. Tato metoda je volána služby WCF Data Services načíst počet poskytovatelé služeb, včetně poskytovatelům služeb metadata a data poskytovatelé akce. Po zobrazení dotazu pro zprostředkovatele dat služeb akce, vrátí vaše [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) implementace.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) obsahuje metody, které vám umožní načíst informace o dostupné akce. Při implementaci [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) metadata jsou rozšířit služby, který je definovaný implementace služby [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) s akcemi a zpracování odesílání k těmto akcím podle potřeby.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) volána k určení, jaké akce jsou k dispozici pro zadaný prostředek. Tato metoda je volána pouze pro akce, které nejsou vždycky k dispozici. Umožňuje zjistit, zda akce musí být zahrnut v odpovědi OData na základě stavu požadovaný prostředek nebo stav služby. Jak se provádí tato kontrola je zcela na vás. Pokud je nákladné výpočet dostupnosti a aktuální prostředek je ve informační kanál, je přijatelné přeskočil kontrolu a inzerování akce. `inFeed` Parametr je nastaven na `true` Pokud aktuální prostředek nevrátila je součástí informačního kanálu.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) je volána k vytvoření [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) , obsahuje delegáta, který zapouzdřuje kód, který implementuje chování akce. Tím se vytvoří [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) instanci, ale není volání akce. WCF Data Service akce vedlejší efekty a potřebuji fungování ve spojení s poskytovateli aktualizací tyto změny uložit na disk. [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) metoda je volána z poskytovatele aktualizaci SaveChanges() metoda je volána.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Tato metoda vrátí kolekci [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) instance, která představuje všechny akce, které zpřístupňuje datové služby WCF. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) je reprezentace metadata akce, které obsahují informace jako název akce, jeho parametry a návratový typ.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Tato metoda vrátí kolekci všech [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) instancí, které mohou být vázány na typ parametru Zadaná vazba. Jinými slovy, všechny [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)s, který může fungovat na zadaný typ prostředku (také nazývané typ parametru vazby). To se používá, když se služba vrátí prostředek aby obsahovaly informace o akcích, které mohou být vyvolány proti prostředku. Tato metoda by měla vrátit pouze akce, které můžete vázat na typ parametru vazby přesný (žádné odvozené typy). Tato metoda je volána jednou na základě požadavku na typ a výsledek je uložené v mezipaměti služby WCF Data Services.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Tato metoda vyhledá zadanou [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) a vrátí `true` Pokud [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) nalezen. Pokud se najde, [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) je vrácený v `serviceAction``out` parametr.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Toto rozhraní poskytuje způsob, jak provést akci WCF Data Service. Při implementaci IDataServiceInvokable jste zodpovědní za 3 věcí:  
  
1.  Zaznamenání a potenciálně zařazování parametry  
  
2.  Odeslání parametry, které chcete kód, který ve skutečnosti implementuje akci při volání Invoke  
  
3.  Ukládání žádné výsledkem Invoke, takže je může načíst pomocí GetResult()  
  
 Parametry mohou být předána jako tokeny. Je to proto, že je možné zapisovat zprostředkovatele dat služby, který funguje s tokeny, které představují prostředky, pokud se jedná o tento případ, budete muset převést (zařazování) tyto tokeny do skutečné zdroje před odesláním do skutečné akce. Po parametr byl zařazeno, musí být ve stavu upravovat tak, aby všechny změny na prostředek, ke kterým došlo při vyvolání akce budou uložené a zapsaný na disk.  
  
 Toto rozhraní vyžaduje dvě metody: vyvolání a GetResult. Vyvolání vyvolá delegáta, který implementuje chování akce a vrátí GetResult výsledek akce.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Vyvolání akce WCF Data Service  
 Akce jsou vyvolány pomocí požadavku HTTP POST. Adresa URL určuje prostředky, za nímž následuje název akce. Parametry jsou předány v textu požadavku. Například pokud se služba s názvem MovieService, které poskytovaly akce vyvolaná rychlost. Můžete použít následující adresu URL pro vyvolání akce míra na konkrétní film:  
  
 http://MovieServer/MovieService.svc/Movies (1) nebo míry  
  
 Movies(1) určuje film, který si přejete rychlost a rychlost Určuje rychlost akci. Skutečná hodnota hodnocení bude v textu požadavku HTTP, jak je znázorněno v následujícím příkladu:  
  
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
>  Výše uvedený ukázkový kód budou fungovat jenom s WCF Data Services 5.2 a novějším, na kterém je podpora pro formát JSON light. Pokud používáte starší verzi datové služby WCF, je nutné zadat typ podrobné-obsah json následujícím způsobem: `application/json;odata=verbose`.  
  
 Případně můžete vyvolat akci pomocí klienta WCF Data Services, jak je znázorněno v následující fragment kódu.  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 Ve výše, fragmentu kódu `MoviesModel` třída byl vytvořen pomocí sady Visual Studio přidat odkaz na službu služby WCF Data Service.  
  
## <a name="see-also"></a>Viz také  
 [Datové služby WCF 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Definování datových služeb WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Vývoj a nasazení služby WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Poskytovatelé služeb vlastních dat](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
