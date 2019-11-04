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
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Postupy: Zjištění instalovaného modulu plugin WPF pro Firefox

Modul plug-in Windows Presentation Foundation (WPF) pro Firefox umožňuje používat aplikace prohlížeče XAML (XBAP) a volné soubory XAML ke spuštění v prohlížeči Mozilla Firefox. Toto téma poskytuje skript napsaný v HTML a JavaScriptu, který můžou správci použít k určení, jestli je nainstalovaný modul plug-in WPF pro Firefox.

> [!NOTE]
> Další informace o instalaci, nasazení a detekci .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](../../install/guide-for-developers.md).

## <a name="example"></a>Příklad

Pokud je nainstalovaná .NET Framework 3,5, klientský počítač je nakonfigurovaný s modulem plug-in WPF pro Firefox. Následující ukázkový skript zkontroluje modul plug-in WPF pro prohlížeč Firefox a pak zobrazí příslušnou stavovou zprávu.

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

Pokud je ověření modulu plug-in WPF pro Firefox úspěšné, zobrazí se následující stavová zpráva:

`The WPF plug-in for Firefox is installed.`

V opačném případě se zobrazí následující stavová zpráva:

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Viz také:

- [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Přehled aplikací Prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md)
