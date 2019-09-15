---
title: 'Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990484"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="06a79-102">Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="06a79-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="06a79-103">Applies To</span></span>  
  
- <span data-ttu-id="06a79-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="06a79-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="06a79-105">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="06a79-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
- <span data-ttu-id="06a79-106">Řešení potíží a ladění aplikací WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="06a79-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="06a79-107">Summary</span></span>  
 <span data-ttu-id="06a79-108">Tento postup popisuje nezbytné kroky, jak nakonfigurovat trasování WIF, shromažďovat protokoly trasování a analyzovat protokoly trasování pomocí nástroje Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="06a79-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="06a79-109">Poskytuje obecné mapování pro položky trasování k akcím, které jsou potřeba k řešení problémů souvisejících s WIF.</span><span class="sxs-lookup"><span data-stu-id="06a79-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="06a79-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="06a79-110">Contents</span></span>  
  
- <span data-ttu-id="06a79-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="06a79-111">Objectives</span></span>  
  
- <span data-ttu-id="06a79-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="06a79-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="06a79-113">Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config</span><span class="sxs-lookup"><span data-stu-id="06a79-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="06a79-114">Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="06a79-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="06a79-115">Krok 3 – určení řešení pro opravu problémů spojených s WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
- <span data-ttu-id="06a79-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="06a79-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="06a79-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="06a79-117">Objectives</span></span>  
  
- <span data-ttu-id="06a79-118">Nakonfigurujte trasování WIF.</span><span class="sxs-lookup"><span data-stu-id="06a79-118">Configure WIF tracing.</span></span>  
  
- <span data-ttu-id="06a79-119">Zobrazit protokoly trasování v nástroji Prohlížeč trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-119">View trace logs in the Trace Viewer tool.</span></span>  
  
- <span data-ttu-id="06a79-120">Identifikujte problémy související s WIF v protokolech trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-120">Identify WIF related issues in the trace logs.</span></span>  
  
- <span data-ttu-id="06a79-121">Použijte opravné akce, které WIF související problémy nalezené v protokolech trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="06a79-122">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="06a79-122">Summary of Steps</span></span>  
  
- <span data-ttu-id="06a79-123">Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config</span><span class="sxs-lookup"><span data-stu-id="06a79-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="06a79-124">Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="06a79-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="06a79-125">Krok 3 – určení řešení pro opravu problémů spojených s WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="06a79-126">Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config</span><span class="sxs-lookup"><span data-stu-id="06a79-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="06a79-127">V tomto kroku přidáte změny do konfiguračních oddílů v souboru *Web. config* , které umožní WIF trasování událostí a jejich uložení do protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="06a79-128">Konfigurace trasování WIF pomocí konfiguračního souboru Web. config</span><span class="sxs-lookup"><span data-stu-id="06a79-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="06a79-129">Otevřete kořenový konfigurační soubor **Web. config** nebo **App. config** v editoru sady Visual Studio tak, že na něj dvakrát kliknete v **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="06a79-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="06a79-130">Pokud vaše řešení neobsahuje konfigurační soubor **Web. config** nebo **App. config** , přidejte jej kliknutím pravým tlačítkem na řešení v **Průzkumník řešení** a kliknutím na tlačítko **Přidat**a kliknutím na položku **Nová položka...** .</span><span class="sxs-lookup"><span data-stu-id="06a79-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="06a79-131">V dialogovém okně **Nová položka** vyberte v **seznamu konfigurační soubor aplikace** pro soubor **App. config** nebo **webový konfigurační soubor** pro **Web. config** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="06a79-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="06a79-132">Do konfiguračního souboru  **\<v uzlu Konfigurace >** na konci konfiguračního souboru přidejte položky konfigurace podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="06a79-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
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
  
