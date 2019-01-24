---
title: Zákaz RealTimeStylus pro aplikace WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 7b97a451c52b72ee1ddcec5c58e1848a0b10fb7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616907"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Zákaz RealTimeStylus pro aplikace WPF
Windows Presentation Foundation (WPF) má vestavěnou podporou pro zpracování dotykové ovládání Windows 7. Podpora prochází tablet platforma v reálném čase tužkou jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, a <xref:System.Windows.UIElement.OnStylusMove%2A> události. Windows 7 také poskytuje více dotykové ovládání jako Win32 WM_TOUCH zprávy okna. Tato dvě rozhraní API se vzájemně vylučují na stejné HWND. Povolení touch vstupních přes tablet platformy (výchozí nastavení pro aplikace WPF) zakáže WM_TOUCH zprávy. V důsledku toho použít WM_TOUCH pro příjem zpráv touch z okna WPF, musíte zakázat podporu integrovanou stylus v subsystému WPF. To platí ve scénáři, jako je například okno WPF, který je hostitelem součásti, která používá WM_TOUCH.  
  
 Zakázat WPF naslouchání na vstup pomocí pera, odeberte všechny tablet podporu přidal okno WPF.  
  
## <a name="example"></a>Příklad  
 Následující ukázkový kód ukazuje, jak odebrat výchozí podporu platformy tabletu pomocí reflexe.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Přijetí vstupu z pera](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
