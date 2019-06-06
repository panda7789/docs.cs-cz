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
ms.openlocfilehash: f84a0a2af43931b3ada1f674390ec5d841b79a1c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690428"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Postupy: Zjištění, jestli je instalovaný modulu plug-in WPF pro Firefox

Umožňuje Windows Presentation Foundation (WPF) modul plugin pro Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volné soubory XAML pro spuštění v prohlížeči Mozilla Firefox. Toto téma obsahuje skript napsané v HTML a JavaScript, která správcům umožňuje určit, jestli je nainstalovaná modulu Plugin WPF pro Firefox.

> [!NOTE]
> Další informace o instalaci, nasazení a zjištění rozhraní .NET Framework naleznete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md).

## <a name="example"></a>Příklad

Při instalaci rozhraní .NET Framework 3.5, klientský počítač je nakonfigurovaný modul plugin WPF pro Firefox. Následující ukázkový skript kontroluje modulu Plugin WPF pro Firefox a zobrazí příslušnou stavovou zprávu.

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

Kontrola modulu Plugin WPF pro Firefox je úspěšný, zobrazí se následující stavová zpráva:

`The WPF plug-in for Firefox is installed.`

V opačném případě se zobrazí následující zpráva stavu:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Viz také:

- [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Přehled aplikací Prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md)
