---
title: 'Postupy: Zjištění instalovaného modulu plugin WPF pro Firefox'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: fdc7b516c316c7efc7056b549baf43191a5aedd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423750"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="5beff-102">Postupy: Zjištění instalovaného modulu plugin WPF pro Firefox</span><span class="sxs-lookup"><span data-stu-id="5beff-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="5beff-103">Modul plug-in Windows Presentation Foundation (WPF) pro Firefox umožňuje používat aplikace prohlížeče XAML (XBAP) a volné soubory XAML ke spuštění v prohlížeči Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="5beff-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables XAML browser applications (XBAPs) and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="5beff-104">Toto téma poskytuje skript napsaný v HTML a JavaScriptu, který můžou správci použít k určení, jestli je nainstalovaný modul plug-in WPF pro Firefox.</span><span class="sxs-lookup"><span data-stu-id="5beff-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="5beff-105">Další informace o instalaci, nasazení a detekci .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="5beff-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="5beff-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5beff-106">Example</span></span>

<span data-ttu-id="5beff-107">Pokud je nainstalovaná .NET Framework 3,5, klientský počítač je nakonfigurovaný s modulem plug-in WPF pro Firefox.</span><span class="sxs-lookup"><span data-stu-id="5beff-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="5beff-108">Následující ukázkový skript zkontroluje modul plug-in WPF pro prohlížeč Firefox a pak zobrazí příslušnou stavovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="5beff-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

<span data-ttu-id="5beff-109">Pokud je ověření modulu plug-in WPF pro Firefox úspěšné, zobrazí se následující stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="5beff-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="5beff-110">V opačném případě se zobrazí následující stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="5beff-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="5beff-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5beff-111">See also</span></span>

- [<span data-ttu-id="5beff-112">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="5beff-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="5beff-113">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="5beff-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="5beff-114">Přehled aplikací Prohlížeče WPF XAML</span><span class="sxs-lookup"><span data-stu-id="5beff-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
