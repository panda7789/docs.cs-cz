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
ms.openlocfilehash: bdd2832f112706cef6050774ce3f6db5a940424a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052090"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Postupy: Získání procesu z instalačního programu .NET Framework 4.5

.NET Framework 4,5 je Distribuovatelný modul runtime. Pokud vyvíjíte aplikace pro tuto verzi .NET Framework, můžete zahrnout (zřetězit) .NET Framework nastavení 4,5 jako součást instalace aplikace. Pokud chcete prezentovat vlastní nebo sjednocené prostředí pro nastavení, můžete chtít tiche spustit nastavení .NET Framework 4,5 a sledovat jeho průběh a zároveň zobrazit průběh instalace vaší aplikace. Pokud chcete povolit tiché sledování, .NET Framework nastavení 4,5 (které jde sledovat) definuje protokol pomocí segmentu v/v (MMIO) mapované paměti ke komunikaci s vaším nastavením (sledovací proces nebo chainer). Tento protokol definuje způsob, jak může chainer získat informace o průběhu, získat podrobné výsledky, reagovat na zprávy a zrušit nastavení .NET Framework 4,5.

- **Vyvolání**. Chcete-li volat .NET Framework 4,5 nastavení a získávat informace o průběhu z části MMIO, musí instalační program provést následující akce:

    1. Zavolejte Distribuovatelný program .NET Framework 4,5:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        Kde *název oddílu* je libovolný název, který chcete použít k identifikaci vaší aplikace. .NET Framework instalační program asynchronně načítá a zapisuje do MMIO oddílu, takže v této době může být užitečné používat události a zprávy. V tomto příkladu je proces instalace .NET Framework vytvořen konstruktorem, který obě přiděluje oddíl MMIO (`TheSectionName`) a definuje událost (`TheEventName`):

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Nahraďte prosím názvy názvy, které jsou jedinečné pro instalační program.

    2. Přečtěte si část MMIO. V .NET Framework 4,5 jsou operace stažení a instalace současné: V průběhu stahování jiné součásti se může nainstalovat jedna součást .NET Framework. V důsledku toho se do části MMIO pošle zpět (tj. zápis) jako dvě čísla (`m_downloadSoFar` a `m_installSoFar`), která se zvyšují od 0 do 255. Po napsání 255 a ukončení .NET Framework se instalace dokončí.

- **Ukončovací kódy**. Následující ukončovací kódy z příkazu pro volání nástroje .NET Framework 4,5 Redistributable program označují, zda byla instalace úspěšná nebo neúspěšná:

  - 0 – instalace byla úspěšně dokončena.

  - 3010 – instalace byla úspěšně dokončena. je vyžadováno restartování systému.

  - 1602 – instalace byla zrušena.

  - Všechny ostatní kódy – při instalaci došlo k chybám. Podrobnější informace najdete v souborech protokolu vytvořených v% Temp%.

- **Ruší se instalace**. Instalaci můžete kdykoli zrušit pomocí `Abort` metody pro `m_downloadAbort` nastavení příznaků a `m_ installAbort` v oddílu MMIO.

## <a name="chainer-sample"></a>Ukázka řetězu

Ukázka zřetězení Tichy spustí a sleduje nastavení .NET Framework 4,5 během zobrazování průběhu. Tato ukázka je podobná ukázce řetězení, který je k dispozici pro .NET Framework 4. Kromě toho se může vyhnout restartování systému tím, že zpracovává okno se zprávou pro uzavírání aplikací .NET Framework 4. Informace o tomto okně se zprávou najdete v tématu [zmenšení systému restartování během instalace .NET Framework 4,5](reducing-system-restarts.md). Tuto ukázku můžete použít s instalačním programem .NET Framework 4; v takovém případě se zpráva jednoduše neposílá.

> [!WARNING]
> Příklad musíte spustit jako správce.

