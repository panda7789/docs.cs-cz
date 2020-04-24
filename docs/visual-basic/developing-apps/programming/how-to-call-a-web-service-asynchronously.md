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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="3a0fb-102">Postupy: Asynchronní volání webové služby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a0fb-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="3a0fb-103">Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohl načíst výsledek volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="3a0fb-104">Tento příklad používal webovou službu DemoTemperatureService na adrese `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="3a0fb-105">Když odkazujete na webovou službu v projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio, přidá se k `My.WebServices` objektu a rozhraní IDE vygeneruje klientskou proxy třídu pro přístup k zadané webové službě.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="3a0fb-106">Třída proxy umožňuje volat metody webové služby synchronně, kde vaše aplikace čeká na dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="3a0fb-107">Kromě toho proxy vytvoří další členy, které vám pomůžou vyvolat asynchronní volání metody.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="3a0fb-108">Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy podrutinu *NameOfWebServiceFunction* `Async` , událost *NameOfWebServiceFunction* `Completed` a třídu *NameOfWebServiceFunction* `CompletedEventArgs` .</span><span class="sxs-lookup"><span data-stu-id="3a0fb-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="3a0fb-109">Tento příklad ukazuje, jak použít asynchronní členy pro přístup k `getTemp` funkci webové služby DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="3a0fb-110">Tento kód nefunguje ve webových aplikacích, protože ASP.NET `My.WebServices` objekt nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="3a0fb-111">Asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="3a0fb-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="3a0fb-112">Odkaz na webovou službu DemoTemperatureService na `http://www.xmethods.net`adrese.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="3a0fb-113">Adresa je</span><span class="sxs-lookup"><span data-stu-id="3a0fb-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="3a0fb-114">Přidejte obslužnou rutinu události pro `getTempCompleted` událost:</span><span class="sxs-lookup"><span data-stu-id="3a0fb-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="3a0fb-115">`Handles` Příkaz nelze použít k přidružení obslužné rutiny události k událostem `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="3a0fb-116">Přidejte pole, které se má sledovat, pokud byla do `getTempCompleted` události přidána obslužná rutina události:</span><span class="sxs-lookup"><span data-stu-id="3a0fb-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="3a0fb-117">Přidejte metodu pro přidání obslužné rutiny události do `getTempCompleted` události, je-li to nutné, a volání `getTempAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="3a0fb-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="3a0fb-118">Pro asynchronní volání `getTemp` webové metody volejte `CallGetTempAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="3a0fb-119">Po dokončení metody web je jeho návratová hodnota předána obslužné rutině `getTempCompletedHandler` události.</span><span class="sxs-lookup"><span data-stu-id="3a0fb-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a0fb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a0fb-120">See also</span></span>

- [<span data-ttu-id="3a0fb-121">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="3a0fb-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="3a0fb-122">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="3a0fb-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
