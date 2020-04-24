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

Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohl načíst výsledek volání asynchronní metody. Tento příklad používal webovou službu DemoTemperatureService na adrese `http://www.xmethods.net`.

Když odkazujete na webovou službu v projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio, přidá se k `My.WebServices` objektu a rozhraní IDE vygeneruje klientskou proxy třídu pro přístup k zadané webové službě.

Třída proxy umožňuje volat metody webové služby synchronně, kde vaše aplikace čeká na dokončení funkce. Kromě toho proxy vytvoří další členy, které vám pomůžou vyvolat asynchronní volání metody. Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy podrutinu *NameOfWebServiceFunction* `Async` , událost *NameOfWebServiceFunction* `Completed` a třídu *NameOfWebServiceFunction* `CompletedEventArgs` . Tento příklad ukazuje, jak použít asynchronní členy pro přístup k `getTemp` funkci webové služby DemoTemperatureService.

> [!NOTE]
> Tento kód nefunguje ve webových aplikacích, protože ASP.NET `My.WebServices` objekt nepodporuje.

## <a name="call-a-web-service-asynchronously"></a>Asynchronní volání webové služby

1. Odkaz na webovou službu DemoTemperatureService na `http://www.xmethods.net`adrese. Adresa je

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Přidejte obslužnou rutinu události pro `getTempCompleted` událost:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > `Handles` Příkaz nelze použít k přidružení obslužné rutiny události k událostem `My.WebServices` objektu.

3. Přidejte pole, které se má sledovat, pokud byla do `getTempCompleted` události přidána obslužná rutina události:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Přidejte metodu pro přidání obslužné rutiny události do `getTempCompleted` události, je-li to nutné, a volání `getTempAsync` metody:

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

    Pro asynchronní volání `getTemp` webové metody volejte `CallGetTempAsync` metodu. Po dokončení metody web je jeho návratová hodnota předána obslužné rutině `getTempCompletedHandler` události.

## <a name="see-also"></a>Viz také

- [Přístup k aplikačním webovým službám](accessing-application-web-services.md)
- [Objekt My.WebServices](../../language-reference/objects/my-webservices-object.md)
