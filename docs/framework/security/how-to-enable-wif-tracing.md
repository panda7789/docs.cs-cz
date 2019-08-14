---
title: 'Postupy: Povolení trasování WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971507"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="eebe5-102">Postupy: Povolení trasování WIF</span><span class="sxs-lookup"><span data-stu-id="eebe5-102">How To: Enable WIF Tracing</span></span>

## <a name="applies-to"></a><span data-ttu-id="eebe5-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="eebe5-103">Applies To</span></span>

- <span data-ttu-id="eebe5-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="eebe5-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="eebe5-105">Webové formuláře ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="eebe5-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="eebe5-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="eebe5-106">Summary</span></span>

<span data-ttu-id="eebe5-107">V tomto postupu najdete podrobné postupy pro povolení WIF trasování v aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="eebe5-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="eebe5-108">Poskytuje také pokyny pro testování aplikace za účelem ověření, že naslouchací proces trasování a protokol fungují správně.</span><span class="sxs-lookup"><span data-stu-id="eebe5-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="eebe5-109">Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="eebe5-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="eebe5-110">Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely.</span><span class="sxs-lookup"><span data-stu-id="eebe5-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="eebe5-111">Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="eebe5-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="eebe5-112">Dá se stáhnout z následujícího umístění: [Nástroj identity and Access](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="eebe5-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eebe5-113">Povolení trasování WIF pro pasivní aplikace, tedy aplikací, které používají protokol WS-Federation, může potenciálně vystavit aplikaci útokům DOS (Denial of Service) nebo vyzrazení informací pro osobu, která je škodlivá.</span><span class="sxs-lookup"><span data-stu-id="eebe5-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="eebe5-114">Zahrnuje to pasivní RPs i pasivní STSes.</span><span class="sxs-lookup"><span data-stu-id="eebe5-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="eebe5-115">Z tohoto důvodu doporučujeme, abyste nepovolili trasování WIF pro pasivní RPs nebo STSes v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="eebe5-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>

## <a name="contents"></a><span data-ttu-id="eebe5-116">Obsah</span><span class="sxs-lookup"><span data-stu-id="eebe5-116">Contents</span></span>

- <span data-ttu-id="eebe5-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="eebe5-117">Objectives</span></span>

- <span data-ttu-id="eebe5-118">Přehled</span><span class="sxs-lookup"><span data-stu-id="eebe5-118">Overview</span></span>

- <span data-ttu-id="eebe5-119">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="eebe5-119">Summary of Steps</span></span>

- <span data-ttu-id="eebe5-120">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="eebe5-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="eebe5-121">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="eebe5-121">Step 2 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="eebe5-122">Cíle</span><span class="sxs-lookup"><span data-stu-id="eebe5-122">Objectives</span></span>

- <span data-ttu-id="eebe5-123">Vytvoření jednoduché aplikace ASP.NET, která používá WIF a vývoj STS z nástroje Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="eebe5-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>

- <span data-ttu-id="eebe5-124">Povolit trasování a ověřit, zda funguje</span><span class="sxs-lookup"><span data-stu-id="eebe5-124">Enable tracing and verify that it is working</span></span>

## <a name="overview"></a><span data-ttu-id="eebe5-125">Přehled</span><span class="sxs-lookup"><span data-stu-id="eebe5-125">Overview</span></span>

<span data-ttu-id="eebe5-126">Trasování vám umožní ladit a řešit potíže s mnoha typy problémů s WIF, včetně tokenů, souborů cookie, deklarací, zpráv protokolu a dalších.</span><span class="sxs-lookup"><span data-stu-id="eebe5-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="eebe5-127">Trasování WIF se podobá trasování WCF; Můžete například vybrat podrobnosti trasování a Zobrazit vše z kritických zpráv ve všech zprávách.</span><span class="sxs-lookup"><span data-stu-id="eebe5-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="eebe5-128">Trasování WIF je možné vygenerovat v souborech **. XML** nebo v souborech **. svclog** , které lze zobrazit pomocí nástroje pro prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="eebe5-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="eebe5-129">Tento nástroj se nachází v adresáři **bin** instalační cesty Windows SDK na počítači, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="eebe5-130">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="eebe5-130">Summary of Steps</span></span>

