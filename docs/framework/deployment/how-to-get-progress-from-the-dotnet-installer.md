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
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>Postupy: Získání procesu z instalačního programu .NET Framework 4.5

Rozhraní .NET Framework 4.5 je redistribuovatelný runtime. Pokud vyvíjíte aplikace pro tuto verzi rozhraní .NET Framework, můžete zahrnout (řetězové) nastavení rozhraní .NET Framework 4.5 jako předpoklad součást nastavení vaší aplikace. Chcete-li prezentovat přizpůsobené nebo jednotné nastavení, můžete bezobslužně spustit nastavení rozhraní .NET Framework 4.5 a sledovat jeho průběh a zároveň zobrazit průběh nastavení aplikace. Chcete-li povolit tiché sledování, nastavení rozhraní .NET Framework 4.5 (které lze sledovat) definuje protokol pomocí segmentu MMIO mapované ho paměti pro komunikaci s nastavením (sledovací proces nebo chainer). Tento protokol definuje způsob, jakým chainer získává informace o průběhu, získává podrobné výsledky, odpovídá na zprávy a ruší nastavení rozhraní .NET Framework 4.5.

- **Vyvolání**. Chcete-li volat instalační program rozhraní .NET Framework 4.5 a přijímat informace o průběhu z části MMIO, musí instalační program provést následující kroky:

    1. Zavolejte redistribuovatelný program rozhraní .NET Framework 4.5:

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        Kde *název oddílu* je libovolný název, který chcete použít k identifikaci vaší aplikace. Instalační program rozhraní .NET Framework čte a zapisuje do sekce MMIO asynchronně, takže může být vhodné používat události a zprávy během této doby. V příkladu je proces nastavení rozhraní .NET Framework vytvořen konstruktorem, který`TheSectionName`přiděluje oddíl`TheEventName`MMIO ( ) a definuje událost ( ):

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        Nahraďte tyto názvy názvy, které jsou jedinečné pro instalační program.

    2. Přečtěte si z oddílu MMIO. V rozhraní .NET Framework 4.5 jsou operace stahování a instalace simultánní: Jedna část rozhraní .NET Framework může být instalace, zatímco jiná část se stahuje. V důsledku toho je pokrok odeslán zpět (to znamená, psaný) do`m_downloadSoFar` `m_installSoFar`sekce MMIO jako dvě čísla ( a ), která se zvyšují z 0 na 255. Při zápisu 255 a ukončení rozhraní .NET Framework je instalace dokončena.

- **Ukončovací kódy**. Následující ukončovací kódy z příkazu pro volání redistribuovatelného programu rozhraní .NET Framework 4.5 označují, zda bylo nastavení úspěšné nebo neúspěšné:

  - 0 - Instalace byla úspěšně dokončena.

  - 3010 – Instalace byla úspěšně dokončena. je nutné restartovat systém.

  - 1602 – Instalace byla zrušena.

  - Všechny ostatní kódy - Instalační program zjistil chyby; zkontrolujte podrobnosti o souborech protokolu vytvořených v %temp%.

- **Zrušení instalace**. Nastavení můžete kdykoli zrušit pomocí `Abort` metody pro `m_downloadAbort` nastavení `m_ installAbort` příznaků a v části MMIO.

## <a name="chainer-sample"></a>Ukázka chaineru

Ukázka Chainer tiše spustí a sleduje nastavení rozhraní .NET Framework 4.5 při zobrazení průběhu. Tato ukázka je podobná ukázky Chainer pro rozhraní .NET Framework 4. Kromě toho se však může vyhnout restartování systému zpracováním okna se zprávou pro zavření aplikací rozhraní .NET Framework 4. Informace o tomto poli se zprávou naleznete v [tématu Snížení restartování systému během instalace rozhraní .NET Framework 4.5](reducing-system-restarts.md). Tuto ukázku můžete použít s instalačním programem rozhraní .NET Framework 4. v tomto scénáři zpráva jednoduše není odeslána.

> [!WARNING]
> Je nutné spustit příklad jako správce.

Kompletní řešení sady Visual Studio pro [ukázku chaineru rozhraní .NET Framework 4.5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) si můžete stáhnout z galerie ukázek MSDN.

Následující části popisují významné soubory v této ukázce: MMIOChainer.h, ChainingdotNet4.cpp a IProgressObserver.h.

#### <a name="mmiochainerh"></a>MMIOChainer.h

