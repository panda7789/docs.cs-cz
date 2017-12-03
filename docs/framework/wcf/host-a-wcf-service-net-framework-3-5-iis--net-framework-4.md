---
title: "Postupy: Hostování služby WCF napsané pomocí .NET Framework 3.5 v IIS a běžící pod .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88d9b6b8b4aa1d551e292057e0fecf746b17cecd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="be868-102">Postupy: Hostování služby WCF napsané pomocí .NET Framework 3.5 v IIS a běžící pod .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="be868-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>
<span data-ttu-id="be868-103">Při hostování [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby napsané pomocí [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] na počítač se systémem [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], může dojít <xref:System.ServiceModel.ProtocolException> s následujícím textem.</span><span class="sxs-lookup"><span data-stu-id="be868-103">When hosting a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service written with [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] on a machine running [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="be868-104">Nebo pokud se pokusíte vyhledat soubor .svc služby, mohou se zobrazit chybová stránka s následujícím textem.</span><span class="sxs-lookup"><span data-stu-id="be868-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="be868-105">K těmto chybám, protože je spuštěna služba IIS je spuštěna v rámci domény aplikace [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] a služby WCF je očekáván běh [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be868-105">These errors occur because the application domain IIS is running within is running [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] and the WCF service is expecting to run under [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="be868-106">Toto téma vysvětluje změny vyžadované k získání službu spustit.</span><span class="sxs-lookup"><span data-stu-id="be868-106">This topic explains the modifications required to get the service to run.</span></span>  
  
 <span data-ttu-id="be868-107">Poté vyhledejte <`compilers`> elementu a změňte možnost zprostředkovatele CompilerVersion s hodnotou 4.0.</span><span class="sxs-lookup"><span data-stu-id="be868-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="be868-108">Ve výchozím nastavení, jsou uvedeny dvě <`compiler`> elementů v rámci <`compilers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="be868-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="be868-109">Možnost poskytovatele CompilerVersion pro obě jak je znázorněno v následujícím příkladu je nutné aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="be868-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="be868-110">Přidat atribut vyžaduje targetFramework</span><span class="sxs-lookup"><span data-stu-id="be868-110">Add the required targetFramework attribute</span></span>  
  
1.  <span data-ttu-id="be868-111">Otevřete soubor Web.config služby a podívejte se <`compilation`> elementu.</span><span class="sxs-lookup"><span data-stu-id="be868-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2.  <span data-ttu-id="be868-112">Přidat `targetFramework` atribut <`compilation`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="be868-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  <span data-ttu-id="be868-113">Najít <`compilers`> elementu a změňte možnost zprostředkovatele CompilerVersion s hodnotou 4.0.</span><span class="sxs-lookup"><span data-stu-id="be868-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="be868-114">Ve výchozím nastavení, jsou uvedeny dvě <`compiler`> elementů v rámci <`compilers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="be868-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="be868-115">Možnost poskytovatele CompilerVersion pro obě jak je znázorněno v následujícím příkladu je nutné aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="be868-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
