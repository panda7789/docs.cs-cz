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
ms.openlocfilehash: 5c71816b1bd2e9c95e8c7efb44e3e689dce4ab93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853973"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="85d5b-102">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="85d5b-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="85d5b-103">.NET Framework 4,5 je Distribuovatelný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="85d5b-103">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="85d5b-104">Pokud vyvíjíte aplikace pro tuto verzi .NET Framework, můžete zahrnout (zřetězit) .NET Framework nastavení 4,5 jako součást instalace aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d5b-104">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="85d5b-105">Pokud chcete prezentovat vlastní nebo sjednocené prostředí pro nastavení, můžete chtít tiche spustit nastavení .NET Framework 4,5 a sledovat jeho průběh a zároveň zobrazit průběh instalace vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d5b-105">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="85d5b-106">Pokud chcete povolit tiché sledování, .NET Framework nastavení 4,5 (které jde sledovat) definuje protokol pomocí segmentu v/v (MMIO) mapované paměti ke komunikaci s vaším nastavením (sledovací proces nebo chainer).</span><span class="sxs-lookup"><span data-stu-id="85d5b-106">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="85d5b-107">Tento protokol definuje způsob, jak může chainer získat informace o průběhu, získat podrobné výsledky, reagovat na zprávy a zrušit nastavení .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="85d5b-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="85d5b-108">**Vyvolání**.</span><span class="sxs-lookup"><span data-stu-id="85d5b-108">**Invocation**.</span></span> <span data-ttu-id="85d5b-109">Chcete-li volat .NET Framework 4,5 nastavení a získávat informace o průběhu z části MMIO, musí instalační program provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="85d5b-109">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="85d5b-110">Zavolejte Distribuovatelný program .NET Framework 4,5:</span><span class="sxs-lookup"><span data-stu-id="85d5b-110">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="85d5b-111">Kde *název oddílu* je libovolný název, který chcete použít k identifikaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d5b-111">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="85d5b-112">.NET Framework instalační program asynchronně načítá a zapisuje do MMIO oddílu, takže v této době může být užitečné používat události a zprávy.</span><span class="sxs-lookup"><span data-stu-id="85d5b-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="85d5b-113">V tomto příkladu je proces instalace .NET Framework vytvořen konstruktorem, který obě přiděluje oddíl MMIO (`TheSectionName`) a definuje událost (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="85d5b-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="85d5b-114">Nahraďte prosím názvy názvy, které jsou jedinečné pro instalační program.</span><span class="sxs-lookup"><span data-stu-id="85d5b-114">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="85d5b-115">Přečtěte si část MMIO.</span><span class="sxs-lookup"><span data-stu-id="85d5b-115">Read from the MMIO section.</span></span> <span data-ttu-id="85d5b-116">V .NET Framework 4,5 jsou operace stažení a instalace současné: V průběhu stahování jiné součásti se může nainstalovat jedna součást .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85d5b-116">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="85d5b-117">V důsledku toho se do části MMIO pošle zpět (tj. zápis) jako dvě čísla (`m_downloadSoFar` a `m_installSoFar`), která se zvyšují od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="85d5b-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="85d5b-118">Po napsání 255 a ukončení .NET Framework se instalace dokončí.</span><span class="sxs-lookup"><span data-stu-id="85d5b-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="85d5b-119">**Ukončovací kódy**.</span><span class="sxs-lookup"><span data-stu-id="85d5b-119">**Exit codes**.</span></span> <span data-ttu-id="85d5b-120">Následující ukončovací kódy z příkazu pro volání nástroje .NET Framework 4,5 Redistributable program označují, zda byla instalace úspěšná nebo neúspěšná:</span><span class="sxs-lookup"><span data-stu-id="85d5b-120">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="85d5b-121">0 – instalace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="85d5b-121">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="85d5b-122">3010 – instalace byla úspěšně dokončena. je vyžadováno restartování systému.</span><span class="sxs-lookup"><span data-stu-id="85d5b-122">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="85d5b-123">1602 – instalace byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="85d5b-123">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="85d5b-124">Všechny ostatní kódy – při instalaci došlo k chybám. Podrobnější informace najdete v souborech protokolu vytvořených v% Temp%.</span><span class="sxs-lookup"><span data-stu-id="85d5b-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="85d5b-125">**Ruší se instalace**.</span><span class="sxs-lookup"><span data-stu-id="85d5b-125">**Canceling setup**.</span></span> <span data-ttu-id="85d5b-126">Instalaci můžete kdykoli zrušit pomocí `Abort` metody pro `m_downloadAbort` nastavení příznaků a `m_ installAbort` v oddílu MMIO.</span><span class="sxs-lookup"><span data-stu-id="85d5b-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="85d5b-127">Ukázka řetězu</span><span class="sxs-lookup"><span data-stu-id="85d5b-127">Chainer Sample</span></span>

