---
title: Zakázat rozhraní RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737936"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Zákaz RealTimeStylus pro aplikace WPF

Windows Presentation Foundation (WPF) má vestavěnou podporu pro zpracování dotykového vstupu v systému Windows 7. Tato podpora se dodává prostřednictvím vstupu stylusu pro tablety v reálném čase jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>a <xref:System.Windows.UIElement.OnStylusMove%2A>ch událostí. Windows 7 také nabízí vstup s více dotykovémi zprávami jako WM_TOUCH zprávy okna Win32. Tato dvě rozhraní API se vzájemně vylučují na stejném HWND. Povolení dotykového vstupu přes platformu tabletu (výchozí pro aplikace WPF) zakáže WM_TOUCH zprávy. V důsledku toho, aby bylo možné použít WM_TOUCH pro příjem dotykových zpráv z okna WPF, je nutné zakázat integrovanou podporu stylusu v WPF. To platí ve scénáři, jako je například okno WPF hostující komponentu, která používá WM_TOUCH.  
  
 Chcete-li zakázat naslouchání WPF vstupu stylusu, odeberte všechny podpory pro tablety přidané v okně WPF.  
  
## <a name="example"></a>Příklad  
 Následující vzorový kód ukazuje, jak odebrat výchozí podporu platformy pro tablety pomocí reflexe.  
  
```csharp  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Přijetí vstupu z pera](intercepting-input-from-the-stylus.md)
