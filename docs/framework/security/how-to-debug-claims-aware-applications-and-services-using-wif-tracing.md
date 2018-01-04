---
title: "Postupy: Ladění deklaracemi identity aplikace a služby pomocí WIF trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4243313d88b22aa9f755a3586ea0c5fbe08cd891
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="f2151-102">Postupy: Ladění deklaracemi identity aplikace a služby pomocí WIF trasování</span><span class="sxs-lookup"><span data-stu-id="f2151-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="f2151-103">Platí pro</span><span class="sxs-lookup"><span data-stu-id="f2151-103">Applies To</span></span>  
  
-   <span data-ttu-id="f2151-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="f2151-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="f2151-105">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f2151-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
-   <span data-ttu-id="f2151-106">Řešení potíží a ladění aplikací WIF</span><span class="sxs-lookup"><span data-stu-id="f2151-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f2151-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="f2151-107">Summary</span></span>  
 <span data-ttu-id="f2151-108">Tento postup popisuje požadované kroky, jak nakonfigurovat WIF trasování, shromážděte protokoly trasování a jak analyzovat trasování protokoly, pomocí nástroje prohlížeče trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="f2151-109">Poskytuje obecné mapování pro trasování položky na akce, které jsou potřebné k řešení potíží s WIF.</span><span class="sxs-lookup"><span data-stu-id="f2151-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="f2151-110">Obsah</span><span class="sxs-lookup"><span data-stu-id="f2151-110">Contents</span></span>  
  
-   <span data-ttu-id="f2151-111">Cíle</span><span class="sxs-lookup"><span data-stu-id="f2151-111">Objectives</span></span>  
  
-   <span data-ttu-id="f2151-112">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="f2151-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="f2151-113">Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f2151-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="f2151-114">Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování</span><span class="sxs-lookup"><span data-stu-id="f2151-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="f2151-115">Krok 3 – lze vyřešit WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="f2151-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
-   <span data-ttu-id="f2151-116">Související položky</span><span class="sxs-lookup"><span data-stu-id="f2151-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="f2151-117">Cíle</span><span class="sxs-lookup"><span data-stu-id="f2151-117">Objectives</span></span>  
  
-   <span data-ttu-id="f2151-118">Konfigurovat WIF trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-118">Configure WIF tracing.</span></span>  
  
-   <span data-ttu-id="f2151-119">V nástroji Prohlížeč trasování protokolů trasování zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f2151-119">View trace logs in the Trace Viewer tool.</span></span>  
  
-   <span data-ttu-id="f2151-120">Identifikovat WIF související s problémy v protokolech trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-120">Identify WIF related issues in the trace logs.</span></span>  
  
-   <span data-ttu-id="f2151-121">Použít opravné akce WIF problémům najít v protokolech trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="f2151-122">Přehled kroků</span><span class="sxs-lookup"><span data-stu-id="f2151-122">Summary of Steps</span></span>  
  
-   <span data-ttu-id="f2151-123">Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f2151-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
-   <span data-ttu-id="f2151-124">Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování</span><span class="sxs-lookup"><span data-stu-id="f2151-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
-   <span data-ttu-id="f2151-125">Krok 3 – lze vyřešit WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="f2151-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="f2151-126">Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f2151-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="f2151-127">V tomto kroku přidáte změny konfigurační oddíly funkce v *Web.config* soubor, který povolit WIF sledovat události a uložit je do protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="f2151-128">Konfigurace trasování WIF pomocí konfiguračního souboru Web.config</span><span class="sxs-lookup"><span data-stu-id="f2151-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1.  <span data-ttu-id="f2151-129">Otevřete kořenu **Web.config** nebo **App.config** konfiguračního souboru v editoru Visual Studio poklepáním na na něm v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="f2151-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="f2151-130">Pokud vaše řešení nemá **Web.config** nebo **App.config** konfigurační soubor, přidejte kliknutím pravým tlačítkem na řešení v **Průzkumníku řešení** a kliknutím na  **Přidat**, pak levým na **novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="f2151-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="f2151-131">Na **nová položka** vyberte **konfigurační soubor aplikace** pro **App.config** nebo **soubor webové konfigurace** pro **Web.config** ze seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2151-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2.  <span data-ttu-id="f2151-132">Přidejte konfigurační položky podobné následujícím do konfiguračního souboru uvnitř  **\<konfigurace >** uzlu na konci tohoto konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="f2151-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
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
  
