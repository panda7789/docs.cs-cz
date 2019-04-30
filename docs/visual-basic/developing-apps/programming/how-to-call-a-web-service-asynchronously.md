---
title: 'Postupy: Asynchronní volání webové služby (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943816"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="3795e-102">Postupy: Asynchronní volání webové služby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3795e-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="3795e-103">Tento příklad připojí obslužnou rutinu pro webovou službu asynchronní obslužné rutiny událostí, tak, aby bylo možné získat výsledku volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="3795e-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="3795e-104">Tento příklad používá DemoTemperatureService webová služba na `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="3795e-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="3795e-105">Při odkazování na webovou službu v projektu v Visual Studio integrované vývojové prostředí (IDE), přidá se do `My.WebServices` objektu a rozhraní IDE vytvoří klientskou proxy třídu pro přístup k zadané webové služby</span><span class="sxs-lookup"><span data-stu-id="3795e-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="3795e-106">Třída proxy umožňují volání metody webové služby synchronně, kdy aplikace čeká na dokončení funkce.</span><span class="sxs-lookup"><span data-stu-id="3795e-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="3795e-107">Kromě toho proxy serveru vytvoří další členy k usnadnění asynchronní volání metody.</span><span class="sxs-lookup"><span data-stu-id="3795e-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="3795e-108">Pro každou funkci webové služby *NameOfWebServiceFunction*, vytvoří proxy *NameOfWebServiceFunction* `Async` podprogramu, *NameOfWebServiceFunction* `Completed` události a *NameOfWebServiceFunction* `CompletedEventArgs` třídy.</span><span class="sxs-lookup"><span data-stu-id="3795e-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="3795e-109">Tento příklad ukazuje, jak použít asynchronní členy pro přístup k `getTemp` funkce DemoTemperatureService webové služby.</span><span class="sxs-lookup"><span data-stu-id="3795e-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="3795e-110">Tento kód nefunguje ve webových aplikacích, protože prostředí ASP.NET nepodporuje `My.WebServices` objektu.</span><span class="sxs-lookup"><span data-stu-id="3795e-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="3795e-111">Pro asynchronní volání webové služby</span><span class="sxs-lookup"><span data-stu-id="3795e-111">To call a Web service asynchronously</span></span>

1. <span data-ttu-id="3795e-112">Odkazovat DemoTemperatureService webová služba na `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="3795e-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="3795e-113">Tato adresa</span><span class="sxs-lookup"><span data-stu-id="3795e-113">The address is</span></span>

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="3795e-114">Přidat obslužnou rutinu události pro `getTempCompleted` události:</span><span class="sxs-lookup"><span data-stu-id="3795e-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="3795e-115">Nelze použít `Handles` příkaz přidružení obslužné rutiny události s `My.WebServices` objektu události.</span><span class="sxs-lookup"><span data-stu-id="3795e-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="3795e-116">Přidat pole ke sledování, zda obslužná rutina události je přidaný do `getTempCompleted` události:</span><span class="sxs-lookup"><span data-stu-id="3795e-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="3795e-117">Přidejte metodu pro přidání obslužné rutiny události pro `getTempCompleted` událost v případě potřeby a k volání `getTempAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="3795e-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="3795e-118">Volání `getTemp` webovou metodu asynchronně, zavolejte `CallGetTempAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="3795e-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="3795e-119">Po dokončení metody webové služby, vrácená hodnota předána `getTempCompletedHandler` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3795e-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="3795e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3795e-120">See also</span></span>

- [<span data-ttu-id="3795e-121">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="3795e-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [<span data-ttu-id="3795e-122">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="3795e-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
