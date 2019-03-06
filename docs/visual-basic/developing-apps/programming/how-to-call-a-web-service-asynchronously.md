---
title: 'Postupy: Asynchronní volání webové služby (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376199"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Postupy: Asynchronní volání webové služby (Visual Basic)

Tento příklad připojí obslužnou rutinu pro webovou službu asynchronní obslužné rutiny událostí, tak, aby bylo možné získat výsledku volání asynchronní metody. Tento příklad používá DemoTemperatureService webová služba na `http://www.xmethods.net`.

Při odkazování na webovou službu v projektu v Visual Studio integrované vývojové prostředí (IDE), přidá se do `My.WebServices` objektu a rozhraní IDE vytvoří klientskou proxy třídu pro přístup k zadané webové služby

Třída proxy umožňují volání metody webové služby synchronně, kdy aplikace čeká na dokončení funkce. Kromě toho proxy serveru vytvoří další členy k usnadnění asynchronní volání metody. Pro každou funkci webové služby *NameOfWebServiceFunction*, vytvoří proxy *NameOfWebServiceFunction* `Async` podprogramu, *NameOfWebServiceFunction* `Completed` události a *NameOfWebServiceFunction* `CompletedEventArgs` třídy. Tento příklad ukazuje, jak použít asynchronní členy pro přístup k `getTemp` funkce DemoTemperatureService webové služby.

> [!NOTE]
> Tento kód nefunguje ve webových aplikacích, protože prostředí ASP.NET nepodporuje `My.WebServices` objektu.

### <a name="to-call-a-web-service-asynchronously"></a>Pro asynchronní volání webové služby

1. Odkazovat DemoTemperatureService webová služba na `http://www.xmethods.net`. Tato adresa

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Přidat obslužnou rutinu události pro `getTempCompleted` události:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Nelze použít `Handles` příkaz přidružení obslužné rutiny události s `My.WebServices` objektu události.

3. Přidat pole ke sledování, zda obslužná rutina události je přidaný do `getTempCompleted` události:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Přidejte metodu pro přidání obslužné rutiny události pro `getTempCompleted` událost v případě potřeby a k volání `getTempAsync` metody:

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

    Volání `getTemp` webovou metodu asynchronně, zavolejte `CallGetTempAsync` metody. Po dokončení metody webové služby, vrácená hodnota předána `getTempCompletedHandler` obslužné rutiny události.

## <a name="see-also"></a>Viz také:

- [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
