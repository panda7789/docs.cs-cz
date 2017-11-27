---
title: "Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e013c9426507e20da05df26932a1f9cf1e5df761
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="17d99-102">Postupy: Zjištění, zda je instalována platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="17d99-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="17d99-103">Předtím, než správci mohou nasadit [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] aplikace v systému, se musí nejprve potvrďte, že [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] runtime je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="17d99-103">Before administrators can deploy [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] applications on a system, they must first confirm that the [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] runtime is present.</span></span> <span data-ttu-id="17d99-104">Toto téma obsahuje skript napsaný v HTML/JavaScript, která správcům umožňuje určit, zda [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] je k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="17d99-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17d99-105">Podrobnější informace o instalaci, nasazování a zjišťování [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], viz popis v [nasazení Microsoft .NET Framework verze 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span><span class="sxs-lookup"><span data-stu-id="17d99-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="17d99-106">Zjištění řetězce ".NET CLR" User-Agent</span><span class="sxs-lookup"><span data-stu-id="17d99-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="17d99-107">Když [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] je nainstalovaná, soubor MSI přidá ".NET CLR" a číslo verze řetězec UserAgent.</span><span class="sxs-lookup"><span data-stu-id="17d99-107">When [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="17d99-108">Následující příklad ukazuje skript vložený do jednoduchá stránka HTML.</span><span class="sxs-lookup"><span data-stu-id="17d99-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="17d99-109">Skript prohledá řetězec UserAgent k určení zda [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] je nainstalován a zobrazí zprávu o stavu ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="17d99-109">The script searches the UserAgent string to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
```  
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
  
 <span data-ttu-id="17d99-110">Je-li hledat verze ".NET CLR" úspěšný, zobrazí se následující typ stavové zprávy:</span><span class="sxs-lookup"><span data-stu-id="17d99-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="17d99-111">Jinak zobrazí se následující typ stavové zprávy:</span><span class="sxs-lookup"><span data-stu-id="17d99-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
