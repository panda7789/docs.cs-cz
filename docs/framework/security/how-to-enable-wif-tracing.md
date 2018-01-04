---
title: "Postupy: Povolení WIF trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c9c3bc67d7ce59d259fec06377c5de1768a130ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="b9cad-102">Postupy: Povolení WIF trasování</span><span class="sxs-lookup"><span data-stu-id="b9cad-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="b9cad-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="b9cad-103">Applies To</span></span>  
  
-   <span data-ttu-id="b9cad-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="b9cad-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="b9cad-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="b9cad-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b9cad-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="b9cad-106">Summary</span></span>  
 <span data-ttu-id="b9cad-107">Tento postup obsahuje podrobné podrobné postupy pro povolení trasování WIF v aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b9cad-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="b9cad-108">Také poskytuje pokyny testování aplikace ověřit, jestli naslouchací proces trasování a protokol jsou správně funguje.</span><span class="sxs-lookup"><span data-stu-id="b9cad-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="b9cad-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="b9cad-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="b9cad-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="b9cad-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="b9cad-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="b9cad-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="b9cad-112">Ho můžete stáhnout z následujícího umístění: [identita a přístup](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="b9cad-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9cad-113">Povolení trasování WIF u pasivních aplikací, to znamená, aplikace, které používají protokol WS-Federation, mohou potenciálně odhalit aplikaci útoků DoS (DoS) a zpřístupnění informací škodlivý strany.</span><span class="sxs-lookup"><span data-stu-id="b9cad-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="b9cad-114">To zahrnuje pasivní RPs a pasivní STSes.</span><span class="sxs-lookup"><span data-stu-id="b9cad-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="b9cad-115">Z tohoto důvodu doporučujeme není povolit WIF trasování pro pasivní RPs nebo STSes v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="b9cad-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="b9cad-116">Obsah</span><span class="sxs-lookup"><span data-stu-id="b9cad-116">Contents</span></span>  
  
-   <span data-ttu-id="b9cad-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="b9cad-117">Objectives</span></span>  
  
-   <span data-ttu-id="b9cad-118">Přehled</span><span class="sxs-lookup"><span data-stu-id="b9cad-118">Overview</span></span>  
  
-   <span data-ttu-id="b9cad-119">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="b9cad-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b9cad-120">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="b9cad-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="b9cad-121">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="b9cad-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="b9cad-122">Cíle</span><span class="sxs-lookup"><span data-stu-id="b9cad-122">Objectives</span></span>  
  
-   <span data-ttu-id="b9cad-123">Vytvořit jednoduchou aplikaci ASP.NET, která používá WIF a vývoj služby tokenů zabezpečení z Identity a přístup</span><span class="sxs-lookup"><span data-stu-id="b9cad-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="b9cad-124">Povolení trasování a ověřte, zda je funkční</span><span class="sxs-lookup"><span data-stu-id="b9cad-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b9cad-125">Přehled</span><span class="sxs-lookup"><span data-stu-id="b9cad-125">Overview</span></span>  
 <span data-ttu-id="b9cad-126">Trasování umožňuje ladění a odstraňování potíží mnoho typů problémů s WIF, včetně tokeny, soubory cookie, deklarace identity, zprávy protokolu a další.</span><span class="sxs-lookup"><span data-stu-id="b9cad-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="b9cad-127">WIF trasování je podobné trasování WCF; Například můžete podrobností trasování do všechno kritické zprávy zobrazit všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="b9cad-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="b9cad-128">WIF trasování může být generována v **.xml** soubory nebo v **.svclog** soubory, které je možné zobrazit pomocí nástroje pro prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="b9cad-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="b9cad-129">Tento nástroj se nachází v **bin** directory sady Windows SDK instalační cesty v počítači, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="b9cad-130">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="b9cad-130">Summary of Steps</span></span>  
  
-   <span data-ttu-id="b9cad-131">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="b9cad-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="b9cad-132">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="b9cad-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="b9cad-133">Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="b9cad-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="b9cad-134">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru povolení trasování.</span><span class="sxs-lookup"><span data-stu-id="b9cad-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="b9cad-135">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b9cad-135">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="b9cad-136">Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="b9cad-137">V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b9cad-138">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="b9cad-139">Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="b9cad-140">**Identit a přístupu** se zobrazí v okně.</span><span class="sxs-lookup"><span data-stu-id="b9cad-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="b9cad-141">V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="b9cad-142">Vytvořte novou složku s názvem v **protokoly** v kořenovém **C:** jednotky, jako je třeba vidět: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="b9cad-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7.  <span data-ttu-id="b9cad-143">Přidejte následující  **\<system.diagnostics >** elementu, který chcete *Web.config* konfigurační soubor okamžitě po zavření  **\</configSections >** element, jako je třeba zobrazí:</span><span class="sxs-lookup"><span data-stu-id="b9cad-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b9cad-144">Zadaný v umístění adresáře **initializeData –** atributu musí existovat, než můžete začít protokolování.</span><span class="sxs-lookup"><span data-stu-id="b9cad-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="b9cad-145">Pokud umístění neexistuje, vytvoří se žádné protokoly.</span><span class="sxs-lookup"><span data-stu-id="b9cad-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="b9cad-146">Povolí výše uvedených nastavení konfigurace **podrobné** trasování pro WIF a výsledný protokolu, který chcete uložit **C:logsWIF.xml** souboru.</span><span class="sxs-lookup"><span data-stu-id="b9cad-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="b9cad-147">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="b9cad-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="b9cad-148">V tomto kroku budete testovat aplikace ASP.NET WIF povoleno ověření, že se mají zaznamenávat protokoly.</span><span class="sxs-lookup"><span data-stu-id="b9cad-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="b9cad-149">K testování aplikace WIF technologie ASP.NET pro úspěšné trasování</span><span class="sxs-lookup"><span data-stu-id="b9cad-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1.  <span data-ttu-id="b9cad-150">Spuštění řešení stisknutím **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="b9cad-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="b9cad-151">Můžete by měl mít výchozí domovskou stránku ASP.NET a automaticky k ověření pomocí uživatelského jména *Terry*, což je výchozí uživatel, který je vrácena službou tokenů zabezpečení vývoj.</span><span class="sxs-lookup"><span data-stu-id="b9cad-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="b9cad-152">Zavřete okno prohlížeče a pak přejděte do **C:\logs** složky.</span><span class="sxs-lookup"><span data-stu-id="b9cad-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="b9cad-153">Otevřete **C:\logs\WIF.xml** souboru pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="b9cad-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3.  <span data-ttu-id="b9cad-154">Zkontrolujte **WIF.xml** souboru a ověřte, zda obsahuje položky počínaje  **\<E2ETraceEvent >**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="b9cad-155">Bude obsahovat toto trasování  **\<TraceRecord >** elementů s popisy trasovaná aktivity, jako například **ověřování SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="b9cad-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
