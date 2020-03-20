---
title: 'Postupy: Získání procesu z instalačního programu .NET Framework 4.5'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: cd81ad83aee80341d0334cfa8caa165b25ee0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716486"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="ec4db-102">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ec4db-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="ec4db-103">Rozhraní .NET Framework 4.5 je redistribuovatelný runtime.</span><span class="sxs-lookup"><span data-stu-id="ec4db-103">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="ec4db-104">Pokud vyvíjíte aplikace pro tuto verzi rozhraní .NET Framework, můžete zahrnout (řetězové) nastavení rozhraní .NET Framework 4.5 jako předpoklad součást nastavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-104">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="ec4db-105">Chcete-li prezentovat přizpůsobené nebo jednotné nastavení, můžete bezobslužně spustit nastavení rozhraní .NET Framework 4.5 a sledovat jeho průběh a zároveň zobrazit průběh nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-105">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="ec4db-106">Chcete-li povolit tiché sledování, nastavení rozhraní .NET Framework 4.5 (které lze sledovat) definuje protokol pomocí segmentu MMIO mapované ho paměti pro komunikaci s nastavením (sledovací proces nebo chainer).</span><span class="sxs-lookup"><span data-stu-id="ec4db-106">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="ec4db-107">Tento protokol definuje způsob, jakým chainer získává informace o průběhu, získává podrobné výsledky, odpovídá na zprávy a ruší nastavení rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="ec4db-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="ec4db-108">**Vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="ec4db-108">**Invocation**.</span></span> <span data-ttu-id="ec4db-109">Chcete-li volat instalační program rozhraní .NET Framework 4.5 a přijímat informace o průběhu z části MMIO, musí instalační program provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="ec4db-109">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="ec4db-110">Zavolejte redistribuovatelný program rozhraní .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="ec4db-110">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="ec4db-111">Kde *název oddílu* je libovolný název, který chcete použít k identifikaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-111">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="ec4db-112">Instalační program rozhraní .NET Framework čte a zapisuje do sekce MMIO asynchronně, takže může být vhodné používat události a zprávy během této doby.</span><span class="sxs-lookup"><span data-stu-id="ec4db-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="ec4db-113">V příkladu je proces nastavení rozhraní .NET Framework vytvořen konstruktorem, který`TheSectionName`přiděluje oddíl`TheEventName`MMIO ( ) a definuje událost ( ):</span><span class="sxs-lookup"><span data-stu-id="ec4db-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="ec4db-114">Nahraďte tyto názvy názvy, které jsou jedinečné pro instalační program.</span><span class="sxs-lookup"><span data-stu-id="ec4db-114">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="ec4db-115">Přečtěte si z oddílu MMIO.</span><span class="sxs-lookup"><span data-stu-id="ec4db-115">Read from the MMIO section.</span></span> <span data-ttu-id="ec4db-116">V rozhraní .NET Framework 4.5 jsou operace stahování a instalace simultánní: Jedna část rozhraní .NET Framework může být instalace, zatímco jiná část se stahuje.</span><span class="sxs-lookup"><span data-stu-id="ec4db-116">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="ec4db-117">V důsledku toho je pokrok odeslán zpět (to znamená, psaný) do`m_downloadSoFar` `m_installSoFar`sekce MMIO jako dvě čísla ( a ), která se zvyšují z 0 na 255.</span><span class="sxs-lookup"><span data-stu-id="ec4db-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="ec4db-118">Při zápisu 255 a ukončení rozhraní .NET Framework je instalace dokončena.</span><span class="sxs-lookup"><span data-stu-id="ec4db-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="ec4db-119">**Ukončovací kódy**.</span><span class="sxs-lookup"><span data-stu-id="ec4db-119">**Exit codes**.</span></span> <span data-ttu-id="ec4db-120">Následující ukončovací kódy z příkazu pro volání redistribuovatelného programu rozhraní .NET Framework 4.5 označují, zda bylo nastavení úspěšné nebo neúspěšné:</span><span class="sxs-lookup"><span data-stu-id="ec4db-120">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="ec4db-121">0 - Instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ec4db-121">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="ec4db-122">3010 – Instalace byla úspěšně dokončena. je nutné restartovat systém.</span><span class="sxs-lookup"><span data-stu-id="ec4db-122">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="ec4db-123">1602 – Instalace byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="ec4db-123">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="ec4db-124">Všechny ostatní kódy - Instalační program zjistil chyby; zkontrolujte podrobnosti o souborech protokolu vytvořených v %temp%.</span><span class="sxs-lookup"><span data-stu-id="ec4db-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="ec4db-125">**Zrušení instalace**.</span><span class="sxs-lookup"><span data-stu-id="ec4db-125">**Canceling setup**.</span></span> <span data-ttu-id="ec4db-126">Nastavení můžete kdykoli zrušit pomocí `Abort` metody pro `m_downloadAbort` nastavení `m_ installAbort` příznaků a v části MMIO.</span><span class="sxs-lookup"><span data-stu-id="ec4db-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="ec4db-127">Ukázka chaineru</span><span class="sxs-lookup"><span data-stu-id="ec4db-127">Chainer Sample</span></span>

