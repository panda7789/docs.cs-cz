---
title: 'Postupy: Asynchronní volání webové služby (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 8968eaa8edd8dee177906a6c801f2f46c2a740d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589032"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Postupy: Asynchronní volání webové služby (Visual Basic)
Tento příklad připojí obslužnou rutinu pro asynchronní obslužnou rutinu události webové služby, tak, aby bylo možné získat výsledek asynchronní volání metody. Tento příklad používá DemoTemperatureService webovou službu v http://www.xmethods.net.  
  
 Když odkazujete webové služby ve vašem projektu v prostředí Visual Studio integrované vývoj prostředí (IDE), je přidán do `My.WebServices` objekt a rozhraní IDE vygeneruje třídu proxy klienta pro přístup k zadané webové služby  
  
 Třídu proxy umožňuje, abyste mohli volat metody webové služby synchronně, kdy aplikace čeká na dokončení funkce. Kromě toho proxy serveru vytvoří další členy k usnadnění asynchronní volání metody. Pro každou funkci webové služby *NameOfWebServiceFunction*, vytvoří proxy *NameOfWebServiceFunction* `Async` podprogramu, *NameOfWebServiceFunction* `Completed` události a *NameOfWebServiceFunction* `CompletedEventArgs` třídy. Tento příklad ukazuje, jak používat pro přístup k asynchronní členy `getTemp` funkce DemoTemperatureService webové služby.  
  
> [!NOTE]
>  Tento kód nefunguje v webových aplikací, protože nepodporuje ASP.NET `My.WebServices` objektu.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Chcete-li asynchronní volání webové služby  
  
1.  Odkaz webovou službu DemoTemperatureService na http://www.xmethods.net. Adresa  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Přidání obslužné rutiny události pro `getTempCompleted` událostí:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Nelze použít `Handles` příkaz přidružit obslužné rutiny události s `My.WebServices` události objektu.  
  
3.  Přidat pole, které chcete sledovat, pokud obslužná rutina události přidala `getTempCompleted` událostí:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Přidání metody pro přidání obslužné rutiny události pro `getTempCompleted` událost, pokud je to nutné a k volání `getTempAsynch` metoda:  
  
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
  
     K volání `getTemp` webové metoda asynchronně, volejte `CallGetTempAsync` metoda. Po dokončení metody webové služby, hodnoty předána `getTempCompletedHandler` obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
