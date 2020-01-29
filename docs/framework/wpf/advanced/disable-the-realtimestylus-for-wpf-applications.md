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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="8b668-102">Zákaz RealTimeStylus pro aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="8b668-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="8b668-103">Windows Presentation Foundation (WPF) má vestavěnou podporu pro zpracování dotykového vstupu v systému Windows 7.</span><span class="sxs-lookup"><span data-stu-id="8b668-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="8b668-104">Tato podpora se dodává prostřednictvím vstupu stylusu pro tablety v reálném čase jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>a <xref:System.Windows.UIElement.OnStylusMove%2A>ch událostí.</span><span class="sxs-lookup"><span data-stu-id="8b668-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="8b668-105">Windows 7 také nabízí vstup s více dotykovémi zprávami jako WM_TOUCH zprávy okna Win32.</span><span class="sxs-lookup"><span data-stu-id="8b668-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="8b668-106">Tato dvě rozhraní API se vzájemně vylučují na stejném HWND.</span><span class="sxs-lookup"><span data-stu-id="8b668-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="8b668-107">Povolení dotykového vstupu přes platformu tabletu (výchozí pro aplikace WPF) zakáže WM_TOUCH zprávy.</span><span class="sxs-lookup"><span data-stu-id="8b668-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="8b668-108">V důsledku toho, aby bylo možné použít WM_TOUCH pro příjem dotykových zpráv z okna WPF, je nutné zakázat integrovanou podporu stylusu v WPF.</span><span class="sxs-lookup"><span data-stu-id="8b668-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="8b668-109">To platí ve scénáři, jako je například okno WPF hostující komponentu, která používá WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="8b668-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="8b668-110">Chcete-li zakázat naslouchání WPF vstupu stylusu, odeberte všechny podpory pro tablety přidané v okně WPF.</span><span class="sxs-lookup"><span data-stu-id="8b668-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b668-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b668-111">Example</span></span>  
 <span data-ttu-id="8b668-112">Následující vzorový kód ukazuje, jak odebrat výchozí podporu platformy pro tablety pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="8b668-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b668-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b668-113">See also</span></span>

- [<span data-ttu-id="8b668-114">Přijetí vstupu z pera</span><span class="sxs-lookup"><span data-stu-id="8b668-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
