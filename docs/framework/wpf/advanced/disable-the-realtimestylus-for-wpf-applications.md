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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="48606-102">Zákaz RealTimeStylus pro aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="48606-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="48606-103">Windows Presentation Foundation (WPF) má vestavěnou podporu pro zpracování dotykového vstupu systému Windows 7.</span><span class="sxs-lookup"><span data-stu-id="48606-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="48606-104">Podpora přichází prostřednictvím vstupu stylusu platformy <xref:System.Windows.UIElement.OnStylusDown%2A>tabletu v reálném čase jako , <xref:System.Windows.UIElement.OnStylusUp%2A>a <xref:System.Windows.UIElement.OnStylusMove%2A> události.</span><span class="sxs-lookup"><span data-stu-id="48606-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="48606-105">Windows 7 také poskytuje multi-touch vstup jako Win32 WM_TOUCH okno zprávy.</span><span class="sxs-lookup"><span data-stu-id="48606-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="48606-106">Tato dvě api se vzájemně vylučují na stejném HWND.</span><span class="sxs-lookup"><span data-stu-id="48606-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="48606-107">Povolenídotykového vstupu prostřednictvím platformy tabletu (výchozí pro aplikace WPF) zakáže WM_TOUCH zprávy.</span><span class="sxs-lookup"><span data-stu-id="48606-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="48606-108">V důsledku toho chcete použít WM_TOUCH pro příjem dotykových zpráv z okna WPF, je nutné zakázat vestavěnou podporu stylusu v WPF.</span><span class="sxs-lookup"><span data-stu-id="48606-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="48606-109">To je použitelné ve scénáři, jako je například okno WPF hostování komponenty, která používá WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="48606-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="48606-110">Chcete-li zakázat wpf poslech stylus vstup, odeberte všechny podpory tabletu přidané oknem WPF.</span><span class="sxs-lookup"><span data-stu-id="48606-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48606-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="48606-111">Example</span></span>  
 <span data-ttu-id="48606-112">Následující ukázkový kód ukazuje, jak odebrat výchozí podporu platformy tabletu pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="48606-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48606-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="48606-113">See also</span></span>

- [<span data-ttu-id="48606-114">Přijetí vstupu z pera</span><span class="sxs-lookup"><span data-stu-id="48606-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
