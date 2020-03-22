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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Postupy: Asynchronní volání webové služby (Visual Basic)

Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohla načíst výsledek volání asynchronní metody. Tento příklad použil webovou službu DemoTemperatureService ve společnosti `http://www.xmethods.net`.

Když odkazujete na webovou službu v projektu v integrovaném vývojovém `My.WebServices` prostředí sady Visual Studio (IDE), je přidána do objektu a ide generuje třídu proxy klienta pro přístup k zadané webové službě

Třída proxy umožňuje volat metody webové služby synchronně, kde aplikace čeká na dokončení funkce. Kromě toho proxy vytvoří další členy, které pomáhají volat metodu asynchronně. Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy server podprogram *NameOfWebServiceFunction,* `Async` událost *NameOfWebServiceFunction* `Completed` a třídu *NameOfWebServiceFunction.* `CompletedEventArgs` Tento příklad ukazuje, jak používat asynchronní členy `getTemp` pro přístup k funkci webové služby DemoTemperatureService.

> [!NOTE]
> Tento kód nefunguje ve webových aplikacích, `My.WebServices` protože ASP.NET nepodporuje objekt.

## <a name="call-a-web-service-asynchronously"></a>Volání webové služby asynchronně

1. Odkazna webovou službu `http://www.xmethods.net`DemoTemperatureService na adrese . Adresa je

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Přidejte obslužnou rutinu `getTempCompleted` události pro událost:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > `Handles` Příkaz nelze použít k přidružení obslužné rutiny události k událostem objektu. `My.WebServices`

3. Přidejte pole ke sledování, pokud byla `getTempCompleted` obslužná rutina události přidána do události:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. V případě potřeby přidejte metodu pro přidání obslužné rutiny `getTempCompleted` události k události a volání `getTempAsync` metody:

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

    Chcete-li `getTemp` volat webovou metodu asynchronně, zavolejte metodu. `CallGetTempAsync` Po dokončení webové metody je její vrácená `getTempCompletedHandler` hodnota předána obslužné rutině události.

## <a name="see-also"></a>Viz také

- [Přístup k aplikačním webovým službám](accessing-application-web-services.md)
- [Objekt My.WebServices](../../language-reference/objects/my-webservices-object.md)
