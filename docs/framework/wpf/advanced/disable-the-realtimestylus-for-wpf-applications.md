---
title: Zákaz RealTimeStylus pro aplikace WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: acae177e1c49a6a1161bcf48f8e2e8ac1bfe13b8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991842"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Zákaz RealTimeStylus pro aplikace WPF
Windows Presentation Foundation (WPF) má vestavěnou podporu pro zpracování dotykového vstupu v systému Windows 7. Tato podpora se dodává prostřednictvím vstupu stylusu pro tablety v reálném čase <xref:System.Windows.UIElement.OnStylusDown%2A>jako <xref:System.Windows.UIElement.OnStylusUp%2A>události, <xref:System.Windows.UIElement.OnStylusMove%2A> a. Windows 7 také nabízí vstup s více dotykovémi zprávami, jako jsou zprávy v okně Win32 WM_TOUCH. Tato dvě rozhraní API se vzájemně vylučují na stejném HWND. Povolení dotykového vstupu přes platformu tabletu (výchozí pro aplikace WPF) zakáže zprávy WM_TOUCH. V důsledku toho, abyste mohli používat WM_TOUCH k přijímání dotykových zpráv z okna WPF, musíte zakázat integrovanou podporu stylusu v WPF. To platí ve scénáři, jako je například okno WPF hostující komponentu, která používá WM_TOUCH.  
  
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
