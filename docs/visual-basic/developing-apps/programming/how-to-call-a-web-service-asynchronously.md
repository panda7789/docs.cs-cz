---
title: 'Postupy: Asynchronní volání webové služby'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794554"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Postupy: Asynchronní volání webové služby (Visual Basic)

Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohl načíst výsledek volání asynchronní metody. Tento příklad používal webovou službu DemoTemperatureService na `http://www.xmethods.net`.

Když odkazujete na webovou službu v projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio, přidá se do objektu `My.WebServices` a IDE vygeneruje třídu proxy klienta pro přístup k zadané webové službě.

Třída proxy umožňuje volat metody webové služby synchronně, kde vaše aplikace čeká na dokončení funkce. Kromě toho proxy vytvoří další členy, které vám pomůžou vyvolat asynchronní volání metody. Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy *NameOfWebServiceFunction*`Async` podprogram, událost *NameOfWebServiceFunction*`Completed` a třídu`CompletedEventArgs` *NameOfWebServiceFunction* . Tento příklad ukazuje, jak použít asynchronní členy pro přístup k funkci `getTemp` webové služby DemoTemperatureService.

> [!NOTE]
> Tento kód nefunguje ve webových aplikacích, protože ASP.NET nepodporuje objekt `My.WebServices`.

## <a name="call-a-web-service-asynchronously"></a>Asynchronní volání webové služby

1. Odkaz na webovou službu DemoTemperatureService na `http://www.xmethods.net`. Adresa je

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Přidejte obslužnou rutinu události pro událost `getTempCompleted`:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Příkaz `Handles` nelze použít k přidružení obslužné rutiny události k událostem objektu `My.WebServices`.

3. Přidejte pole, které se má sledovat, pokud byla obslužná rutina události přidána do události `getTempCompleted`:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Přidejte metodu pro přidání obslužné rutiny události do události `getTempCompleted`, pokud je to nutné, a volání `getTempAsync` metody:

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

    Pro asynchronní volání webové metody `getTemp` volejte metodu `CallGetTempAsync`. Po dokončení metody web je jeho návratová hodnota předána obslužné rutině události `getTempCompletedHandler`.

## <a name="see-also"></a>Viz také:

- [Přístup k aplikačním webovým službám](accessing-application-web-services.md)
- [Objekt My.WebServices](../../language-reference/objects/my-webservices-object.md)