- Soubor MMIOChainer.h (viz [úplný kód)](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)obsahuje definici datové struktury a základní třídu, ze které by měla být odvozena třída chainer. Rozhraní .NET Framework 4.5 rozšiřuje datovou strukturu MMIO tak, aby zpracovávala data, která instalační program rozhraní .NET Framework 4.5 potřebuje. Změny struktury MMIO jsou zpětně kompatibilní, takže řetězeři rozhraní .NET Framework 4 mohou pracovat s nastavením rozhraní .NET Framework 4.5 bez nutnosti rekompilace. Tento scénář však nepodporuje funkci pro snížení restartování systému.

    Pole verze poskytuje způsob identifikace revizí struktury a formátu zprávy. Nastavení rozhraní .NET Framework určuje verzi rozhraní chainer `VirtualQuery` voláním funkce k určení velikosti mapování souborů. Pokud je velikost dostatečně velká, aby se přizpůsobila poli verze, použije nastavení rozhraní .NET Framework zadanou hodnotu. Pokud je mapování souborů příliš malé na to, aby obsahovalo pole verze, což je případ rozhraní .NET Framework 4, proces instalace předpokládá verzi 0 (4). Pokud chainer nepodporuje verzi zprávy, kterou chce odeslat instalační program rozhraní .NET Framework, předpokládá nastavení rozhraní .NET Framework odpověď na ignorování.

    Datová struktura MMIO je definována takto:

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

- Datová struktura by neměla `MmioDataStructure` být používána přímo; použijte `MmioChainer` třídu místo toho k implementaci chainer. Odvodit z třídy `MmioChainer` zřetězit rozhraní .NET Framework 4.5 redistributable.

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- Soubor IProgressObserver.h implementuje pozorovatele průběhu[(viz úplný kód).](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592) Tento pozorovatel získá oznámení o průběhu stahování a `char`instalace (zadáno jako nepodepsané , 0-255, označující 1%-100% dokončení). Pozorovatel je také upozorněn, když chainee odešle zprávu a pozorovatel by měl odeslat odpověď.

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>Řetězové dotNet4.5.cpp

- [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) soubor implementuje třídu, `Server` která `MmioChainer` je odvozena z třídy a přepíše příslušné metody pro zobrazení informací o průběhu. MmioChainer vytvoří oddíl se zadaným názvem oddílu a inicializuje chainer se zadaným názvem události. Název události je uložen v namapované datové struktuře. Názvy oddílů a událostí byste měli udělat jedinečnými. Třída `Server` v následujícím kódu spustí zadaný instalační program, sleduje jeho průběh a vrací ukončovací kód.

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    Instalace je spuštěna metodou Main.

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

- Před spuštěním instalace chainer zkontroluje, zda je rozhraní .NET Framework `IsNetFx4Present`4.5 již nainstalováno voláním :

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

- Můžete změnit cestu spustitelného souboru (Setup.exe v `Launch` příkladu) v metodě přejděte na jeho správné umístění nebo přizpůsobit kód k určení umístění. Základní `MmioChainer` třída poskytuje `Run()` metodu blokování, kterou volá odvozená třída.

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

- Metoda `Send` zachycuje a zpracovává zprávy. V této verzi rozhraní .NET Framework je jedinou podporovanou zprávou zpráva o zavření aplikace.

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

- Údaje o průběhu `char` jsou nepodepsané mezi 0 (0 %) a 255 (100 %).

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT je předán `Finished` metodě.

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > Redistribuovatelné rozhraní .NET Framework 4.5 obvykle zapisuje mnoho zpráv o průběhu a jednu zprávu, která označuje dokončení (na straně chainer). Také čte asynchronně, hledá `Abort` záznamy. Pokud obdrží `Abort` záznam, zruší instalaci a zapíše dokončený záznam s E_ABORT jako jeho data po instalaci byla přerušena a operace instalace byly vráceny zpět.

Typický server vytvoří náhodný název souboru MMIO, vytvoří soubor (jak `Server::CreateSection`je znázorněno v předchozím příkladu `CreateProcess` kódu v ) a `-pipe someFileSectionName` spustí redistribuovatelné pomocí metody a předáním názvu kanálu s možností. Server by `OnProgress`měl `Send`implementovat , a `Finished` metody s kódem specifické pro použití aplikace.

## <a name="see-also"></a>Viz také

- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Nasazení](index.md)