3. <span data-ttu-id="06a79-133">Výše uvedená konfigurace instruuje WIF k vygenerování podrobných událostí trasování a jejich protokolování do souboru *WIFTrace. e2e* .</span><span class="sxs-lookup"><span data-stu-id="06a79-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="06a79-134">Úplný seznam hodnot pro přepínač **určit atributy switchValue** najdete v tabulce úrovně trasování, kterou najdete v následujícím tématu: [Konfigurace trasování](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="06a79-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="06a79-135">Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="06a79-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="06a79-136">V tomto kroku použijete nástroj Prohlížeč trasování (SvcTraceViewer. exe) k analýze protokolů trasování WIF.</span><span class="sxs-lookup"><span data-stu-id="06a79-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="06a79-137">Analýza protokolů trasování WIF pomocí nástroje Trace Viewer (SvcTraceViewer. exe)</span><span class="sxs-lookup"><span data-stu-id="06a79-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="06a79-138">Nástroj Prohlížeč trasování (SvcTraceViewer. exe) se dodává jako součást Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="06a79-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="06a79-139">Pokud jste ještě Windows SDK nenainstalovali, můžete si ho stáhnout tady: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="06a79-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="06a79-140">Spusťte nástroj Prohlížeč trasování (SvcTraceViewer. exe).</span><span class="sxs-lookup"><span data-stu-id="06a79-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="06a79-141">Obvykle je k dispozici ve složce **bin** instalační cesty.</span><span class="sxs-lookup"><span data-stu-id="06a79-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="06a79-142">Otevřete soubor protokolu trasování WIF, například WIFTrace. e2e tak, že vyberete **soubor**, **otevřete...**</span><span class="sxs-lookup"><span data-stu-id="06a79-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="06a79-143">v nabídce nebo pomocí klávesové zkratky **CTRL + O** .</span><span class="sxs-lookup"><span data-stu-id="06a79-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="06a79-144">Soubor protokolu trasování se otevře v nástroji Prohlížeč trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="06a79-145">Zkontrolujte položky na kartě **aktivita** . Každá položka by měla obsahovat číslo aktivity, počet zaznamenaných trasování, dobu trvání aktivity a její počáteční a koncové časové razítko.</span><span class="sxs-lookup"><span data-stu-id="06a79-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="06a79-146">Klikněte na kartu **aktivita** . V hlavní oblasti nástroje by se měly zobrazit podrobné položky trasování.</span><span class="sxs-lookup"><span data-stu-id="06a79-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="06a79-147">Pomocí rozevíracího seznamu **úrovně** v nabídce můžete filtrovat konkrétní úroveň trasování, například: **Vše**, **Upozornění**, **chyby**, **informace**atd.</span><span class="sxs-lookup"><span data-stu-id="06a79-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="06a79-148">Klikněte na konkrétní položky trasování a zkontrolujte podrobnosti v dolní oblasti nástroje.</span><span class="sxs-lookup"><span data-stu-id="06a79-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="06a79-149">Podrobnosti lze zobrazit pomocí **formátovaného** a **XML** zobrazení výběrem odpovídajících karet.</span><span class="sxs-lookup"><span data-stu-id="06a79-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="06a79-150">Krok 3 – určení řešení pro opravu problémů spojených s WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="06a79-151">V tomto kroku můžete identifikovat řešení potíží souvisejících s WIF, které jsou identifikované pomocí protokolu trasování WIF a nástroje Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="06a79-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="06a79-152">Popisuje obecné mapování WIF souvisejících s výjimkami na potenciální řešení nebo požadované akce pro řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="06a79-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="06a79-153">Určení řešení pro opravu problémů souvisejících s WIF</span><span class="sxs-lookup"><span data-stu-id="06a79-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="06a79-154">Projděte si následující tabulku výjimek WIF a požadované akce Opravte problémy.</span><span class="sxs-lookup"><span data-stu-id="06a79-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="06a79-155">**ID chyby**</span><span class="sxs-lookup"><span data-stu-id="06a79-155">**Error ID**</span></span>|<span data-ttu-id="06a79-156">**Chybová zpráva**</span><span class="sxs-lookup"><span data-stu-id="06a79-156">**Error Message**</span></span>|<span data-ttu-id="06a79-157">**Akce nutná k opravě chyby**</span><span class="sxs-lookup"><span data-stu-id="06a79-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="06a79-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="06a79-158">ID4175</span></span>|<span data-ttu-id="06a79-159">Vystavitel tokenu zabezpečení nebyl rozpoznán pomocí IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="06a79-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="06a79-160">Pokud chcete z tohoto vystavitele přijímat tokeny zabezpečení, nakonfigurujte IssuerNameRegistry tak, aby vracel platný název tohoto vystavitele.</span><span class="sxs-lookup"><span data-stu-id="06a79-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="06a79-161">Tato chyba může být způsobena zkopírováním kryptografického otisku z modulu snap-in konzoly MMC a vložením do souboru *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="06a79-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="06a79-162">Konkrétně můžete v textovém řetězci při kopírování z okna vlastností certifikátu získat další netisknutelný znak.</span><span class="sxs-lookup"><span data-stu-id="06a79-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="06a79-163">Tento znak navíc způsobí selhání porovnávání kryptografických otisků.</span><span class="sxs-lookup"><span data-stu-id="06a79-163">This extra character causes the thumbprint match to fail.</span></span> <span data-ttu-id="06a79-164">Postup pro správné kopírování kryptografického otisku se dá najít v [jednotném přihlašování založeném na deklaracích webu a Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="06a79-164">The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="06a79-165">Související položky</span><span class="sxs-lookup"><span data-stu-id="06a79-165">Related Items</span></span>  
  
- [<span data-ttu-id="06a79-166">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="06a79-166">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
