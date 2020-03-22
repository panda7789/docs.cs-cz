---
title: 'Postupy: Asynchronní volání webové služby'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76794554"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="3f9ba-102">Postupy: Asynchronní volání webové služby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f9ba-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="3f9ba-103">Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohla načíst výsledek volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="3f9ba-104">Tento příklad použil webovou službu DemoTemperatureService ve společnosti `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="3f9ba-105">Když odkazujete na webovou službu v projektu v integrovaném vývojovém `My.WebServices` prostředí sady Visual Studio (IDE), je přidána do objektu a ide generuje třídu proxy klienta pro přístup k zadané webové službě</span><span class="sxs-lookup"><span data-stu-id="3f9ba-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="3f9ba-106">Třída proxy umožňuje volat metody webové služby synchronně, kde aplikace čeká na dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="3f9ba-107">Kromě toho proxy vytvoří další členy, které pomáhají volat metodu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="3f9ba-108">Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy server podprogram *NameOfWebServiceFunction,* `Async` událost *NameOfWebServiceFunction* `Completed` a třídu *NameOfWebServiceFunction.* `CompletedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="3f9ba-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="3f9ba-109">Tento příklad ukazuje, jak používat asynchronní členy `getTemp` pro přístup k funkci webové služby DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="3f9ba-110">Tento kód nefunguje ve webových aplikacích, `My.WebServices` protože ASP.NET nepodporuje objekt.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="3f9ba-111">Volání webové služby asynchronně</span><span class="sxs-lookup"><span data-stu-id="3f9ba-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="3f9ba-112">Odkazna webovou službu `http://www.xmethods.net`DemoTemperatureService na adrese .</span><span class="sxs-lookup"><span data-stu-id="3f9ba-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="3f9ba-113">Adresa je</span><span class="sxs-lookup"><span data-stu-id="3f9ba-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="3f9ba-114">Přidejte obslužnou rutinu `getTempCompleted` události pro událost:</span><span class="sxs-lookup"><span data-stu-id="3f9ba-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="3f9ba-115">`Handles` Příkaz nelze použít k přidružení obslužné rutiny události k událostem objektu. `My.WebServices`</span><span class="sxs-lookup"><span data-stu-id="3f9ba-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="3f9ba-116">Přidejte pole ke sledování, pokud byla `getTempCompleted` obslužná rutina události přidána do události:</span><span class="sxs-lookup"><span data-stu-id="3f9ba-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="3f9ba-117">V případě potřeby přidejte metodu pro přidání obslužné rutiny `getTempCompleted` události k události a volání `getTempAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="3f9ba-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

    ```vb
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

    <span data-ttu-id="3f9ba-118">Chcete-li `getTemp` volat webovou metodu asynchronně, zavolejte metodu. `CallGetTempAsync`</span><span class="sxs-lookup"><span data-stu-id="3f9ba-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="3f9ba-119">Po dokončení webové metody je její vrácená `getTempCompletedHandler` hodnota předána obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="3f9ba-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f9ba-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f9ba-120">See also</span></span>

- [<span data-ttu-id="3f9ba-121">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="3f9ba-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="3f9ba-122">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="3f9ba-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
