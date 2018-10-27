---
title: 'Postupy: Získání procesu z instalačního programu .NET Framework 4.5'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bec27165d1bfd6a501ba8b96a1eb133276fe7269
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50043332"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="09d3a-102">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="09d3a-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="09d3a-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je distribuovatelné součásti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="09d3a-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="09d3a-104">Pokud vyvíjíte aplikace pro tuto verzi rozhraní .NET Framework, můžete zahrnout (řetězec) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalace požadovaných součástí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="09d3a-105">Účelem představení prostředí přizpůsobené nebo jednotný instalační program, můžete chtít spustit bezobslužně [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nastavení a sledovat její průběh při zobrazování průběh instalačního programu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="09d3a-106">Umožňuje bezobslužné sledování [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalačního programu (což lze sledovat) definuje protokol pomocí segment mapované paměti / v (MMIO) ke komunikaci s instalačním programem (sledovacích procesů nebo chainer).</span><span class="sxs-lookup"><span data-stu-id="09d3a-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="09d3a-107">Definuje způsob, jakým chainer získat informace o průběhu, získat podrobné výsledky, reagovat na zprávy a zrušit tento protokol [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalační program.</span><span class="sxs-lookup"><span data-stu-id="09d3a-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="09d3a-108">**Vyvolání** .</span><span class="sxs-lookup"><span data-stu-id="09d3a-108">**Invocation** .</span></span>  <span data-ttu-id="09d3a-109">Chcete-li volat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nastavení a přijímat informace o průběhu z část MMIO, instalační program musíte provést následující:</span><span class="sxs-lookup"><span data-stu-id="09d3a-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="09d3a-110">Volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]distribuovatelné součásti programu:</span><span class="sxs-lookup"><span data-stu-id="09d3a-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="09d3a-111">kde *název oddílu* je libovolný název, kterou chcete použít k identifikaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="09d3a-112">Instalační program rozhraní .NET framework čte a zapisuje do MMIO část asynchronně, takže je může být výhodné používat události a zprávy během této doby.</span><span class="sxs-lookup"><span data-stu-id="09d3a-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="09d3a-113">V tomto příkladu se vytvoří proces instalace rozhraní .NET Framework pomocí konstruktoru, že oba přiděluje MMIO část (`TheSectionName`) a definuje události (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="09d3a-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="09d3a-114">Nahraďte názvy, které jsou jedinečné pro instalační program tyto názvy.</span><span class="sxs-lookup"><span data-stu-id="09d3a-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="09d3a-115">Čtení z oddílu MMIO.</span><span class="sxs-lookup"><span data-stu-id="09d3a-115">Read from the MMIO section.</span></span> <span data-ttu-id="09d3a-116">V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], operace stažení a instalaci jsou souběžných: jednu část rozhraní .NET Framework může instalace, zatímco jiné části stahuje.</span><span class="sxs-lookup"><span data-stu-id="09d3a-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="09d3a-117">V důsledku toho se průběh odešle zpět (který je napsán) do části MMIO jako dvou čísel (`m_downloadSoFar` a `m_installSoFar`) zvýšit počet od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="09d3a-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="09d3a-118">Při zápisu 255 a ukončí rozhraní .NET Framework, je instalace dokončena.</span><span class="sxs-lookup"><span data-stu-id="09d3a-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="09d3a-119">**Kódy ukončení příkazu**.</span><span class="sxs-lookup"><span data-stu-id="09d3a-119">**Exit codes**.</span></span> <span data-ttu-id="09d3a-120">Následující kódy ukončení příkazu k volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] distribuovatelné součásti programu označuje, zda má instalační program úspěšné nebo neúspěšné:</span><span class="sxs-lookup"><span data-stu-id="09d3a-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="09d3a-121">0 – instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="09d3a-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="09d3a-122">3010 – instalace byla dokončena úspěšně; je třeba restartovat systém.</span><span class="sxs-lookup"><span data-stu-id="09d3a-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="09d3a-123">1602 – instalace byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="09d3a-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="09d3a-124">Všechny ostatní kódy – instalační program zjistil chyby; Zkontrolujte soubory protokolů vytvořené ve složce % temp % podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="09d3a-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="09d3a-125">**Ruší se instalace**.</span><span class="sxs-lookup"><span data-stu-id="09d3a-125">**Canceling setup**.</span></span> <span data-ttu-id="09d3a-126">Instalační program můžete kdykoli zrušit pomocí `Abort` metody nastavte `m_downloadAbort` a `m_ installAbort` příznaky v části MMIO.</span><span class="sxs-lookup"><span data-stu-id="09d3a-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="09d3a-127">Ukázka chainer</span><span class="sxs-lookup"><span data-stu-id="09d3a-127">Chainer Sample</span></span>  
 <span data-ttu-id="09d3a-128">Ukázka Chainer tiše spustí a sleduje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] při zobrazování průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="09d3a-129">Tento příklad je podobný vzorku Chainer k dispozici pro rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="09d3a-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="09d3a-130">Ale navíc ji můžete zabránit restartování systému zpracováním okně se zprávou pro uzavření aplikace rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="09d3a-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="09d3a-131">Informace o toto okno se zprávou, naleznete v tématu [snížení systému restartování během 4.5 instalaci rozhraní .NET Framework](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="09d3a-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="09d3a-132">Můžete tuto ukázku použít s instalačním programem rozhraní .NET Framework 4; v tomto scénáři není zprávu jednoduše odeslat.</span><span class="sxs-lookup"><span data-stu-id="09d3a-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="09d3a-133">V příkladu musíte spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="09d3a-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="09d3a-134">Můžete si stáhnout kompletní řešení sady Visual Studio pro [ukázku .NET Framework 4.5 Chainer](https://go.microsoft.com/fwlink/?LinkId=231345) z Galerie ukázek na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="09d3a-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="09d3a-135">Následující části popisují důležité soubory v této ukázce: MMIOChainer.h ChainingdotNet4.cpp a IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="09d3a-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="09d3a-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="09d3a-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="09d3a-137">Soubor MMIOChainer.h (viz [dokončení kódu](https://go.microsoft.com/fwlink/?LinkId=231369)) obsahuje definice struktury dat a základní třídu, ze kterého by měla být odvozena třída zřetězovatele.</span><span class="sxs-lookup"><span data-stu-id="09d3a-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="09d3a-138">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozšiřuje datová struktura MMIO zpracování dat, která [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] musí instalační program.</span><span class="sxs-lookup"><span data-stu-id="09d3a-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="09d3a-139">Změny struktury MMIO jsou zpětně kompatibilní, umožní práci s instalačním programem rozhraní .NET Framework 4.5 chainer rozhraní .NET Framework 4 bez nové kompilace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="09d3a-140">Tento scénář ale nepodporuje funkci pro snížení restartování systému.</span><span class="sxs-lookup"><span data-stu-id="09d3a-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="09d3a-141">Pole verze poskytuje způsob identifikace revize pro strukturu a zprávu formátu.</span><span class="sxs-lookup"><span data-stu-id="09d3a-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="09d3a-142">Instalační program rozhraní .NET Framework Určuje verzi rozhraní chainer voláním `VirtualQuery` funkce určit velikost mapování souborů.</span><span class="sxs-lookup"><span data-stu-id="09d3a-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="09d3a-143">Pokud je velikost dostatečně velký, aby pole verze, instalační program rozhraní .NET Framework používá zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09d3a-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="09d3a-144">Pokud mapování souboru je příliš malá tak, aby obsahovala pole verze, která je tomu u rozhraní .NET Framework 4, předpokládá se v procesu instalace verze 0 (4).</span><span class="sxs-lookup"><span data-stu-id="09d3a-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="09d3a-145">Pokud chainer nepodporuje verzi, která požaduje instalaci rozhraní .NET Framework k odeslání zprávy, instalační program rozhraní .NET Framework předpokládá odpověď ignorovat.</span><span class="sxs-lookup"><span data-stu-id="09d3a-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="09d3a-146">Datová struktura MMIO je definovaná následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="09d3a-146">The MMIO data structure is defined as follows:</span></span>  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
    ```  
  
-   <span data-ttu-id="09d3a-147">`MmioDataStructure` Datová struktura, neměl by se používat přímo; použijte `MmioChainer` třídy místo toho implementovat vaše chainer.</span><span class="sxs-lookup"><span data-stu-id="09d3a-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="09d3a-148">Odvozovat `MmioChainer` třídy do řetězce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span><span class="sxs-lookup"><span data-stu-id="09d3a-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="09d3a-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="09d3a-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="09d3a-150">Soubor IProgressObserver.h implementuje pozorovatele průběhu ([zobrazit kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="09d3a-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="09d3a-151">Tato pozorovatel získá oznámení o průběhu stahování a instalace (stanoveno, bez znaménka `char`, 0 – 255, která 1 – 100 % dokončeno).</span><span class="sxs-lookup"><span data-stu-id="09d3a-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="09d3a-152">Pozorovatel také zasláno oznámení, když chainee odešle zprávu a pozorovatel by měl odeslat odpověď.</span><span class="sxs-lookup"><span data-stu-id="09d3a-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="09d3a-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="09d3a-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="09d3a-154">[ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) implementuje `Server` třída, která je odvozena z `MmioChainer` třídy a přepisuje patřičné metody k zobrazení informací o průběhu.</span><span class="sxs-lookup"><span data-stu-id="09d3a-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="09d3a-155">MmioChainer vytvoří oddíl s názvem zadaný oddíl a inicializuje chainer pomocí zadaného názvu události.</span><span class="sxs-lookup"><span data-stu-id="09d3a-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="09d3a-156">Název události je uložen ve struktuře mapovaná data.</span><span class="sxs-lookup"><span data-stu-id="09d3a-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="09d3a-157">Název oddílu a události pro byste měli vytvořit jedinečný.</span><span class="sxs-lookup"><span data-stu-id="09d3a-157">You should make the section and event names unique.</span></span> <span data-ttu-id="09d3a-158">`Server` Třídy v následujícím kódu spustí zadaný instalační program, monitoruje průběh a vrátí ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="09d3a-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="09d3a-159">Instalace je spuštěn v hlavní metodě.</span><span class="sxs-lookup"><span data-stu-id="09d3a-159">The installation is started in the Main method.</span></span>  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
    ```  
  
-   <span data-ttu-id="09d3a-160">Před spuštěním instalace chainer kontroluje, jestli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je již nainstalována voláním `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="09d3a-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
    ```  
  
-   <span data-ttu-id="09d3a-161">Cesta ke spustitelnému souboru (Setup.exe v příkladu) můžete změnit v `Launch` metoda odkazovat na správné umístění nebo přizpůsobení kódu k určení umístění.</span><span class="sxs-lookup"><span data-stu-id="09d3a-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="09d3a-162">`MmioChainer` Poskytuje základní třídu blokování `Run()` metodu, která volá odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="09d3a-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
    ```cpp  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
    ```  
  
-   <span data-ttu-id="09d3a-163">`Send` Metoda zachycuje a zpracovávat zprávy.</span><span class="sxs-lookup"><span data-stu-id="09d3a-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="09d3a-164">V této verzi rozhraní .NET Framework pouze podporované zpráva je zprávou zavřít aplikaci.</span><span class="sxs-lookup"><span data-stu-id="09d3a-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
    ```  
  
-   <span data-ttu-id="09d3a-165">Průběh dat je bez znaménka `char` od 0 (0 %) do 255 (100 %).</span><span class="sxs-lookup"><span data-stu-id="09d3a-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="09d3a-166">Hodnota HRESULT je předán `Finished` metody.</span><span class="sxs-lookup"><span data-stu-id="09d3a-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="09d3a-167">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Redistributable obvykle zapisuje mnoho zprávy o průběhu a jedna zpráva, která označuje dokončení (na straně chainer).</span><span class="sxs-lookup"><span data-stu-id="09d3a-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="09d3a-168">Přečte také asynchronně, hledá `Abort` záznamy.</span><span class="sxs-lookup"><span data-stu-id="09d3a-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="09d3a-169">Pokud obdrží `Abort` záznam, zruší instalace a zapíše dokončení záznam s E_ABORT jako svá data po instalaci se zrušilo a operace instalace byly vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="09d3a-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="09d3a-170">Typický server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak je znázorněno v předchozím příkladu kódu `Server::CreateSection`) a spustí Distribuovatelný pomocí `CreateProcess` metoda a předá kanálu název s `-pipe someFileSectionName` možnost.</span><span class="sxs-lookup"><span data-stu-id="09d3a-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="09d3a-171">Server by měly implementovat `OnProgress`, `Send`, a `Finished` metody s kód specifický pro uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="09d3a-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d3a-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="09d3a-172">See Also</span></span>  
- [<span data-ttu-id="09d3a-173">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="09d3a-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
- [<span data-ttu-id="09d3a-174">Nasazení</span><span class="sxs-lookup"><span data-stu-id="09d3a-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
