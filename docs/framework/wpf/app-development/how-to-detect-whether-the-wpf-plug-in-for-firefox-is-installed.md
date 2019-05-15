---
title: 'Postupy: Zjištění, jestli je instalovaný modulu plug-in WPF pro Firefox'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 5ae2f39883c8edd7be912bfeb8326c14ca38704a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592616"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="632e1-102">Postupy: Zjištění, jestli je instalovaný modulu plug-in WPF pro Firefox</span><span class="sxs-lookup"><span data-stu-id="632e1-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="632e1-103">Umožňuje Windows Presentation Foundation (WPF) modul plugin pro Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volné soubory XAML pro spuštění v prohlížeči Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="632e1-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="632e1-104">Toto téma obsahuje skript napsané v HTML a JavaScript, která správcům umožňuje určit, jestli je nainstalovaná modulu Plugin WPF pro Firefox.</span><span class="sxs-lookup"><span data-stu-id="632e1-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="632e1-105">Další informace o instalaci, nasazení a zjištění rozhraní .NET Framework naleznete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="632e1-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="632e1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="632e1-106">Example</span></span>

<span data-ttu-id="632e1-107">Když [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalovaný, klientský počítač je nakonfigurovaný modul plugin WPF pro Firefox.</span><span class="sxs-lookup"><span data-stu-id="632e1-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="632e1-108">Následující ukázkový skript kontroluje modulu Plugin WPF pro Firefox a zobrazí příslušnou stavovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="632e1-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

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

<span data-ttu-id="632e1-109">Kontrola modulu Plugin WPF pro Firefox je úspěšný, zobrazí se následující stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="632e1-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="632e1-110">V opačném případě se zobrazí následující zpráva stavu:</span><span class="sxs-lookup"><span data-stu-id="632e1-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="632e1-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="632e1-111">See also</span></span>

- [<span data-ttu-id="632e1-112">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="632e1-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="632e1-113">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="632e1-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="632e1-114">Přehled aplikací Prohlížeče WPF XAML</span><span class="sxs-lookup"><span data-stu-id="632e1-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
