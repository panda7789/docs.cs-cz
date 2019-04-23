---
title: 'Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 43fa859aa84189817dffe74ecd72253ab9b82585
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321546"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="90b24-102">Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF</span><span class="sxs-lookup"><span data-stu-id="90b24-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="90b24-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="90b24-103">Applies To</span></span>  
  
-   <span data-ttu-id="90b24-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="90b24-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="90b24-105">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="90b24-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="90b24-106">Řešení potíží a ladění aplikací technologie WIF</span><span class="sxs-lookup"><span data-stu-id="90b24-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="90b24-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="90b24-107">Summary</span></span>  
 <span data-ttu-id="90b24-108">Tento postup popisuje kroky pro postup konfigurace trasování WIF, shromažďovat protokoly trasování a protokoly jak analyzovat trasování pomocí nástroje prohlížeče trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="90b24-109">Poskytuje obecné mapování trasování položky pro akce potřebné k řešení problémů souvisejících s technologie WIF.</span><span class="sxs-lookup"><span data-stu-id="90b24-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="90b24-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="90b24-110">Contents</span></span>  
  
-   <span data-ttu-id="90b24-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="90b24-111">Objectives</span></span>  
  
-   <span data-ttu-id="90b24-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="90b24-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="90b24-113">Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config</span><span class="sxs-lookup"><span data-stu-id="90b24-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="90b24-114">Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="90b24-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="90b24-115">Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="90b24-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="90b24-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="90b24-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="90b24-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="90b24-117">Objectives</span></span>  
  