3.  <span data-ttu-id="f2151-133">Výše uvedené konfigurace dá pokyn WIF generovat události podrobného trasování a protokolování do *WIFTrace.e2e* souboru.</span><span class="sxs-lookup"><span data-stu-id="f2151-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="f2151-134">Úplný seznam hodnot pro **switchValue** přepnout, naleznete v tabulce Úroveň trasování najít v následujícím tématu: [Konfigurace trasování](http://msdn.microsoft.com/library/ms733025.aspx).</span><span class="sxs-lookup"><span data-stu-id="f2151-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](http://msdn.microsoft.com/library/ms733025.aspx).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="f2151-135">Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování</span><span class="sxs-lookup"><span data-stu-id="f2151-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="f2151-136">V tomto kroku použijete nástroj Prohlížeč trasování (SvcTraceViewer.exe) k analýze protokolů trasování WIF.</span><span class="sxs-lookup"><span data-stu-id="f2151-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="f2151-137">K analýze protokolů trasování WIF pomocí nástroje prohlížeče trasování (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f2151-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1.  <span data-ttu-id="f2151-138">Nástroj Prohlížeč trasování (SvcTraceViewer.exe) dodává jako součást sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="f2151-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="f2151-139">Pokud jste ještě nenainstalovali Windows SDK, můžete stáhnout tady: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="f2151-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2.  <span data-ttu-id="f2151-140">Spusťte nástroj Prohlížeč trasování (SvcTraceViewer.exe).</span><span class="sxs-lookup"><span data-stu-id="f2151-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="f2151-141">Je obvykle dostupné v **Bin** složky cesty instalace.</span><span class="sxs-lookup"><span data-stu-id="f2151-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3.  <span data-ttu-id="f2151-142">Otevřete soubor protokolu WIF trasování, například WIFTrace.e2e výběrem **soubor**, **otevřete...**</span><span class="sxs-lookup"><span data-stu-id="f2151-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="f2151-143">možnost v nabídce nebo pomocí **Ctrl + O** zástupce.</span><span class="sxs-lookup"><span data-stu-id="f2151-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="f2151-144">Otevře se v nástroji Prohlížeč trasování soubor protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4.  <span data-ttu-id="f2151-145">Zkontrolujte položky v **aktivity** kartě. Každý záznam by měl obsahovat číslo aktivity, počet trasování, které byly zaznamenány do protokolu, doba trvání aktivity a jeho počáteční a koncové časová razítka.</span><span class="sxs-lookup"><span data-stu-id="f2151-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5.  <span data-ttu-id="f2151-146">Klikněte na **aktivity** kartě. Měli byste vidět podrobné trasování položky v oblasti hlavní nástroje.</span><span class="sxs-lookup"><span data-stu-id="f2151-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="f2151-147">Použití **úroveň** rozevíracího seznamu v nabídce filtrovat konkrétní úroveň trasování, například: **všechny**, **upozornění**, **chyby**, **Informace**atd.</span><span class="sxs-lookup"><span data-stu-id="f2151-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6.  <span data-ttu-id="f2151-148">Kliknutím na konkrétní trasování záznamy pro podrobné informace v oblasti nižší nástroje.</span><span class="sxs-lookup"><span data-stu-id="f2151-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="f2151-149">Podrobnosti lze zobrazit pomocí **formátu** a **XML** zobrazení tak, že zvolíte odpovídající karty.</span><span class="sxs-lookup"><span data-stu-id="f2151-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="f2151-150">Krok 3 – lze vyřešit WIF identifikovat problémy související s</span><span class="sxs-lookup"><span data-stu-id="f2151-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="f2151-151">V tomto kroku můžete identifikovat řešení s WIF problémy identifikovat pomocí protokolu trasování WIF a nástroj prohlížeče trasování.</span><span class="sxs-lookup"><span data-stu-id="f2151-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="f2151-152">Popisuje obecné mapování WIF související výjimky možná řešení nebo požadované akce k odstranění problému.</span><span class="sxs-lookup"><span data-stu-id="f2151-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="f2151-153">K identifikaci lze vyřešit WIF problémy související s</span><span class="sxs-lookup"><span data-stu-id="f2151-153">To identify solutions to fix WIF related issues</span></span>  
  
1.  <span data-ttu-id="f2151-154">Přečtěte si následující tabulku WIF výjimky a požadované akce k opravě problémů.</span><span class="sxs-lookup"><span data-stu-id="f2151-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="f2151-155">**ID chyby**</span><span class="sxs-lookup"><span data-stu-id="f2151-155">**Error ID**</span></span>|<span data-ttu-id="f2151-156">**Chybová zpráva**</span><span class="sxs-lookup"><span data-stu-id="f2151-156">**Error Message**</span></span>|<span data-ttu-id="f2151-157">**Akce potřebné opravy chyby**</span><span class="sxs-lookup"><span data-stu-id="f2151-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="f2151-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="f2151-158">ID4175</span></span>|<span data-ttu-id="f2151-159">Vystavitel tokenu zabezpečení nebyl rozpoznán IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="f2151-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="f2151-160">Pokud chcete přijímat tokeny zabezpečení z vystaviteli, nakonfigurujte IssuerNameRegistry vrátit platný název pro tento vystavitele.</span><span class="sxs-lookup"><span data-stu-id="f2151-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="f2151-161">Tato chyba může být způsobeno kopírování kryptografický otisk z modulu snap-in konzoly MMC a vložíte ji do *Web.config* souboru.</span><span class="sxs-lookup"><span data-stu-id="f2151-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="f2151-162">Konkrétně můžete získat velmi netisknutelný znak v textovém řetězci při kopírování v okně Vlastnosti certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f2151-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="f2151-163">Tento další znak způsobí selhání porovnávání kryptografický otisk. Postup pro správně kopírování kryptografický otisk naleznete zde: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span><span class="sxs-lookup"><span data-stu-id="f2151-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found here: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="f2151-164">Související položky</span><span class="sxs-lookup"><span data-stu-id="f2151-164">Related Items</span></span>  
  
-   [<span data-ttu-id="f2151-165">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="f2151-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](http://msdn.microsoft.com/library/aa751795.aspx)
