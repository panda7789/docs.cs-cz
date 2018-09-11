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
ms.openlocfilehash: 8c27bdb75ef9950d0b2b32f742b38e141cf4981b
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268991"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Postupy: Získání procesu z instalačního programu .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je distribuovatelné součásti modulu runtime. Pokud vyvíjíte aplikace pro tuto verzi rozhraní .NET Framework, můžete zahrnout (řetězec) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalace požadovaných součástí vaší aplikace. Účelem představení prostředí přizpůsobené nebo jednotný instalační program, můžete chtít spustit bezobslužně [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nastavení a sledovat její průběh při zobrazování průběh instalačního programu vaší aplikace. Umožňuje bezobslužné sledování [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalačního programu (což lze sledovat) definuje protokol pomocí segment mapované paměti / v (MMIO) ke komunikaci s instalačním programem (sledovacích procesů nebo chainer). Definuje způsob, jakým chainer získat informace o průběhu, získat podrobné výsledky, reagovat na zprávy a zrušit tento protokol [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] instalační program.  
  
-   **Vyvolání** .  Chcete-li volat [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nastavení a přijímat informace o průběhu z část MMIO, instalační program musíte provést následující:  
  
    1.  Volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]distribuovatelné součásti programu:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         kde *název oddílu* je libovolný název, kterou chcete použít k identifikaci vaší aplikace. Instalační program rozhraní .NET framework čte a zapisuje do MMIO část asynchronně, takže je může být výhodné používat události a zprávy během této doby. V tomto příkladu se vytvoří proces instalace rozhraní .NET Framework pomocí konstruktoru, že oba přiděluje MMIO část (`TheSectionName`) a definuje události (`TheEventName`):  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Nahraďte názvy, které jsou jedinečné pro instalační program tyto názvy.  
  
    2.  Čtení z oddílu MMIO. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], operace stažení a instalaci jsou souběžných: jednu část rozhraní .NET Framework může instalace, zatímco jiné části stahuje. V důsledku toho se průběh odešle zpět (který je napsán) do části MMIO jako dvou čísel (`m_downloadSoFar` a `m_installSoFar`) zvýšit počet od 0 do 255. Při zápisu 255 a ukončí rozhraní .NET Framework, je instalace dokončena.  
  
-   **Kódy ukončení příkazu**. Následující kódy ukončení příkazu k volání [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] distribuovatelné součásti programu označuje, zda má instalační program úspěšné nebo neúspěšné:  
  
    -   0 – instalace byla úspěšně dokončena.  
  
    -   3010 – instalace byla dokončena úspěšně; je třeba restartovat systém.  
  
    -   1602 – instalace byla zrušena.  
  
    -   Všechny ostatní kódy – instalační program zjistil chyby; Zkontrolujte soubory protokolů vytvořené ve složce % temp % podrobnosti.  
  
-   **Ruší se instalace**. Instalační program můžete kdykoli zrušit pomocí `Abort` metody nastavte `m_downloadAbort` a `m_ installAbort` příznaky v části MMIO.  
  
## <a name="chainer-sample"></a>Ukázka chainer  
 Ukázka Chainer tiše spustí a sleduje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] při zobrazování průběhu instalace. Tento příklad je podobný vzorku Chainer k dispozici pro rozhraní .NET Framework 4. Ale navíc ji můžete zabránit restartování systému zpracováním okně se zprávou pro uzavření aplikace rozhraní .NET Framework 4. Informace o toto okno se zprávou, naleznete v tématu [snížení systému restartování během 4.5 instalaci rozhraní .NET Framework](../../../docs/framework/deployment/reducing-system-restarts.md). Můžete tuto ukázku použít s instalačním programem rozhraní .NET Framework 4; v tomto scénáři není zprávu jednoduše odeslat.  
  
