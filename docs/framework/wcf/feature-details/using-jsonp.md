---
title: Používání JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932831"
---
# <a name="using-jsonp"></a><span data-ttu-id="e315c-102">Používání JSONP</span><span class="sxs-lookup"><span data-stu-id="e315c-102">Using JSONP</span></span>

<span data-ttu-id="e315c-103">JSON odsazení (JSONP) je mechanismus, který umožňuje podporu skriptování napříč weby ve webových prohlížečích.</span><span class="sxs-lookup"><span data-stu-id="e315c-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="e315c-104">Navržené s ohledem na schopnost webových prohlížečů načítat skripty ze serveru jinak než aktuální načtený dokument byla načtena z JSONP.</span><span class="sxs-lookup"><span data-stu-id="e315c-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="e315c-105">Mechanismus funguje odsazením datovou část JSON s názvem funkce zpětného volání definované uživatelem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e315c-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="e315c-106">V předchozím příkladu datové části JSON `{"a" = \\"b\\"}`, je zabalený ve volání funkce `callback`.</span><span class="sxs-lookup"><span data-stu-id="e315c-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="e315c-107">Funkce zpětného volání musí již být definován v aktuální webové stránky.</span><span class="sxs-lookup"><span data-stu-id="e315c-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="e315c-108">Typ obsahu odpovědi JSONP `application/javascript`.</span><span class="sxs-lookup"><span data-stu-id="e315c-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="e315c-109">JSONP není povolené automaticky.</span><span class="sxs-lookup"><span data-stu-id="e315c-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="e315c-110">Chcete-li ji povolit, nastavte `javascriptCallbackEnabled` atribut `true` na jednom ze standardních koncových bodů HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e315c-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="e315c-111">Název funkce zpětného volání lze v dotazu proměnnou s názvem zpětné volání, jak je znázorněno na následující adrese URL.</span><span class="sxs-lookup"><span data-stu-id="e315c-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="e315c-112">Při vyvolání, služba odešle odpověď vypadat asi takto.</span><span class="sxs-lookup"><span data-stu-id="e315c-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="e315c-113">Můžete také zadat název funkce zpětného volání s použitím <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> na třídu služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e315c-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="e315c-114">Pro službu uvedenému výše žádost o vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="e315c-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="e315c-115">Při vyvolání služby odpovídá následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="e315c-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="e315c-116">Stavové kódy HTTP</span><span class="sxs-lookup"><span data-stu-id="e315c-116">HTTP Status Codes</span></span>

<span data-ttu-id="e315c-117">Odpovědi JSONP s stavové kódy HTTP než 200 obsahují druhý parametr s číselné vyjádření stavový kód HTTP, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e315c-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="e315c-118">Ověření</span><span class="sxs-lookup"><span data-stu-id="e315c-118">Validations</span></span>

<span data-ttu-id="e315c-119">Následující ověření jsou prováděny, když je povolen formát JSONP:</span><span class="sxs-lookup"><span data-stu-id="e315c-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="e315c-120">Infrastruktura WCF vyvolá výjimku, pokud `javascriptCallback` je povoleno, parametru řetězce dotazu zpětného volání je k dispozici v požadavku a formátu odpovědi je nastavená na JSON.</span><span class="sxs-lookup"><span data-stu-id="e315c-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="e315c-121">Pokud požadavek obsahuje parametr řetězce dotazu zpětné volání, ale není operaci HTTP GET, parametru zpětného volání se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e315c-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="e315c-122">Pokud je název zpětného volání `null` nebo prázdný řetězec odpovědi není formátu JSONP.</span><span class="sxs-lookup"><span data-stu-id="e315c-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="e315c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e315c-123">See also</span></span>

- [<span data-ttu-id="e315c-124">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="e315c-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
