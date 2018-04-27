---
title: 'Postupy: Asynchronní volání webové služby (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c7a9666141accdcc0b1346de7b0c2903c7cc86df
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="1b111-102">Postupy: Asynchronní volání webové služby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b111-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="1b111-103">Tento příklad připojí obslužnou rutinu pro asynchronní obslužnou rutinu události webové služby, tak, aby bylo možné získat výsledek asynchronní volání metody.</span><span class="sxs-lookup"><span data-stu-id="1b111-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="1b111-104">Tento příklad používá DemoTemperatureService webovou službu v http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="1b111-104">This example used the DemoTemperatureService Web service at http://www.xmethods.net.</span></span>  
  
 <span data-ttu-id="1b111-105">Když odkazujete webové služby ve vašem projektu v prostředí Visual Studio integrované vývoj prostředí (IDE), je přidán do `My.WebServices` objekt a rozhraní IDE vygeneruje třídu proxy klienta pro přístup k zadané webové služby</span><span class="sxs-lookup"><span data-stu-id="1b111-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="1b111-106">Třídu proxy umožňuje, abyste mohli volat metody webové služby synchronně, kdy aplikace čeká na dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="1b111-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="1b111-107">Kromě toho proxy serveru vytvoří další členy k usnadnění asynchronní volání metody.</span><span class="sxs-lookup"><span data-stu-id="1b111-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="1b111-108">Pro každou funkci webové služby *NameOfWebServiceFunction*, vytvoří proxy *NameOfWebServiceFunction* `Async` podprogramu, *NameOfWebServiceFunction* `Completed` události a *NameOfWebServiceFunction* `CompletedEventArgs` třídy.</span><span class="sxs-lookup"><span data-stu-id="1b111-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="1b111-109">Tento příklad ukazuje, jak používat pro přístup k asynchronní členy `getTemp` funkce DemoTemperatureService webové služby.</span><span class="sxs-lookup"><span data-stu-id="1b111-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b111-110">Tento kód nefunguje v webových aplikací, protože nepodporuje ASP.NET `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="1b111-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="1b111-111">Chcete-li asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="1b111-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="1b111-112">Odkaz webovou službu DemoTemperatureService na http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="1b111-112">Reference the DemoTemperatureService Web service at http://www.xmethods.net.</span></span> <span data-ttu-id="1b111-113">Adresa</span><span class="sxs-lookup"><span data-stu-id="1b111-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="1b111-114">Přidání obslužné rutiny události pro `getTempCompleted` událostí:</span><span class="sxs-lookup"><span data-stu-id="1b111-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1b111-115">Nelze použít `Handles` příkaz přidružit obslužné rutiny události s `My.WebServices` události objektu.</span><span class="sxs-lookup"><span data-stu-id="1b111-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="1b111-116">Přidat pole, které chcete sledovat, pokud obslužná rutina události přidala `getTempCompleted` událostí:</span><span class="sxs-lookup"><span data-stu-id="1b111-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="1b111-117">Přidání metody pro přidání obslužné rutiny události pro `getTempCompleted` událost, pokud je to nutné a k volání `getTempAsynch` metoda:</span><span class="sxs-lookup"><span data-stu-id="1b111-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     <span data-ttu-id="1b111-118">K volání `getTemp` webové metoda asynchronně, volejte `CallGetTempAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="1b111-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="1b111-119">Po dokončení metody webové služby, hodnoty předána `getTempCompletedHandler` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1b111-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b111-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b111-120">See Also</span></span>  
 [<span data-ttu-id="1b111-121">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="1b111-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [<span data-ttu-id="1b111-122">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="1b111-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
