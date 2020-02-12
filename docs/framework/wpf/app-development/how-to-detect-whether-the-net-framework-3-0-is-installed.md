---
title: 'Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0'
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 41010e615b6b3d10ebf6adc0e3f871873e94f409
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124452"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a>Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0
Než můžou správci nasadit aplikace Microsoft .NET Framework v systému, musí nejdřív ověřit, že je k dispozici modul runtime .NET Framework. Toto téma poskytuje skript napsaný ve formátu HTML/JavaScript, který mohou správci použít k určení, zda .NET Framework k dispozici v systému.  
  
> [!NOTE]
> Podrobnější informace o instalaci, nasazení a detekci .NET Framework Microsoftu najdete v diskuzi v tématu [nasazení microsoft .NET Framework verze 3,0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a>Zjištění řetězce uživatelského agenta .NET CLR  
 Když je nainstalovaná .NET Framework, soubor MSI přidá ".NET CLR" a číslo verze do řetězce UserAgent. Následující příklad ukazuje skript vložený do jednoduché stránky HTML. Skript vyhledá řetězec UserAgent a určí, zda je .NET Framework nainstalován, a zobrazí stavovou zprávu výsledků hledání.  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 Pokud je vyhledávání verze .NET CLR úspěšné, zobrazí se následující typ stavové zprávy:  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 V opačném případě se zobrazí následující typ stavové zprávy:  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
