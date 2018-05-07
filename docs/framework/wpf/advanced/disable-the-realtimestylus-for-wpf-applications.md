---
title: Zákaz RealTimeStylus pro aplikace WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: ddf4a7f4488f957b2f413d61ad02aa59beba30f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Zákaz RealTimeStylus pro aplikace WPF
Windows Presentation Foundation (WPF) má integrovanou podporu pro zpracování dotykové ovládání Windows 7. Podpora přicházejí vstup v reálném čase pera tablet platformy jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, a <xref:System.Windows.UIElement.OnStylusMove%2A> události. Windows 7 také poskytuje více dotykové ovládání jako Win32 WM_TOUCH okno zprávy. Tato dvě rozhraní API se vzájemně vylučují na stejné HWND. Povolení touch vstup přes tablet platformy (výchozí nastavení pro aplikace WPF) zakáže WM_TOUCH zprávy. V důsledku toho pokud chcete použít WM_TOUCH a přijímat zprávy touch z grafického subsystému WPF okna, je nutné zakázat podporu předdefinované pera v grafickém subsystému WPF. To se vztahuje, třeba okno WPF hostování komponenty, která používá WM_TOUCH v situaci.  
  
 Zakázat WPF naslouchání vstup pera, odeberte všechny tablet podporu přidal okno WPF.  
  
## <a name="example"></a>Příklad  
 Následující vzorový kód ukazuje, jak odebrat podporu platformy tablet výchozí pomocí reflexe.  
  
```  
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
 [Přijetí vstupu z pera](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
