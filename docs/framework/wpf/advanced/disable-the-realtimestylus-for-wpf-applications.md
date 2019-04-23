---
title: Zákaz RealTimeStylus pro aplikace WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124680"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="04cbe-102">Zákaz RealTimeStylus pro aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="04cbe-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="04cbe-103">Windows Presentation Foundation (WPF) má vestavěnou podporou pro zpracování dotykové ovládání Windows 7. Podpora prochází tablet platforma v reálném čase tužkou jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, a <xref:System.Windows.UIElement.OnStylusMove%2A> události.</span><span class="sxs-lookup"><span data-stu-id="04cbe-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="04cbe-104">Windows 7 také poskytuje více dotykové ovládání jako Win32 WM_TOUCH zprávy okna.</span><span class="sxs-lookup"><span data-stu-id="04cbe-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="04cbe-105">Tato dvě rozhraní API se vzájemně vylučují na stejné HWND.</span><span class="sxs-lookup"><span data-stu-id="04cbe-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="04cbe-106">Povolení touch vstupních přes tablet platformy (výchozí nastavení pro aplikace WPF) zakáže WM_TOUCH zprávy.</span><span class="sxs-lookup"><span data-stu-id="04cbe-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="04cbe-107">V důsledku toho použít WM_TOUCH pro příjem zpráv touch z okna WPF, musíte zakázat podporu integrovanou stylus v subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="04cbe-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="04cbe-108">To platí ve scénáři, jako je například okno WPF, který je hostitelem součásti, která používá WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="04cbe-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="04cbe-109">Zakázat WPF naslouchání na vstup pomocí pera, odeberte všechny tablet podporu přidal okno WPF.</span><span class="sxs-lookup"><span data-stu-id="04cbe-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04cbe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="04cbe-110">Example</span></span>  
 <span data-ttu-id="04cbe-111">Následující ukázkový kód ukazuje, jak odebrat výchozí podporu platformy tabletu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="04cbe-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04cbe-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04cbe-112">See also</span></span>

- [<span data-ttu-id="04cbe-113">Přijetí vstupu z pera</span><span class="sxs-lookup"><span data-stu-id="04cbe-113">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
