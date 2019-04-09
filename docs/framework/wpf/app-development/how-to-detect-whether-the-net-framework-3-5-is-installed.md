---
title: 'Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: af2428ece79803953b8c90431d905824dd18fec8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074635"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="33ee3-102">Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="33ee3-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="33ee3-103">Správci mohli nasadit aplikace Windows Presentation Foundation (WPF) v systému, který se zaměřuje [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], se musí nejdřív ověřit, která [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] modul runtime je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="33ee3-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="33ee3-104">Toto téma obsahuje skript napsané v HTML/JavaScript, která správcům umožňuje určit, zda [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="33ee3-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33ee3-105">Podrobné informace o instalaci, nasazení a zjištění [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], naleznete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="33ee3-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33ee3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="33ee3-106">Example</span></span>  
 <span data-ttu-id="33ee3-107">Když [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalovaný, MSI přidá ".NET CLR" a číslo verze na řetězec UserAgent.</span><span class="sxs-lookup"><span data-stu-id="33ee3-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="33ee3-108">Následující příklad ukazuje skript součástí jednoduché stránky HTML.</span><span class="sxs-lookup"><span data-stu-id="33ee3-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="33ee3-109">Skript hledá řetězec UserAgent k určení, zda [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] je nainstalována a stavovou zprávu se zobrazí ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="33ee3-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33ee3-110">Tento skript je určená pro aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="33ee3-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="33ee3-111">Jiné prohlížeče nemusí obsahovat informace o .NET CLR v řetězec UserAgent.</span><span class="sxs-lookup"><span data-stu-id="33ee3-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
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
  
 <span data-ttu-id="33ee3-112">Pokud hledání pro verzi ".NET CLR" je úspěšné, zobrazí se následující typ stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="33ee3-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="33ee3-113">V opačném případě se zobrazí následující typ stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="33ee3-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="33ee3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33ee3-114">See also</span></span>

- [<span data-ttu-id="33ee3-115">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="33ee3-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
