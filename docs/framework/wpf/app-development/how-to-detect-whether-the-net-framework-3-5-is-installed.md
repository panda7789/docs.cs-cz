---
title: 'Postupy: zjištění, zda je nainstalována rozhraní .NET Framework 3.5'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 0d0f99dfa88216d0d768895ea751b0f62eccf701
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>Postupy: zjištění, zda je nainstalována rozhraní .NET Framework 3.5
Než správci můžete nasadit aplikace Windows Presentation Foundation (WPF) v systému, která je cílena [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], se musí nejprve potvrďte, že [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime je k dispozici. Toto téma obsahuje skript napsaný v HTML/JavaScript, která správcům umožňuje určit, zda [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je k dispozici v systému.  
  
> [!NOTE]
>  Podrobnější informace o instalaci, nasazování a zjišťování [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], najdete v části [instalaci rozhraní .NET Framework pro vývojáře](../../../../docs/framework/install/guide-for-developers.md).  
  
## <a name="example"></a>Příklad  
 Když [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalovaná, soubor MSI přidá ".NET CLR" a číslo verze řetězec UserAgent. Následující příklad ukazuje skript vložený do jednoduchá stránka HTML. Skript prohledá řetězec UserAgent k určení zda [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalován a zobrazí zprávu o stavu ve výsledcích hledání.  
  
> [!NOTE]
>  Tento skript je určená pro Internet Explorer. Jiné prohlížeče nesmí obsahovat informace o modulu .NET CLR v řetězec UserAgent.  
  
```  
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
  
 Je-li hledat verze ".NET CLR" úspěšný, zobrazí se následující typ stavové zprávy:  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 Jinak zobrazí se následující typ stavové zprávy:  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>Viz také  
 [Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