-   <span data-ttu-id="90b24-118">Konfigurace trasování WIF.</span><span class="sxs-lookup"><span data-stu-id="90b24-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="90b24-119">Protokoly trasování zobrazení v nástroji prohlížeče trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="90b24-120">Identifikujte technologie WIF související s problémy v protokolech trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="90b24-121">Použít opravné akce, které technologie WIF a související s problémy zjištěné v protokoly trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="90b24-122">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="90b24-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="90b24-123">Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config</span><span class="sxs-lookup"><span data-stu-id="90b24-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="90b24-124">Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="90b24-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="90b24-125">Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="90b24-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="90b24-126">Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config</span><span class="sxs-lookup"><span data-stu-id="90b24-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="90b24-127">V tomto kroku přidáte změny do konfigurační oddíly funkce v *Web.config* soubor, který se povolit technologie WIF sledovat jeho události a uložit je do protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="90b24-128">Konfigurace trasování WIF je používán konfigurační soubor Web.config</span><span class="sxs-lookup"><span data-stu-id="90b24-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="90b24-129">Otevřít kořenové **Web.config** nebo **App.config** konfiguračním souboru v editoru sady Visual Studio, dvakrát klikněte na něj v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="90b24-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="90b24-130">Pokud vaše řešení nemá **Web.config** nebo **App.config** konfigurace přidejte kliknutím pravým tlačítkem na řešení v **Průzkumníka řešení** a kliknete na  **Přidat**, pak levým na **novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="90b24-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="90b24-131">Na **nová položka** dialogového okna, vyberte **konfiguračního souboru aplikace** pro **App.config** nebo **souboru konfigurace webu** pro **Web.config** ze seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="90b24-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="90b24-132">Přidat položky konfigurace, který je podobný následujícímu do konfiguračního souboru uvnitř  **\<konfigurace >** uzlu na konci konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="90b24-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3. <span data-ttu-id="90b24-133">V konfiguraci uvedené výš dává pokyn technologie WIF generování událostí na podrobné trasování a protokolování do *WIFTrace.e2e* souboru.</span><span class="sxs-lookup"><span data-stu-id="90b24-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="90b24-134">Úplný seznam hodnot **switchValue** přepnout, naleznete v tabulce Úroveň trasování v následujícím tématu: [Konfigurace trasování](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="90b24-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="90b24-135">Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování</span><span class="sxs-lookup"><span data-stu-id="90b24-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="90b24-136">V tomto kroku použijete nástroj prohlížeče trasování (SvcTraceViewer.exe) k analýze protokolů trasování WIF.</span><span class="sxs-lookup"><span data-stu-id="90b24-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="90b24-137">K analýze protokolů trasování WIF pomocí nástroje prohlížeče trasování (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="90b24-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="90b24-138">Prohlížečem trasování (SvcTraceViewer.exe) dodávána jako součást sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="90b24-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="90b24-139">Pokud jste ještě nenainstalovali sady Windows SDK, můžete ji stáhnout zde: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="90b24-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="90b24-140">Spusťte nástroj prohlížeče trasování (SvcTraceViewer.exe).</span><span class="sxs-lookup"><span data-stu-id="90b24-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="90b24-141">Je obvykle dostupná **Bin** složce instalační cesta.</span><span class="sxs-lookup"><span data-stu-id="90b24-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="90b24-142">Otevřít soubor protokolu technologie WIF trasování, například WIFTrace.e2e tak, že vyberete **souboru**, **otevřít...**</span><span class="sxs-lookup"><span data-stu-id="90b24-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="90b24-143">Možnosti v nabídce nebo pomocí **Ctrl + O** zástupce.</span><span class="sxs-lookup"><span data-stu-id="90b24-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="90b24-144">Soubor protokolu trasování se otevře v prohlížeči trasování nástroje.</span><span class="sxs-lookup"><span data-stu-id="90b24-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="90b24-145">Zkontrolujte záznamy v **aktivity** kartu. Každý záznam může obsahovat číslo aktivity, počet trasování, které byly zaznamenány, doba trvání aktivity a její spuštění a ukončení časová razítka.</span><span class="sxs-lookup"><span data-stu-id="90b24-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="90b24-146">Klikněte na **aktivity** kartu. Měli byste vidět položky podrobné trasování v hlavní oblasti nástroje.</span><span class="sxs-lookup"><span data-stu-id="90b24-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="90b24-147">Použití **úroveň** rozevíracího seznamu v nabídce filtrovat konkrétní úroveň trasování, například: **Všechny**, **upozornění**, **chyby**, **informace**atd.</span><span class="sxs-lookup"><span data-stu-id="90b24-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="90b24-148">Klikněte na položky konkrétní trasování chcete podívat na podrobnosti ve spodní části nástroje.</span><span class="sxs-lookup"><span data-stu-id="90b24-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="90b24-149">Podrobnosti lze zobrazit pomocí **formátu** a **XML** zobrazení výběrem příslušné karty.</span><span class="sxs-lookup"><span data-stu-id="90b24-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="90b24-150">Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="90b24-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="90b24-151">V tomto kroku můžete identifikovat řešení pro související technologie WIF problémů zjištěných pomocí prohlížeče trasování nástroje a technologie WIF protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="90b24-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="90b24-152">Popisuje obecné mapování technologie WIF související výjimky z možných řešení nebo požadované akce k odstranění tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="90b24-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="90b24-153">K identifikaci řešení Chcete-li vyřešit technologie WIF problémy související s</span><span class="sxs-lookup"><span data-stu-id="90b24-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="90b24-154">Projděte si následující tabulku výjimek technologie WIF a požadovaných akcí, chcete-li opravit problémy.</span><span class="sxs-lookup"><span data-stu-id="90b24-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="90b24-155">**ID chyby**</span><span class="sxs-lookup"><span data-stu-id="90b24-155">**Error ID**</span></span>|<span data-ttu-id="90b24-156">**Chybová zpráva**</span><span class="sxs-lookup"><span data-stu-id="90b24-156">**Error Message**</span></span>|<span data-ttu-id="90b24-157">**Akce potřebný k opravě chyby**</span><span class="sxs-lookup"><span data-stu-id="90b24-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="90b24-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="90b24-158">ID4175</span></span>|<span data-ttu-id="90b24-159">IssuerNameRegistry nebyl rozpoznán vystavitele tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="90b24-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="90b24-160">Přijímat tokeny zabezpečení od tohoto vydavatele, nakonfigurujte IssuerNameRegistry vrátit platný název pro tento vystavitele.</span><span class="sxs-lookup"><span data-stu-id="90b24-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="90b24-161">Tato chyba může být způsobena zkopírováním kryptografický otisk z modulu snap-in konzoly MMC a jeho vložením do *Web.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="90b24-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="90b24-162">Konkrétně můžete získat další netisknutelné znaky v textovém řetězci při kopírování z okna Vlastnosti certifikátu.</span><span class="sxs-lookup"><span data-stu-id="90b24-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="90b24-163">Tento znak navíc způsobí, že shoda kryptografický otisk selhání. Postup pro správně kopírování kryptografický otisk lze nalézt v [jednotné přihlašování založené na deklaracích-v pro Web a Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="90b24-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="90b24-164">Související položky</span><span class="sxs-lookup"><span data-stu-id="90b24-164">Related Items</span></span>  
  
-   [<span data-ttu-id="90b24-165">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="90b24-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