- <span data-ttu-id="eebe5-131">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="eebe5-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="eebe5-132">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="eebe5-132">Step 2 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="eebe5-133">Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování</span><span class="sxs-lookup"><span data-stu-id="eebe5-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

<span data-ttu-id="eebe5-134">V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravíte soubor *Web. config* , aby bylo možné trasování povolit.</span><span class="sxs-lookup"><span data-stu-id="eebe5-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="eebe5-135">Vytvoření jednoduché aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eebe5-135">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="eebe5-136">Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="eebe5-137">V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="eebe5-138">Do **název**zadejte `TestApp` a stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-138">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="eebe5-139">V části **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TestApp** a pak vyberte **Identita a přístup**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

5. <span data-ttu-id="eebe5-140">Zobrazí se okno **Identita a přístup** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="eebe5-141">Včásti poskytovatelé vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

6. <span data-ttu-id="eebe5-142">V kořenovém adresáři jednotky **C:** vytvořte novou složku s názvem **logs** : **C:\Logs.**</span><span class="sxs-lookup"><span data-stu-id="eebe5-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>

7. <span data-ttu-id="eebe5-143">Přidejte následující  **\<> element System. Diagnostics** do konfiguračního souboru *Web. config* hned za element > ukončení  **\</configSections** , jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="eebe5-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>

    ```xml
    <configuration>
        <configSections>
            ...
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
    > <span data-ttu-id="eebe5-144">Předtím, než může protokolování začít, musí existovat umístění adresáře zadané v atributu **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="eebe5-145">Pokud umístění neexistuje, nebudou vytvořeny žádné protokoly.</span><span class="sxs-lookup"><span data-stu-id="eebe5-145">If the location does not exist, no logs will be created.</span></span>

     <span data-ttu-id="eebe5-146">Výše uvedené nastavení konfigurace umožní **podrobné** trasování pro WIF a uložení výsledného protokolu do souboru **C:logsWIF.XML** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>

## <a name="step-2--test-your-solution"></a><span data-ttu-id="eebe5-147">Krok 2 – testování řešení</span><span class="sxs-lookup"><span data-stu-id="eebe5-147">Step 2 – Test Your Solution</span></span>

<span data-ttu-id="eebe5-148">V tomto kroku otestujete svou ASP.NET aplikaci s podporou WIF, abyste ověřili, že jsou protokoly zaznamenávány.</span><span class="sxs-lookup"><span data-stu-id="eebe5-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="eebe5-149">Testování aplikace ASP.NET s povoleným WIF pro úspěšné trasování</span><span class="sxs-lookup"><span data-stu-id="eebe5-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>

1. <span data-ttu-id="eebe5-150">Spusťte řešení stisknutím klávesy **F5** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="eebe5-151">Měli byste se dodávat s výchozí domovskou stránkou ASP.NET a automaticky se ověřit s uživatelským jménem *Terry*, což je výchozí uživatel, který je vrácený službou Development STS.</span><span class="sxs-lookup"><span data-stu-id="eebe5-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>

2. <span data-ttu-id="eebe5-152">Zavřete okno prohlížeče a potom přejděte do složky **c:\Logs.** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="eebe5-153">Otevřete soubor **C:\logs\WIF.XML** pomocí textového editoru.</span><span class="sxs-lookup"><span data-stu-id="eebe5-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>

3. <span data-ttu-id="eebe5-154">Zkontrolujte soubor **WIF. XML** a ověřte, zda obsahuje položky začínající  **\<na E2ETraceEvent >** .</span><span class="sxs-lookup"><span data-stu-id="eebe5-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="eebe5-155">Tato trasování budou obsahovat  **\<prvky TraceRecord >** s popisy pro sledovanou aktivitu, jako je například **ověření tokenu SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="eebe5-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
