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
ms.openlocfilehash: ba411d662a8e5b0c4727e23c8d507e8924b6e9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546985"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Postupy: Zjištění instalovaného modulu plugin WPF pro Firefox
Umožňuje systému Windows Presentation Foundation (WPF) modul plug-in pro Firefox [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a ztrátě souborů XAML pro spouštění v prohlížeči Mozilla Firefox. Toto téma obsahuje skript napsaný v HTML a JavaScript, který mohou správci zjistit, zda je nainstalována WPF modulu plug-in pro Firefox.  
  
> [!NOTE]
>  Další informace o instalaci, nasazování a zjišťování [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], najdete v části [instalaci rozhraní .NET Framework pro vývojáře](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Příklad  
 Když [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalovaná, klientský počítač je nakonfigurován v grafickém subsystému WPF, která se modul plug-in pro Firefox. Následující ukázkový skript kontroluje pro modul plug-in WPF Firefox a poté zobrazí zprávu příslušný stav.  
  
```  
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
  
 Pokud kontrolu pro modul plug-in WPF Firefox úspěšné, se zobrazí následující zprávu:  
  
 `The WPF plug-in for Firefox is installed.`  
  
 Jinak se zobrazí následující zprávu:  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>Viz také  
 [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [Přehled aplikací Prohlížeče WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