<span data-ttu-id="85d5b-128">Ukázka zřetězení Tichy spustí a sleduje nastavení .NET Framework 4,5 během zobrazování průběhu.</span><span class="sxs-lookup"><span data-stu-id="85d5b-128">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="85d5b-129">Tato ukázka je podobná ukázce řetězení, který je k dispozici pro .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="85d5b-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="85d5b-130">Kromě toho se může vyhnout restartování systému tím, že zpracovává okno se zprávou pro uzavírání aplikací .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="85d5b-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="85d5b-131">Informace o tomto okně se zprávou najdete v tématu [zmenšení systému restartování během instalace .NET Framework 4,5](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="85d5b-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="85d5b-132">Tuto ukázku můžete použít s instalačním programem .NET Framework 4; v takovém případě se zpráva jednoduše neposílá.</span><span class="sxs-lookup"><span data-stu-id="85d5b-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="85d5b-133">Příklad musíte spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="85d5b-133">You must run the example as an administrator.</span></span>

<span data-ttu-id="85d5b-134">Kompletní řešení sady Visual Studio pro [ukázku .NET Framework 4,5 chainer](https://go.microsoft.com/fwlink/?LinkId=231345) si můžete stáhnout z Galerie UKÁZEK na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="85d5b-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="85d5b-135">V následujících částech najdete popis důležitých souborů v této ukázce: MMIOChainer. h, ChainingdotNet4. cpp a IProgressObserver. h.</span><span class="sxs-lookup"><span data-stu-id="85d5b-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="85d5b-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="85d5b-136">MMIOChainer.h</span></span>

- <span data-ttu-id="85d5b-137">Soubor MMIOChainer. h (viz [kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231369)) obsahuje definici datové struktury a základní třídu, ze které by měla být odvozena třída řetězení.</span><span class="sxs-lookup"><span data-stu-id="85d5b-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="85d5b-138">.NET Framework 4,5 rozšiřuje strukturu dat MMIO pro zpracování dat, která vyžaduje Instalační program .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="85d5b-138">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="85d5b-139">Změny struktury MMIO jsou zpětně kompatibilní, takže .NET Framework 4 chainer může pracovat s nastavením .NET Framework 4,5 bez nutnosti opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="85d5b-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="85d5b-140">Tento scénář ale nepodporuje funkci pro snížení restartu systému.</span><span class="sxs-lookup"><span data-stu-id="85d5b-140">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="85d5b-141">Pole verze poskytuje způsob identifikace revizí struktury a formátu zpráv.</span><span class="sxs-lookup"><span data-stu-id="85d5b-141">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="85d5b-142">Instalační program určuje verzi rozhraní chainer voláním `VirtualQuery` funkce k určení velikosti mapování souboru. .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85d5b-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="85d5b-143">Pokud je velikost dostatečně velká, aby se vešla do pole verze, .NET Framework instalační program používá zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="85d5b-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="85d5b-144">Pokud mapování souborů je příliš malé, aby obsahovalo pole verze, což je případ s .NET Framework 4, proces instalace předpokládá, že verze je 0 (4).</span><span class="sxs-lookup"><span data-stu-id="85d5b-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="85d5b-145">Pokud řetěz nepodporuje verzi zprávy, kterou .NET Framework instalační program potřebuje odeslat, .NET Framework instalační program předpokládá odpověď ignore.</span><span class="sxs-lookup"><span data-stu-id="85d5b-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="85d5b-146">Struktura dat MMIO je definována takto:</span><span class="sxs-lookup"><span data-stu-id="85d5b-146">The MMIO data structure is defined as follows:</span></span>

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

- <span data-ttu-id="85d5b-147">Struktura dat by neměla být použita přímo; místo toho `MmioChainer` použijte třídu k implementaci vašeho řetězu. `MmioDataStructure`</span><span class="sxs-lookup"><span data-stu-id="85d5b-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="85d5b-148">Je odvozen od `MmioChainer` třídy za účelem zřetězení .NET Framework 4,5 distribuovatelné.</span><span class="sxs-lookup"><span data-stu-id="85d5b-148">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="85d5b-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="85d5b-149">IProgressObserver.h</span></span>

- <span data-ttu-id="85d5b-150">Soubor IProgressObserver. h Implementuje pozorovatele průběhu ([Viz kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="85d5b-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="85d5b-151">Tento pozorovatel se upozorní na průběh stahování a instalace (zadaný jako nepodepsaný `char`, 0-255, který indikuje 1%-100% dokončení).</span><span class="sxs-lookup"><span data-stu-id="85d5b-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="85d5b-152">Pozorovatel je upozorněn také v případě, že chainee odesílá zprávu a pozorovatel by měl poslat odpověď.</span><span class="sxs-lookup"><span data-stu-id="85d5b-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="85d5b-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="85d5b-153">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="85d5b-154">Soubor [chainingdotnet 4.5. cpp](https://go.microsoft.com/fwlink/?LinkId=231368) implementuje `Server` třídu, která `MmioChainer` je odvozena z třídy, a přepíše příslušné metody pro zobrazení informací o průběhu.</span><span class="sxs-lookup"><span data-stu-id="85d5b-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="85d5b-155">MmioChainer vytvoří oddíl se zadaným názvem oddílu a inicializuje řetěz se zadaným názvem události.</span><span class="sxs-lookup"><span data-stu-id="85d5b-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="85d5b-156">Název události je uložen v mapované datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="85d5b-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="85d5b-157">Název oddílu a události by měl být jedinečný.</span><span class="sxs-lookup"><span data-stu-id="85d5b-157">You should make the section and event names unique.</span></span> <span data-ttu-id="85d5b-158">`Server` Třída v následujícím kódu spustí zadaný instalační program, monitoruje jeho průběh a vrátí ukončovací kód.</span><span class="sxs-lookup"><span data-stu-id="85d5b-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="85d5b-159">Instalace se spustí v metodě Main.</span><span class="sxs-lookup"><span data-stu-id="85d5b-159">The installation is started in the Main method.</span></span>

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

- <span data-ttu-id="85d5b-160">Před spuštěním instalace řetěz zkontroluje, jestli je už .NET Framework 4,5 nainstalovaná voláním `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="85d5b-160">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

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

- <span data-ttu-id="85d5b-161">Můžete změnit cestu spustitelného souboru (Setup. exe v příkladu) v `Launch` metodě, aby odkazovala na správné umístění, nebo přizpůsobit kód pro určení umístění.</span><span class="sxs-lookup"><span data-stu-id="85d5b-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="85d5b-162">Základní třída poskytuje blokující `Run()` metodu, která volá odvozenou třídu. `MmioChainer`</span><span class="sxs-lookup"><span data-stu-id="85d5b-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

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

- <span data-ttu-id="85d5b-163">`Send` Metoda zachycuje a zpracovává zprávy.</span><span class="sxs-lookup"><span data-stu-id="85d5b-163">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="85d5b-164">V této verzi .NET Framework jediná podporovaná zpráva je zpráva Zavřít aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85d5b-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

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

- <span data-ttu-id="85d5b-165">Data o průběhu jsou bez `char` znaménka mezi 0 (0%) a 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="85d5b-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="85d5b-166">Hodnota HRESULT je předána `Finished` metodě.</span><span class="sxs-lookup"><span data-stu-id="85d5b-166">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="85d5b-167">Distribuovatelné součásti .NET Framework 4,5 obvykle zapisuje mnoho zpráv o průběhu a jednu zprávu, která indikuje dokončení (na straně řetězení).</span><span class="sxs-lookup"><span data-stu-id="85d5b-167">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="85d5b-168">Také se čte asynchronně a hledá `Abort` záznamy.</span><span class="sxs-lookup"><span data-stu-id="85d5b-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="85d5b-169">Pokud obdrží `Abort` záznam, zruší instalaci a zapíše dokončený záznam se E_ABORT jako jeho data po přerušení instalace a instalaci operací byla vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="85d5b-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="85d5b-170">Typický Server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak je znázorněno v předchozím příkladu kódu v `Server::CreateSection`části) a spustí Distribuovatelný `CreateProcess` pomocí metody a předání názvu kanálu s `-pipe someFileSectionName` možností.</span><span class="sxs-lookup"><span data-stu-id="85d5b-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="85d5b-171">Server by měl implementovat `OnProgress`metody `Send`, a `Finished` s kódem specifickým pro uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d5b-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="85d5b-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85d5b-172">See also</span></span>

- [<span data-ttu-id="85d5b-173">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="85d5b-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [<span data-ttu-id="85d5b-174">Nasazení</span><span class="sxs-lookup"><span data-stu-id="85d5b-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
