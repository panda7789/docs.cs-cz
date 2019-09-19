---
title: 'Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0'
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: c68daf2cb5687497e66ad3022ce42352a17ae0f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053441"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="95acc-102">Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="95acc-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="95acc-103">Než můžou správci nasadit aplikace Microsoft .NET Framework v systému, musí nejdřív ověřit, že je k dispozici modul runtime .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95acc-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="95acc-104">Toto téma poskytuje skript napsaný ve formátu HTML/JavaScript, který mohou správci použít k určení, zda .NET Framework k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="95acc-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95acc-105">Podrobnější informace o instalaci, nasazení a detekci .NET Framework Microsoftu najdete v diskuzi v tématu [nasazení microsoft .NET Framework verze 3,0](https://go.microsoft.com/fwlink/?LinkId=96739).</span><span class="sxs-lookup"><span data-stu-id="95acc-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="95acc-106">Zjištění řetězce uživatelského agenta .NET CLR</span><span class="sxs-lookup"><span data-stu-id="95acc-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="95acc-107">Když je nainstalovaná .NET Framework, soubor MSI přidá ".NET CLR" a číslo verze do řetězce UserAgent.</span><span class="sxs-lookup"><span data-stu-id="95acc-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="95acc-108">Následující příklad ukazuje skript vložený do jednoduché stránky HTML.</span><span class="sxs-lookup"><span data-stu-id="95acc-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="95acc-109">Skript vyhledá řetězec UserAgent a určí, zda je .NET Framework nainstalován, a zobrazí stavovou zprávu výsledků hledání.</span><span class="sxs-lookup"><span data-stu-id="95acc-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
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
  
 <span data-ttu-id="95acc-110">Pokud je vyhledávání verze .NET CLR úspěšné, zobrazí se následující typ stavové zprávy:</span><span class="sxs-lookup"><span data-stu-id="95acc-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="95acc-111">V opačném případě se zobrazí následující typ stavové zprávy:</span><span class="sxs-lookup"><span data-stu-id="95acc-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
