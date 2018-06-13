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
ms.openlocfilehash: 84bd96f27e8276546bef0dd9994163ccd843ac20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393306"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Postupy: Získání procesu z instalačního programu .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je modul runtime redistributable. Pokud vyvíjíte aplikace pro tuto verzi rozhraní .NET Framework, můžete zahrnout (řetězec) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalace požadovaných součástí instalace vaší aplikace. K dispozici instalace přizpůsobené nebo jednotné prostředí, můžete chtít spustit bezobslužně [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalační program a jeho průběh sledovat při zobrazování průběh instalačního programu vaší aplikace. Povolit bezobslužné sledování [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalačního programu (stažené lze sledovat) definuje protokol pomocí segment mapované paměti vstupně-výstupních operací (MMIO) ke komunikaci s vaší instalace (sledovacích procesů nebo zřetězeného souboru). Tento protokol definuje způsob, jak zřetězeného souboru získat informace o průběhu, získat podrobné výsledky, odpovězte na otázky a zrušit [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalační program.  
  
-   **Volání** .  K volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalační program a přijímat informace o průběhu z části MMIO, instalační program musíte provést následující:  
  
    1.  Volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         kde *název oddílu* je libovolný název, kterou chcete použít k identifikaci vaší aplikace. Instalační program rozhraní .NET framework čte a zapisuje do části MMIO asynchronně, takže je může být výhodné použít události a zprávy během této doby. V příkladu se vytvoří procesu instalace rozhraní .NET Framework konstruktorem, obě přiděluje části MMIO (`TheSectionName`) a definuje události (`TheEventName`):  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Tyto názvy prosím nahraďte názvy, které jsou jedinečné pro instalační program.  
  
    2.  Čtení z části MMIO. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], stahování a instalace operace jsou souběžných: jeden součástí rozhraní .NET Framework může instalace, zatímco jiné části je stahování. V důsledku toho se odesílají průběh (které se zapíše) zpět do části MMIO jako dvou čísel (`m_downloadSoFar` a `m_installSoFar`), zvýšit od 0 do 255. Při zápisu 255 a ukončí rozhraní .NET Framework, instalace je dokončena.  
  
-   **Kódy ukončení**. Kódy ukončení následující příkaz k volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable programu označuje, zda má instalace byla úspěšná nebo neúspěšná:  
  
    -   0 – instalace byla úspěšně dokončena.  
  
    -   3010 – instalace byla dokončena úspěšně; je vyžadováno restartování systému.  
  
    -   1602 – instalace byla zrušena.  
  
    -   Všechny ostatní kódy – instalační program zjistil chyb; Zkontrolujte soubory protokolů vytvořené v % temp % podrobnosti.  
  
-   **Zrušení instalace**. Instalační program můžete kdykoli zrušit pomocí `Abort` metodu a nastavit `m_downloadAbort` a `m_ installAbort` příznaky v části MMIO.  
  
## <a name="chainer-sample"></a>Ukázka zřetězeného souboru  
 Ukázka zřetězeného souboru bezobslužná spustí a sleduje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalace při zobrazování průběhu. Tato ukázka je podobný ukázce zřetězeného souboru zadaná pro rozhraní .NET Framework 4. Však kromě toho se můžete vyhnout restartování systému zpracování okně pro zavření aplikace rozhraní .NET Framework 4. Informace o toto okno se zprávou najdete v tématu [snižuje restartuje během rozhraní .NET Framework 4.5 instalací systému](../../../docs/framework/deployment/reducing-system-restarts.md). Můžete tuto ukázku použít instalační program rozhraní .NET Framework 4; v tomto scénáři se zprávy jednoduše neposílají.  
  
