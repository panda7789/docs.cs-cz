---
title: 'Postupy: Povolení trasování WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971507"
---
# <a name="how-to-enable-wif-tracing"></a>Postupy: Povolení trasování WIF

## <a name="applies-to"></a>Platí pro

- Microsoft® Windows® Identity Foundation (WIF)

- Webové formuláře ASP.NET®

## <a name="summary"></a>Souhrn

V tomto postupu najdete podrobné postupy pro povolení WIF trasování v aplikaci ASP.NET. Poskytuje také pokyny pro testování aplikace za účelem ověření, že naslouchací proces trasování a protokol fungují správně. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Dá se stáhnout z následujícího umístění: [Nástroj identity and Access](https://go.microsoft.com/fwlink/?LinkID=245849)

> [!IMPORTANT]
> Povolení trasování WIF pro pasivní aplikace, tedy aplikací, které používají protokol WS-Federation, může potenciálně vystavit aplikaci útokům DOS (Denial of Service) nebo vyzrazení informací pro osobu, která je škodlivá. Zahrnuje to pasivní RPs i pasivní STSes. Z tohoto důvodu doporučujeme, abyste nepovolili trasování WIF pro pasivní RPs nebo STSes v produkčním prostředí.

## <a name="contents"></a>Obsah

- Cíle

- Přehled

- Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování

- Krok 2 – testování řešení

## <a name="objectives"></a>Cíle

- Vytvoření jednoduché aplikace ASP.NET, která používá WIF a vývoj STS z nástroje Identity and Access Tool

- Povolit trasování a ověřit, zda funguje

## <a name="overview"></a>Přehled

Trasování vám umožní ladit a řešit potíže s mnoha typy problémů s WIF, včetně tokenů, souborů cookie, deklarací, zpráv protokolu a dalších. Trasování WIF se podobá trasování WCF; Můžete například vybrat podrobnosti trasování a Zobrazit vše z kritických zpráv ve všech zprávách. Trasování WIF je možné vygenerovat v souborech **. XML** nebo v souborech **. svclog** , které lze zobrazit pomocí nástroje pro prohlížeč trasování služby. Tento nástroj se nachází v adresáři **bin** instalační cesty Windows SDK na počítači, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.

## <a name="summary-of-steps"></a>Přehled kroků

- Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování

- Krok 2 – testování řešení

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 – Vytvoření jednoduché aplikace webových formulářů ASP.NET a povolení trasování

V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravíte soubor *Web. config* , aby bylo možné trasování povolit.

### <a name="to-create-a-simple-aspnet-application"></a>Vytvoření jednoduché aplikace ASP.NET

1. Spusťte Visual Studio a klikněte na **soubor**, **Nový**a pak na **projekt**.

2. V okně **Nový projekt** klikněte na **ASP.NET webová Formulářová aplikace**.

3. Do **název**zadejte `TestApp` a stiskněte **OK**.

4. V části **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TestApp** a pak vyberte **Identita a přístup**.

5. Zobrazí se okno **Identita a přístup** . Včásti poskytovatelé vyberte **test aplikace pomocí místní služby tokenů pro vývoj**a pak klikněte na **použít**.

6. V kořenovém adresáři jednotky **C:** vytvořte novou složku s názvem **logs** : **C:\Logs.**

7. Přidejte následující  **\<> element System. Diagnostics** do konfiguračního souboru *Web. config* hned za element > ukončení  **\</configSections** , jak je znázorněno níže:

    ```xml
    <configuration>
        <configSections>
            ...
        </configSections>
        <system.diagnostics>
            <sources>
                <source name="System.IdentityModel" switchValue="Verbose">
                    <listeners>
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />
                    </listeners>
                </source>
            </sources>
            <trace autoflush="true" />
        </system.diagnostics>
    ```

    > [!NOTE]
    > Předtím, než může protokolování začít, musí existovat umístění adresáře zadané v atributu **initializeData** . Pokud umístění neexistuje, nebudou vytvořeny žádné protokoly.

     Výše uvedené nastavení konfigurace umožní **podrobné** trasování pro WIF a uložení výsledného protokolu do souboru **C:logsWIF.XML** .

## <a name="step-2--test-your-solution"></a>Krok 2 – testování řešení

V tomto kroku otestujete svou ASP.NET aplikaci s podporou WIF, abyste ověřili, že jsou protokoly zaznamenávány.

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Testování aplikace ASP.NET s povoleným WIF pro úspěšné trasování

1. Spusťte řešení stisknutím klávesy **F5** . Měli byste se dodávat s výchozí domovskou stránkou ASP.NET a automaticky se ověřit s uživatelským jménem *Terry*, což je výchozí uživatel, který je vrácený službou Development STS.

2. Zavřete okno prohlížeče a potom přejděte do složky **c:\Logs.** . Otevřete soubor **C:\logs\WIF.XML** pomocí textového editoru.

3. Zkontrolujte soubor **WIF. XML** a ověřte, zda obsahuje položky začínající  **\<na E2ETraceEvent >** . Tato trasování budou obsahovat  **\<prvky TraceRecord >** s popisy pro sledovanou aktivitu, jako je například **ověření tokenu SecurityToken**.
