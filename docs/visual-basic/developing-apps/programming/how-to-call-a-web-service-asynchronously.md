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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Postupy: Asynchronní volání webové služby (Visual Basic)

Tento příklad připojí obslužnou rutinu k události asynchronní obslužné rutiny webové služby, aby mohl načíst výsledek volání asynchronní metody. Tento příklad používal webovou službu DemoTemperatureService na `http://www.xmethods.net`.

Když odkazujete na webovou službu v projektu v integrovaném vývojovém prostředí (IDE) sady Visual Studio, přidá se do objektu `My.WebServices` a IDE vygeneruje třídu proxy klienta pro přístup k zadané webové službě.

Třída proxy umožňuje volat metody webové služby synchronně, kde vaše aplikace čeká na dokončení funkce. Kromě toho proxy vytvoří další členy, které vám pomůžou vyvolat asynchronní volání metody. Pro každou funkci webové služby *NameOfWebServiceFunction*vytvoří proxy *NameOfWebServiceFunction*`Async` podprogram, událost *NameOfWebServiceFunction*`Completed` a třídu`CompletedEventArgs` *NameOfWebServiceFunction* . Tento příklad ukazuje, jak použít asynchronní členy pro přístup k funkci `getTemp` webové služby DemoTemperatureService.

> [!NOTE]
> Tento kód nefunguje ve webových aplikacích, protože ASP.NET nepodporuje objekt `My.WebServices`.

### <a name="to-call-a-web-service-asynchronously"></a>Asynchronní volání webové služby

1. Odkaz na webovou službu DemoTemperatureService na `http://www.xmethods.net`. Adresa je

    ```
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

- [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