> [!WARNING]
>  V příkladu musíte spustit jako správce.  
  
 Si můžete stáhnout kompletní řešení sady Visual Studio pro [rozhraní .NET Framework 4.5 zřetězeného souboru ukázka](http://go.microsoft.com/fwlink/?LinkId=231345) z Galerie ukázky na webu MSDN.  
  
 Následující části popisují důležité soubory v této ukázce: MMIOChainer.h, ChainingdotNet4.cpp a IProgressObserver.h.  
  
#### <a name="mmiochainerh"></a>MMIOChainer.h  
  
-   Soubor MMIOChainer.h (najdete v části [dokončení kódu](http://go.microsoft.com/fwlink/?LinkId=231369)) obsahuje definici strukturu dat a základní třídy, ze kterého by měl být odvozen třídě zřetězeného souboru. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozšiřuje MMIO datovou strukturu pro zpracování dat, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] musí instalační program. Změny na strukturu MMIO jsou zpětně kompatibilní, takže zřetězeného souboru rozhraní .NET Framework 4 můžete pracovat se instalační program rozhraní .NET Framework 4.5 bez nutnosti rekompilace. Tento scénář však nepodporuje funkci pro snížení zatížení restartování systému.  
  
     Pole verze poskytuje způsob identifikace revize pro formát strukturu a zprávy.  Instalační program rozhraní .NET Framework Určuje verzi rozhraní zřetězeného souboru voláním `VirtualQuery` funkce k určení velikosti mapování souboru.  Pokud je velikost dostatečně velké na to, aby dokázala pojmout pole verze, používá instalační program rozhraní .NET Framework se zadanou hodnotou. Pokud mapování souboru je příliš malá, aby obsahovat pole verze, která je tomu u rozhraní .NET Framework 4, předpokládá se v procesu instalace verze 0 (4). Pokud zřetězeného souboru nepodporuje verzi zprávu, která chce poslat instalační program rozhraní .NET Framework, instalační program rozhraní .NET Framework předpokládá odpověď ignorovat.  
  
     Datová struktura MMIO je definován následujícím způsobem:  
  
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
  
-   `MmioDataStructure` Datová struktura, neměl by se používat přímo; použít `MmioChainer` místo třídy k implementaci vašeho zřetězeného souboru. Odvozena od `MmioChainer` třídy řetězu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.  
  
#### <a name="iprogressobserverh"></a>IProgressObserver.h  
  
-   Soubor IProgressObserver.h implementuje pozorovatel průběh ([najdete kompletní kódu](http://go.microsoft.com/fwlink/?LinkId=231370)). Získá tento pozorovatel informováni o průběh stahování a instalace (zadaný jako nepodepsaný `char`, 0 – 255, která udává, 1 – 100 % dokončení). Pozorovatel také zasláno oznámení, když chainee odešle zprávu a pozorovatel by měl odeslání odpovědi.  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a>ChainingdotNet4.5.cpp  
  
-   [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) souboru implementuje `Server` třída, která je odvozena z `MmioChainer` třídy a přepíše příslušné metody zobrazíte informace o průběhu. MmioChainer vytvoří oddíl s názvem zadaný oddíl a inicializuje zřetězeného souboru s názvem zadané události. Název události se uloží do namapované datovou strukturu. Název oddílu a událostí měli vytvořit jedinečný. `Server` Třídy v následujícím kódu spustí zadaný instalační program, monitoruje jejím průběhu a vrátí ukončovací kód.  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     Instalace je spuštěn v metodě hlavní.  
  
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
  
-   Před spuštěním instalace, zřetězeného souboru kontroluje, zda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je již nainstalována voláním `IsNetFx4Present`:  
  
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
  
-   Cesta ke spustitelnému souboru (Setup.exe v příkladu) můžete změnit `Launch` metoda přejděte na správné umístění, nebo upravit kód k určení umístění. `MmioChainer` Poskytuje základní třídu blokování `Run()` metoda, která volá odvozené třídy.  
  
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
  
-   `Send` Metoda přijímá a zpracovává zprávy.  V této verzi rozhraní .NET Framework pouze podporované zpráva je zpráv zavřít aplikaci.  
  
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
  
-   Průběh dat je nepodepsaný `char` od 0 (0 %) do 255 (100 %).  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   Hodnota HRESULT předána `Finished` metoda.  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Redistributable obvykle zapíše mnoho zprávy o průběhu a do jedné zprávy, která označuje dokončení (na straně zřetězeného souboru). Čte také asynchronně, hledá `Abort` záznamy. Pokud obdrží `Abort` záznamů, se zruší instalace a zapíše dokončení záznam s E_ABORT jako jeho data po instalaci byla přerušena a operací instalačního programu byly vráceny zpět.  
  
 Typický server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak je znázorněno v předchozím příkladu kódu v `Server::CreateSection`) a spouští redistribuovatelný balíček pomocí `CreateProcess` metoda a předání kanálu název s `-pipe someFileSectionName` možnost. Server by měla implementovat `OnProgress`, `Send`, a `Finished` metody s kódu pro konkrétní uživatelského rozhraní aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Nasazení](../../../docs/framework/deployment/index.md)