<span data-ttu-id="ec4db-128">Ukázka Chainer tiše spustí a sleduje nastavení rozhraní .NET Framework 4.5 při zobrazení průběhu.</span><span class="sxs-lookup"><span data-stu-id="ec4db-128">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="ec4db-129">Tato ukázka je podobná ukázky Chainer pro rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec4db-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="ec4db-130">Kromě toho se však může vyhnout restartování systému zpracováním okna se zprávou pro zavření aplikací rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec4db-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="ec4db-131">Informace o tomto poli se zprávou naleznete v [tématu Snížení restartování systému během instalace rozhraní .NET Framework 4.5](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="ec4db-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="ec4db-132">Tuto ukázku můžete použít s instalačním programem rozhraní .NET Framework 4. v tomto scénáři zpráva jednoduše není odeslána.</span><span class="sxs-lookup"><span data-stu-id="ec4db-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="ec4db-133">Je nutné spustit příklad jako správce.</span><span class="sxs-lookup"><span data-stu-id="ec4db-133">You must run the example as an administrator.</span></span>

<span data-ttu-id="ec4db-134">Kompletní řešení sady Visual Studio pro [ukázku chaineru rozhraní .NET Framework 4.5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) si můžete stáhnout z galerie ukázek MSDN.</span><span class="sxs-lookup"><span data-stu-id="ec4db-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="ec4db-135">Následující části popisují významné soubory v této ukázce: MMIOChainer.h, ChainingdotNet4.cpp a IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="ec4db-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="ec4db-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="ec4db-136">MMIOChainer.h</span></span>

- <span data-ttu-id="ec4db-137">Soubor MMIOChainer.h (viz [úplný kód)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)obsahuje definici datové struktury a základní třídu, ze které by měla být odvozena třída chainer.</span><span class="sxs-lookup"><span data-stu-id="ec4db-137">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="ec4db-138">Rozhraní .NET Framework 4.5 rozšiřuje datovou strukturu MMIO tak, aby zpracovávala data, která instalační program rozhraní .NET Framework 4.5 potřebuje.</span><span class="sxs-lookup"><span data-stu-id="ec4db-138">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="ec4db-139">Změny struktury MMIO jsou zpětně kompatibilní, takže řetězeři rozhraní .NET Framework 4 mohou pracovat s nastavením rozhraní .NET Framework 4.5 bez nutnosti rekompilace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="ec4db-140">Tento scénář však nepodporuje funkci pro snížení restartování systému.</span><span class="sxs-lookup"><span data-stu-id="ec4db-140">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="ec4db-141">Pole verze poskytuje způsob identifikace revizí struktury a formátu zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec4db-141">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="ec4db-142">Nastavení rozhraní .NET Framework určuje verzi rozhraní chainer `VirtualQuery` voláním funkce k určení velikosti mapování souborů.</span><span class="sxs-lookup"><span data-stu-id="ec4db-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="ec4db-143">Pokud je velikost dostatečně velká, aby se přizpůsobila poli verze, použije nastavení rozhraní .NET Framework zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ec4db-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="ec4db-144">Pokud je mapování souborů příliš malé na to, aby obsahovalo pole verze, což je případ rozhraní .NET Framework 4, proces instalace předpokládá verzi 0 (4).</span><span class="sxs-lookup"><span data-stu-id="ec4db-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="ec4db-145">Pokud chainer nepodporuje verzi zprávy, kterou chce odeslat instalační program rozhraní .NET Framework, předpokládá nastavení rozhraní .NET Framework odpověď na ignorování.</span><span class="sxs-lookup"><span data-stu-id="ec4db-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="ec4db-146">Datová struktura MMIO je definována takto:</span><span class="sxs-lookup"><span data-stu-id="ec4db-146">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="ec4db-147">Datová struktura by neměla `MmioDataStructure` být používána přímo; použijte `MmioChainer` třídu místo toho k implementaci chainer.</span><span class="sxs-lookup"><span data-stu-id="ec4db-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="ec4db-148">Odvodit z třídy `MmioChainer` zřetězit rozhraní .NET Framework 4.5 redistributable.</span><span class="sxs-lookup"><span data-stu-id="ec4db-148">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="ec4db-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="ec4db-149">IProgressObserver.h</span></span>

- <span data-ttu-id="ec4db-150">Soubor IProgressObserver.h implementuje pozorovatele průběhu[(viz úplný kód).](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)</span><span class="sxs-lookup"><span data-stu-id="ec4db-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="ec4db-151">Tento pozorovatel získá oznámení o průběhu stahování a `char`instalace (zadáno jako nepodepsané , 0-255, označující 1%-100% dokončení).</span><span class="sxs-lookup"><span data-stu-id="ec4db-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="ec4db-152">Pozorovatel je také upozorněn, když chainee odešle zprávu a pozorovatel by měl odeslat odpověď.</span><span class="sxs-lookup"><span data-stu-id="ec4db-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="ec4db-153">Řetězové dotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="ec4db-153">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="ec4db-154">[ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) soubor implementuje třídu, `Server` která `MmioChainer` je odvozena z třídy a přepíše příslušné metody pro zobrazení informací o průběhu.</span><span class="sxs-lookup"><span data-stu-id="ec4db-154">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="ec4db-155">MmioChainer vytvoří oddíl se zadaným názvem oddílu a inicializuje chainer se zadaným názvem události.</span><span class="sxs-lookup"><span data-stu-id="ec4db-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="ec4db-156">Název události je uložen v namapované datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="ec4db-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="ec4db-157">Názvy oddílů a událostí byste měli udělat jedinečnými.</span><span class="sxs-lookup"><span data-stu-id="ec4db-157">You should make the section and event names unique.</span></span> <span data-ttu-id="ec4db-158">Třída `Server` v následujícím kódu spustí zadaný instalační program, sleduje jeho průběh a vrací ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="ec4db-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="ec4db-159">Instalace je spuštěna metodou Main.</span><span class="sxs-lookup"><span data-stu-id="ec4db-159">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="ec4db-160">Před spuštěním instalace chainer zkontroluje, zda je rozhraní .NET Framework `IsNetFx4Present`4.5 již nainstalováno voláním :</span><span class="sxs-lookup"><span data-stu-id="ec4db-160">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="ec4db-161">Můžete změnit cestu spustitelného souboru (Setup.exe v `Launch` příkladu) v metodě přejděte na jeho správné umístění nebo přizpůsobit kód k určení umístění.</span><span class="sxs-lookup"><span data-stu-id="ec4db-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="ec4db-162">Základní `MmioChainer` třída poskytuje `Run()` metodu blokování, kterou volá odvozená třída.</span><span class="sxs-lookup"><span data-stu-id="ec4db-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="ec4db-163">Metoda `Send` zachycuje a zpracovává zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec4db-163">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="ec4db-164">V této verzi rozhraní .NET Framework je jedinou podporovanou zprávou zpráva o zavření aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
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

- <span data-ttu-id="ec4db-165">Údaje o průběhu `char` jsou nepodepsané mezi 0 (0 %) a 255 (100 %).</span><span class="sxs-lookup"><span data-stu-id="ec4db-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="ec4db-166">HRESULT je předán `Finished` metodě.</span><span class="sxs-lookup"><span data-stu-id="ec4db-166">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="ec4db-167">Redistribuovatelné rozhraní .NET Framework 4.5 obvykle zapisuje mnoho zpráv o průběhu a jednu zprávu, která označuje dokončení (na straně chainer).</span><span class="sxs-lookup"><span data-stu-id="ec4db-167">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="ec4db-168">Také čte asynchronně, hledá `Abort` záznamy.</span><span class="sxs-lookup"><span data-stu-id="ec4db-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="ec4db-169">Pokud obdrží `Abort` záznam, zruší instalaci a zapíše dokončený záznam s E_ABORT jako jeho data po instalaci byla přerušena a operace instalace byly vráceny zpět.</span><span class="sxs-lookup"><span data-stu-id="ec4db-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="ec4db-170">Typický server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak `Server::CreateSection`je znázorněno v předchozím příkladu `CreateProcess` kódu v ) a `-pipe someFileSectionName` spustí redistribuovatelné pomocí metody a předáním názvu kanálu s možností.</span><span class="sxs-lookup"><span data-stu-id="ec4db-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="ec4db-171">Server by `OnProgress`měl `Send`implementovat , a `Finished` metody s kódem specifické pro použití aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec4db-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec4db-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec4db-172">See also</span></span>

- [<span data-ttu-id="ec4db-173">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ec4db-173">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="ec4db-174">Nasazení</span><span class="sxs-lookup"><span data-stu-id="ec4db-174">Deployment</span></span>](index.md)
