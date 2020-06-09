---
title: Používání JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594956"
---
# <a name="using-jsonp"></a><span data-ttu-id="0b413-102">Používání JSONP</span><span class="sxs-lookup"><span data-stu-id="0b413-102">Using JSONP</span></span>

<span data-ttu-id="0b413-103">Odsazení JSON (JSONP) je mechanismus, který umožňuje podporu skriptování mezi weby ve webových prohlížečích.</span><span class="sxs-lookup"><span data-stu-id="0b413-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="0b413-104">JSONP je navrženo kolem schopnosti webových prohlížečů načíst skripty z lokality odlišnou od právě načteného načteného dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0b413-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="0b413-105">Mechanismus funguje tak, že naplní datovou část JSON pomocí uživatelsky definovaného názvu funkce zpětného volání, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b413-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="0b413-106">V předchozím příkladu datová část JSON `{"a" = \\"b\\"}` je zabalena ve volání funkce, `callback` .</span><span class="sxs-lookup"><span data-stu-id="0b413-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="0b413-107">Funkce zpětného volání musí být na aktuální webové stránce již definována.</span><span class="sxs-lookup"><span data-stu-id="0b413-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="0b413-108">Typ obsahu odpovědi JSONP je `application/javascript` .</span><span class="sxs-lookup"><span data-stu-id="0b413-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="0b413-109">JSONP není automaticky povoleno.</span><span class="sxs-lookup"><span data-stu-id="0b413-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="0b413-110">Pokud ho chcete povolit, nastavte `javascriptCallbackEnabled` atribut na `true` jeden ze standardních koncových bodů http ( <xref:System.ServiceModel.Description.WebHttpEndpoint> nebo <xref:System.ServiceModel.Description.WebScriptEndpoint> ), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b413-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="0b413-111">Název funkce zpětného volání lze zadat v proměnné dotazu nazvané zpětné volání, jak je znázorněno na následující adrese URL.</span><span class="sxs-lookup"><span data-stu-id="0b413-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="0b413-112">Při vyvolání služba odešle odpověď podobnou následující.</span><span class="sxs-lookup"><span data-stu-id="0b413-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="0b413-113">Můžete také zadat název funkce zpětného volání, a to tak, že použijete na <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> třídu služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b413-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="0b413-114">U výše uvedené služby je požadavek podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="0b413-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="0b413-115">Při vyvolání služba odpoví následujícím.</span><span class="sxs-lookup"><span data-stu-id="0b413-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="0b413-116">Stavové kódy HTTP</span><span class="sxs-lookup"><span data-stu-id="0b413-116">HTTP Status Codes</span></span>

<span data-ttu-id="0b413-117">Odpovědi JSONP se stavovým kódem HTTP jiným než 200 zahrnují druhý parametr s číselnou reprezentací stavového kódu HTTP, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0b413-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="0b413-118">Ověřování</span><span class="sxs-lookup"><span data-stu-id="0b413-118">Validations</span></span>

<span data-ttu-id="0b413-119">Následující ověření jsou provedena, pokud je povoleno JSONP:</span><span class="sxs-lookup"><span data-stu-id="0b413-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="0b413-120">Infrastruktura WCF vyvolá výjimku `javascriptCallback` , pokud je povolena, v žádosti se nachází parametr řetězce dotazu zpětného volání a formát odpovědi je nastaven na JSON.</span><span class="sxs-lookup"><span data-stu-id="0b413-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="0b413-121">Pokud požadavek obsahuje parametr řetězce dotazu zpětného volání, ale operace není HTTP GET, parametr zpětného volání se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="0b413-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="0b413-122">Pokud je název zpětného volání `null` nebo prázdný řetězec, odpověď není formátována jako JSONP.</span><span class="sxs-lookup"><span data-stu-id="0b413-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b413-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b413-123">See also</span></span>

- [<span data-ttu-id="0b413-124">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="0b413-124">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
