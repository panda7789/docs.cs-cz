---
title: 'Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 18e5c819eb4deb62208280816d11dce0940d134d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053432"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5
Než můžou správci nasadit aplikace Windows Presentation Foundation (WPF) v systému, který cílí na .NET Framework 3,5, musí nejdřív ověřit, že je přítomen modul runtime .NET Framework 3,5. Toto téma poskytuje skript napsaný ve formátu HTML/JavaScript, který mohou správci použít k určení, zda je v systému k dispozici .NET Framework 3,5.  
  
> [!NOTE]
> Podrobnější informace o instalaci, nasazení a detekci .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](../../install/guide-for-developers.md).  
  
## <a name="example"></a>Příklad  
 Pokud je nainstalovaná .NET Framework 3,5, soubor MSI přidá ".NET CLR" a číslo verze do řetězce UserAgent. Následující příklad ukazuje skript vložený do jednoduché stránky HTML. Skript vyhledá řetězec UserAgent a určí, zda je nainstalovaná .NET Framework 3,5, a zobrazí stavovou zprávu výsledků hledání.  
  
> [!NOTE]
> Tento skript je určený pro Internet Explorer. Jiné prohlížeče nemusí obsahovat informace .NET CLR v řetězci UserAgent.  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 V opačném případě se zobrazí následující typ stavové zprávy:  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>Viz také:

- [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
