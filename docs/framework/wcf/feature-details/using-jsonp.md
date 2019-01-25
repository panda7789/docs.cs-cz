---
title: Používání JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713483"
---
# <a name="using-jsonp"></a>Používání JSONP

JSON odsazení (JSONP) je mechanismus, který umožňuje podporu skriptování napříč weby ve webových prohlížečích. Navržené s ohledem na schopnost webových prohlížečů načítat skripty ze serveru jinak než aktuální načtený dokument byla načtena z JSONP. Mechanismus funguje odsazením datovou část JSON s názvem funkce zpětného volání definované uživatelem, jak je znázorněno v následujícím příkladu.

```javascript
callback({"a" = \\"b\\"});
```

V předchozím příkladu datové části JSON `{"a" = \\"b\\"}`, je zabalený ve volání funkce `callback`. Funkce zpětného volání musí již být definován v aktuální webové stránky. Typ obsahu odpovědi JSONP `application/javascript`.

JSONP není povolené automaticky. Chcete-li ji povolit, nastavte `javascriptCallbackEnabled` atribut `true` na jednom ze standardních koncových bodů HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak je znázorněno v následujícím příkladu.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Název funkce zpětného volání lze v dotazu proměnnou s názvem zpětné volání, jak je znázorněno na následující adrese URL.

`http://baseaddress/Service/RestService?callback=functionName`

Při vyvolání, služba odešle odpověď vypadat asi takto.

```javascript
functionName({"root":"Something"});
```  

Můžete také zadat název funkce zpětného volání s použitím <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> na třídu služby, jak je znázorněno v následujícím příkladu.

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

Pro službu uvedenému výše žádost o vypadá takto.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Při vyvolání služby odpovídá následujícím kódem.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Stavové kódy HTTP

Odpovědi JSONP s stavové kódy HTTP než 200 obsahují druhý parametr s číselné vyjádření stavový kód HTTP, jak je znázorněno v následujícím příkladu.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Ověření

Následující ověření jsou prováděny, když je povolen formát JSONP:

- Infrastruktura WCF vyvolá výjimku, pokud `javascriptCallback` je povoleno, parametru řetězce dotazu zpětného volání je k dispozici v požadavku a formátu odpovědi je nastavená na JSON.

- Pokud požadavek obsahuje parametr řetězce dotazu zpětné volání, ale není operaci HTTP GET, parametru zpětného volání se ignoruje.

- Pokud je název zpětného volání `null` nebo prázdný řetězec odpovědi není formátu JSONP.

## <a name="see-also"></a>Viz také:

- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
