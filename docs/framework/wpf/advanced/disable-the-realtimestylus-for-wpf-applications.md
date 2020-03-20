---
title: Zakázat RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186087"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Zákaz RealTimeStylus pro aplikace WPF

Windows Presentation Foundation (WPF) má vestavěnou podporu pro zpracování dotykového vstupu systému Windows 7. Podpora přichází prostřednictvím vstupu stylusu platformy <xref:System.Windows.UIElement.OnStylusDown%2A>tabletu v reálném čase jako , <xref:System.Windows.UIElement.OnStylusUp%2A>a <xref:System.Windows.UIElement.OnStylusMove%2A> události. Windows 7 také poskytuje multi-touch vstup jako Win32 WM_TOUCH okno zprávy. Tato dvě api se vzájemně vylučují na stejném HWND. Povolenídotykového vstupu prostřednictvím platformy tabletu (výchozí pro aplikace WPF) zakáže WM_TOUCH zprávy. V důsledku toho chcete použít WM_TOUCH pro příjem dotykových zpráv z okna WPF, je nutné zakázat vestavěnou podporu stylusu v WPF. To je použitelné ve scénáři, jako je například okno WPF hostování komponenty, která používá WM_TOUCH.  
  
 Chcete-li zakázat wpf poslech stylus vstup, odeberte všechny podpory tabletu přidané oknem WPF.  
  
## <a name="example"></a>Příklad  
 Následující ukázkový kód ukazuje, jak odebrat výchozí podporu platformy tabletu pomocí reflexe.  
  
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
  
## <a name="see-also"></a>Viz také

- [Přijetí vstupu z pera](intercepting-input-from-the-stylus.md)