Kompletní řešení sady Visual Studio pro [ukázku .NET Framework 4,5 chainer](https://go.microsoft.com/fwlink/?LinkId=231345) si můžete stáhnout z Galerie UKÁZEK na webu MSDN.

V následujících částech najdete popis důležitých souborů v této ukázce: MMIOChainer. h, ChainingdotNet4. cpp a IProgressObserver. h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- Soubor MMIOChainer. h (viz [kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231369)) obsahuje definici datové struktury a základní třídu, ze které by měla být odvozena třída řetězení. .NET Framework 4,5 rozšiřuje strukturu dat MMIO pro zpracování dat, která vyžaduje Instalační program .NET Framework 4,5. Změny struktury MMIO jsou zpětně kompatibilní, takže .NET Framework 4 chainer může pracovat s nastavením .NET Framework 4,5 bez nutnosti opětovné kompilace. Tento scénář ale nepodporuje funkci pro snížení restartu systému.

    Pole verze poskytuje způsob identifikace revizí struktury a formátu zpráv. Instalační program určuje verzi rozhraní chainer voláním `VirtualQuery` funkce k určení velikosti mapování souboru. .NET Framework Pokud je velikost dostatečně velká, aby se vešla do pole verze, .NET Framework instalační program používá zadanou hodnotu. Pokud mapování souborů je příliš malé, aby obsahovalo pole verze, což je případ s .NET Framework 4, proces instalace předpokládá, že verze je 0 (4). Pokud řetěz nepodporuje verzi zprávy, kterou .NET Framework instalační program potřebuje odeslat, .NET Framework instalační program předpokládá odpověď ignore.

    Struktura dat MMIO je definována takto:

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

- Struktura dat by neměla být použita přímo; místo toho `MmioChainer` použijte třídu k implementaci vašeho řetězu. `MmioDataStructure` Je odvozen od `MmioChainer` třídy za účelem zřetězení .NET Framework 4,5 distribuovatelné.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- Soubor IProgressObserver. h Implementuje pozorovatele průběhu ([Viz kompletní kód](https://go.microsoft.com/fwlink/?LinkId=231370)). Tento pozorovatel se upozorní na průběh stahování a instalace (zadaný jako nepodepsaný `char`, 0-255, který indikuje 1%-100% dokončení). Pozorovatel je upozorněn také v případě, že chainee odesílá zprávu a pozorovatel by měl poslat odpověď.

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

- Soubor [chainingdotnet 4.5. cpp](https://go.microsoft.com/fwlink/?LinkId=231368) implementuje `Server` třídu, která `MmioChainer` je odvozena z třídy, a přepíše příslušné metody pro zobrazení informací o průběhu. MmioChainer vytvoří oddíl se zadaným názvem oddílu a inicializuje řetěz se zadaným názvem události. Název události je uložen v mapované datové struktuře. Název oddílu a události by měl být jedinečný. `Server` Třída v následujícím kódu spustí zadaný instalační program, monitoruje jeho průběh a vrátí ukončovací kód.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Instalace se spustí v metodě Main.

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

- Před spuštěním instalace řetěz zkontroluje, jestli je už .NET Framework 4,5 nainstalovaná voláním `IsNetFx4Present`:

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

- Můžete změnit cestu spustitelného souboru (Setup. exe v příkladu) v `Launch` metodě, aby odkazovala na správné umístění, nebo přizpůsobit kód pro určení umístění. Základní třída poskytuje blokující `Run()` metodu, která volá odvozenou třídu. `MmioChainer`

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

- `Send` Metoda zachycuje a zpracovává zprávy. V této verzi .NET Framework jediná podporovaná zpráva je zpráva Zavřít aplikaci.

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

- Data o průběhu jsou bez `char` znaménka mezi 0 (0%) a 255 (100%).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- Hodnota HRESULT je předána `Finished` metodě.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > Distribuovatelné součásti .NET Framework 4,5 obvykle zapisuje mnoho zpráv o průběhu a jednu zprávu, která indikuje dokončení (na straně řetězení). Také se čte asynchronně a hledá `Abort` záznamy. Pokud obdrží `Abort` záznam, zruší instalaci a zapíše dokončený záznam se E_ABORT jako jeho data po přerušení instalace a instalaci operací byla vrácena zpět.

Typický Server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak je znázorněno v předchozím příkladu kódu v `Server::CreateSection`části) a spustí Distribuovatelný `CreateProcess` pomocí metody a předání názvu kanálu s `-pipe someFileSectionName` možností. Server by měl implementovat `OnProgress`metody `Send`, a `Finished` s kódem specifickým pro uživatelské rozhraní aplikace.

## <a name="see-also"></a>Viz také:

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Nasazení](index.md)
