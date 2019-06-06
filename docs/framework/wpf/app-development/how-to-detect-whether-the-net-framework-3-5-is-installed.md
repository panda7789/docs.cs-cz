---
title: 'Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 69dfa0eb8d9ad9b780d258a874d255484f270cfe
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690434"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="0ad89-102">Postupy: Zjištění, jestli je nainstalovaná platforma .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="0ad89-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="0ad89-103">Správci mohli nasadit aplikace Windows Presentation Foundation (WPF) v systému, který cílí na rozhraní .NET Framework 3.5, se musí nejdřív ověřit, zda modul runtime rozhraní .NET Framework 3.5 je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0ad89-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the .NET Framework 3.5, they must first confirm that the .NET Framework 3.5 runtime is present.</span></span> <span data-ttu-id="0ad89-104">Toto téma obsahuje skript napsané v HTML/JavaScript, mohou správci zjistit, jestli je rozhraní .NET Framework 3.5 v systému k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0ad89-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework 3.5 is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ad89-105">Podrobnější informace o instalaci, nasazení a zjištění rozhraní .NET Framework najdete v článku [nainstalovat rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="0ad89-105">For more detailed information on installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ad89-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ad89-106">Example</span></span>  
 <span data-ttu-id="0ad89-107">Při instalaci rozhraní .NET Framework 3.5 MSI přidá řetězec UserAgent ".NET CLR" a čísla verze.</span><span class="sxs-lookup"><span data-stu-id="0ad89-107">When the .NET Framework 3.5 is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="0ad89-108">Následující příklad ukazuje skript součástí jednoduché stránky HTML.</span><span class="sxs-lookup"><span data-stu-id="0ad89-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="0ad89-109">Skript hledá řetězec UserAgent k určení, jestli je nainstalované rozhraní .NET Framework 3.5 a stavová zpráva se zobrazí ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="0ad89-109">The script searches the UserAgent string to determine whether the .NET Framework 3.5 is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ad89-110">Tento skript je určená pro aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0ad89-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="0ad89-111">Jiné prohlížeče nemusí obsahovat informace o .NET CLR v řetězec UserAgent.</span><span class="sxs-lookup"><span data-stu-id="0ad89-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
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
  
 <span data-ttu-id="0ad89-112">Pokud hledání pro verzi ".NET CLR" je úspěšné, zobrazí se následující typ stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="0ad89-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="0ad89-113">V opačném případě se zobrazí následující typ stavová zpráva:</span><span class="sxs-lookup"><span data-stu-id="0ad89-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="0ad89-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ad89-114">See also</span></span>

- [<span data-ttu-id="0ad89-115">Zjištění, jestli je nainstalovaná platforma .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="0ad89-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