> [!WARNING]
>  V příkladu musíte spustit jako správce.  
  
 Můžete si stáhnout kompletní řešení sady Visual Studio pro [ukázku .NET Framework 4.5 Chainer](https://go.microsoft.com/fwlink/?LinkId=231345) z Galerie ukázek na webu MSDN.  
  
 Následující části popisují důležité soubory v této ukázce: MMIOChainer.h ChainingdotNet4.cpp a IProgressObserver.h.  
  
#### <a name="mmiochainerh"></a>MMIOChainer.h  
  
-   Soubor MMIOChainer.h (viz [dokončení kódu](https://go.microsoft.com/fwlink/?LinkId=231369)) obsahuje definice struktury dat a základní třídu, ze kterého by měla být odvozena třída zřetězovatele. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Rozšiřuje datová struktura MMIO zpracování dat, která [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] musí instalační program. Změny struktury MMIO jsou zpětně kompatibilní, umožní práci s instalačním programem rozhraní .NET Framework 4.5 chainer rozhraní .NET Framework 4 bez nové kompilace. Tento scénář ale nepodporuje funkci pro snížení restartování systému.  
  
     Pole verze poskytuje způsob identifikace revize pro strukturu a zprávu formátu.  Instalační program rozhraní .NET Framework Určuje verzi rozhraní chainer voláním `VirtualQuery` funkce určit velikost mapování souborů.  Pokud je velikost dostatečně velký, aby pole verze, instalační program rozhraní .NET Framework používá zadanou hodnotu. Pokud mapování souboru je příliš malá tak, aby obsahovala pole verze, která je tomu u rozhraní .NET Framework 4, předpokládá se v procesu instalace verze 0 (4). Pokud chainer nepodporuje verzi, která požaduje instalaci rozhraní .NET Framework k odeslání zprávy, instalační program rozhraní .NET Framework předpokládá odpověď ignorovat.  
  
     Datová struktura MMIO je definovaná následujícím způsobem:  
  
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
  
-   `MmioDataStructure` Datová struktura, neměl by se používat přímo; použijte `MmioChainer` třídy místo toho implementovat vaše chainer. Odvozovat `MmioChainer` třídy do řetězce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.  
  
#### <a name="iprogressobserverh"></a>IProgressObserver.h  
  
-   Soubor IProgressObserver.h implementuje pozorovatele průběhu ([zobrazit kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231370)). Tato pozorovatel získá oznámení o průběhu stahování a instalace (stanoveno, bez znaménka `char`, 0 – 255, která 1 – 100 % dokončeno). Pozorovatel také zasláno oznámení, když chainee odešle zprávu a pozorovatel by měl odeslat odpověď.  
  
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
  
-   [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) implementuje `Server` třída, která je odvozena z `MmioChainer` třídy a přepisuje patřičné metody k zobrazení informací o průběhu. MmioChainer vytvoří oddíl s názvem zadaný oddíl a inicializuje chainer pomocí zadaného názvu události. Název události je uložen ve struktuře mapovaná data. Název oddílu a události pro byste měli vytvořit jedinečný. `Server` Třídy v následujícím kódu spustí zadaný instalační program, monitoruje průběh a vrátí ukončovací kód.  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     Instalace je spuštěn v hlavní metodě.  
  
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
  
-   Před spuštěním instalace chainer kontroluje, jestli [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je již nainstalována voláním `IsNetFx4Present`:  
  
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
  
-   Cesta ke spustitelnému souboru (Setup.exe v příkladu) můžete změnit v `Launch` metoda odkazovat na správné umístění nebo přizpůsobení kódu k určení umístění. `MmioChainer` Poskytuje základní třídu blokování `Run()` metodu, která volá odvozené třídy.  
  
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
  
-   `Send` Metoda zachycuje a zpracovávat zprávy.  V této verzi rozhraní .NET Framework pouze podporované zpráva je zprávou zavřít aplikaci.  
  
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
  
-   Průběh dat je bez znaménka `char` od 0 (0 %) do 255 (100 %).  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   Hodnota HRESULT je předán `Finished` metody.  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Redistributable obvykle zapisuje mnoho zprávy o průběhu a jedna zpráva, která označuje dokončení (na straně chainer). Přečte také asynchronně, hledá `Abort` záznamy. Pokud obdrží `Abort` záznam, zruší instalace a zapíše dokončení záznam s E_ABORT jako svá data po instalaci se zrušilo a operace instalace byly vráceny zpět.  
  
 Typický server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak je znázorněno v předchozím příkladu kódu `Server::CreateSection`) a spustí Distribuovatelný pomocí `CreateProcess` metoda a předá kanálu název s `-pipe someFileSectionName` možnost. Server by měly implementovat `OnProgress`, `Send`, a `Finished` metody s kód specifický pro uživatelské rozhraní aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Nasazení](../../../docs/framework/deployment/index.md)
