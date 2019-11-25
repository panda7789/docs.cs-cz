---
title: 'Postupy: Asynchronní volání webové služby'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 0eeb358ba38836ba6302f98f9e3e0314b83510f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352123"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="86a2f-102">Postupy: Asynchronní volání webové služby (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86a2f-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="86a2f-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span><span class="sxs-lookup"><span data-stu-id="86a2f-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="86a2f-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="86a2f-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="86a2f-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span><span class="sxs-lookup"><span data-stu-id="86a2f-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="86a2f-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span><span class="sxs-lookup"><span data-stu-id="86a2f-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="86a2f-107">In addition, the proxy creates additional members to help call the method asynchronously.</span><span class="sxs-lookup"><span data-stu-id="86a2f-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="86a2f-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span><span class="sxs-lookup"><span data-stu-id="86a2f-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="86a2f-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span><span class="sxs-lookup"><span data-stu-id="86a2f-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="86a2f-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span><span class="sxs-lookup"><span data-stu-id="86a2f-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="86a2f-111">To call a Web service asynchronously</span><span class="sxs-lookup"><span data-stu-id="86a2f-111">To call a Web service asynchronously</span></span>

1. <span data-ttu-id="86a2f-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="86a2f-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="86a2f-113">The address is</span><span class="sxs-lookup"><span data-stu-id="86a2f-113">The address is</span></span>

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="86a2f-114">Add an event handler for the `getTempCompleted` event:</span><span class="sxs-lookup"><span data-stu-id="86a2f-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="86a2f-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span><span class="sxs-lookup"><span data-stu-id="86a2f-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="86a2f-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span><span class="sxs-lookup"><span data-stu-id="86a2f-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="86a2f-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span><span class="sxs-lookup"><span data-stu-id="86a2f-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="86a2f-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span><span class="sxs-lookup"><span data-stu-id="86a2f-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="86a2f-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span><span class="sxs-lookup"><span data-stu-id="86a2f-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="86a2f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86a2f-120">See also</span></span>

- [<span data-ttu-id="86a2f-121">Přístup k aplikačním webovým službám</span><span class="sxs-lookup"><span data-stu-id="86a2f-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [<span data-ttu-id="86a2f-122">Objekt My.WebServices</span><span class="sxs-lookup"><span data-stu-id="86a2f-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
