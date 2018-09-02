---
title: 'Postupy: Povolení trasování WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 17650e06cb505dd778a9c0980c2a32fda8099cb4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407570"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="e151b-102">Postupy: Povolení trasování WIF</span><span class="sxs-lookup"><span data-stu-id="e151b-102">How To: Enable WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="e151b-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="e151b-103">Applies To</span></span>  
  
-   <span data-ttu-id="e151b-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e151b-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e151b-105">ASP.NET® webových formulářů</span><span class="sxs-lookup"><span data-stu-id="e151b-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e151b-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="e151b-106">Summary</span></span>  
 <span data-ttu-id="e151b-107">Tento návod obsahuje podrobné podrobné postupy pro povolení trasování WIF aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e151b-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="e151b-108">Také poskytuje pokyny k testování aplikace pro ověření, že naslouchací proces trasování a protokol fungují správně.</span><span class="sxs-lookup"><span data-stu-id="e151b-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="e151b-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="e151b-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="e151b-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="e151b-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="e151b-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="e151b-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="e151b-112">Můžete ho stáhnout z následujícího umístění: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="e151b-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e151b-113">Povolení trasování WIF u pasivních aplikací, to znamená, aplikace používající protokol WS-Federation, může potenciálně aplikaci vystavit útoky na dostupnost služby (DoS) a zpřístupnění informací škodlivý straně.</span><span class="sxs-lookup"><span data-stu-id="e151b-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="e151b-114">To zahrnuje pasivní RPs a pasivní STSes.</span><span class="sxs-lookup"><span data-stu-id="e151b-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="e151b-115">Z tohoto důvodu doporučujeme není povolit trasování WIF pro pasivní RPs nebo STSes v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="e151b-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e151b-116">Obsah</span><span class="sxs-lookup"><span data-stu-id="e151b-116">Contents</span></span>  
  
-   <span data-ttu-id="e151b-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="e151b-117">Objectives</span></span>  
  
-   <span data-ttu-id="e151b-118">Přehled</span><span class="sxs-lookup"><span data-stu-id="e151b-118">Overview</span></span>  
  
-   <span data-ttu-id="e151b-119">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e151b-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e151b-120">Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="e151b-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="e151b-121">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e151b-121">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e151b-122">Cíle</span><span class="sxs-lookup"><span data-stu-id="e151b-122">Objectives</span></span>  
  
-   <span data-ttu-id="e151b-123">Vytvořit jednoduchou aplikaci ASP.NET, která používá technologie WIF a služba STS pro vývoj od Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="e151b-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="e151b-124">Povolení trasování a ověřte, že je funkční</span><span class="sxs-lookup"><span data-stu-id="e151b-124">Enable tracing and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e151b-125">Přehled</span><span class="sxs-lookup"><span data-stu-id="e151b-125">Overview</span></span>  
 <span data-ttu-id="e151b-126">Trasování umožňuje ladění a řešení potíží s mnoha typy problémů pomocí technologie WIF, včetně tokeny, soubory cookie, deklarace identity, zprávách protokolů a dalších.</span><span class="sxs-lookup"><span data-stu-id="e151b-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="e151b-127">Trasování WIF je podobný trasování WCF; Například můžete nastavit úroveň podrobností trasování vše od kritické zprávy zobrazíte všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="e151b-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="e151b-128">Technologie WIF trasování mohou být generovány v **.xml** soubory nebo v **.svclog** soubory, které je možné zobrazit pomocí nástroje prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="e151b-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="e151b-129">Tento nástroj se nachází v **bin** adresář sady Windows SDK cesta pro instalaci na počítač, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="e151b-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e151b-130">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="e151b-130">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e151b-131">Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="e151b-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
  
-   <span data-ttu-id="e151b-132">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e151b-132">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="e151b-133">Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="e151b-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>  
 <span data-ttu-id="e151b-134">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru trasování.</span><span class="sxs-lookup"><span data-stu-id="e151b-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e151b-135">Chcete-li vytvořit jednoduchou aplikaci ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e151b-135">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e151b-136">Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e151b-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="e151b-137">V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="e151b-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e151b-138">V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.</span><span class="sxs-lookup"><span data-stu-id="e151b-138">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="e151b-139">Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.</span><span class="sxs-lookup"><span data-stu-id="e151b-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="e151b-140">**Identit a přístupu** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="e151b-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="e151b-141">V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="e151b-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="e151b-142">Vytvořte novou složku v s názvem **protokoly** v kořenovém adresáři **C:** jednotky, jako je třeba je znázorněno: **C:\logs**</span><span class="sxs-lookup"><span data-stu-id="e151b-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>  
  
7.  <span data-ttu-id="e151b-143">Přidejte následující  **\<system.diagnostics >** elementu *Web.config* konfigurační soubor hned za uzavírací  **\</configSections >** element, jako je třeba zobrazí:</span><span class="sxs-lookup"><span data-stu-id="e151b-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>  
  
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
    >  <span data-ttu-id="e151b-144">Zadaný v umístění adresáře **initializeData** atribut musí existovat předtím, než můžete začít protokolování.</span><span class="sxs-lookup"><span data-stu-id="e151b-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="e151b-145">Pokud umístění ještě neexistuje, vytvoří se žádné protokoly.</span><span class="sxs-lookup"><span data-stu-id="e151b-145">If the location does not exist, no logs will be created.</span></span>  
  
     <span data-ttu-id="e151b-146">Výše uvedených nastavení konfigurace se umožní **Verbose** trasování pro technologie WIF a výsledné protokol **C:logsWIF.xml** souboru.</span><span class="sxs-lookup"><span data-stu-id="e151b-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="e151b-147">Krok 2 – otestování řešení</span><span class="sxs-lookup"><span data-stu-id="e151b-147">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="e151b-148">V tomto kroku otestujete aplikaci technologie ASP.NET s podporou technologie WIF ověření, že jsou zaznamenávány protokoly.</span><span class="sxs-lookup"><span data-stu-id="e151b-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="e151b-149">Chcete-li otestovat aplikaci technologie ASP.NET s podporou technologie WIF pro úspěšné trasování</span><span class="sxs-lookup"><span data-stu-id="e151b-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>  
  
1.  <span data-ttu-id="e151b-150">Spuštění řešení stisknutím kombinace kláves **F5** klíč.</span><span class="sxs-lookup"><span data-stu-id="e151b-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="e151b-151">Měli byste se výchozí domovskou stránku ASP.NET a automaticky ověřuje se uživatelské jméno *Terry*, což je výchozí uživatel, který je vrácen služba STS pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="e151b-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="e151b-152">Zavřete okno prohlížeče a přejděte **C:\logs** složky.</span><span class="sxs-lookup"><span data-stu-id="e151b-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="e151b-153">Otevřít **C:\logs\WIF.xml** soubor pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="e151b-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>  
  
3.  <span data-ttu-id="e151b-154">Zkontrolujte **WIF.xml** souboru a ověřte, zda obsahuje položky počínaje  **\<E2ETraceEvent >**.</span><span class="sxs-lookup"><span data-stu-id="e151b-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="e151b-155">Toto trasování bude obsahovat  **\<TraceRecord >** prvky s popisem trasovaných aktivity, jako například **ověření tokenu SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="e151b-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
