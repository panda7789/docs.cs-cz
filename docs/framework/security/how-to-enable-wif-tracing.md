---
title: 'Postupy: Povolení trasování WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: ab59b0809008f212269e2c4b9745ccaec8c9af5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605159"
---
# <a name="how-to-enable-wif-tracing"></a>Postupy: Povolení trasování WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento návod obsahuje podrobné podrobné postupy pro povolení trasování WIF aplikace technologie ASP.NET. Také poskytuje pokyny k testování aplikace pro ověření, že naslouchací proces trasování a protokol fungují správně. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Můžete ho stáhnout z následujícího umístění: [Nástroj identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Povolení trasování WIF u pasivních aplikací, to znamená, aplikace používající protokol WS-Federation, může potenciálně aplikaci vystavit útoky na dostupnost služby (DoS) a zpřístupnění informací škodlivý straně. To zahrnuje pasivní RPs a pasivní STSes. Z tohoto důvodu doporučujeme není povolit trasování WIF pro pasivní RPs nebo STSes v produkčním prostředí.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování  
  
-   Krok 2 – otestování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Vytvořit jednoduchou aplikaci ASP.NET, která používá technologie WIF a služba STS pro vývoj od Identity and Access Tool  
  
-   Povolení trasování a ověřte, že je funkční  
  
## <a name="overview"></a>Přehled  
 Trasování umožňuje ladění a řešení potíží s mnoha typy problémů pomocí technologie WIF, včetně tokeny, soubory cookie, deklarace identity, zprávách protokolů a dalších. Trasování WIF je podobný trasování WCF; Například můžete nastavit úroveň podrobností trasování vše od kritické zprávy zobrazíte všechny zprávy. Technologie WIF trasování mohou být generovány v **.xml** soubory nebo v **.svclog** soubory, které je možné zobrazit pomocí nástroje prohlížeče trasování služeb. Tento nástroj se nachází v **bin** adresář sady Windows SDK cesta pro instalaci na počítač, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování  
  
-   Krok 2 – otestování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 – Vytvoření aplikace jednoduché rozhraní ASP.NET Web Forms a povolení trasování  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru trasování.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spusťte sadu Visual Studio a klikněte na tlačítko **souboru**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okna, klikněte na tlačítko **aplikace webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Klikněte pravým tlačítkem myši **TestApp** projektu v rámci **Průzkumníku řešení**a pak vyberte **identit a přístupu**.  
  
5.  **Identit a přístupu** zobrazí se okno. V části **poskytovatelé**vyberte **testování aplikace s místní službu STS pro vývoj**, pak klikněte na tlačítko **použít**.  
  
6.  Vytvořte novou složku s názvem v **protokoly** v kořenovém adresáři **C:** jednotky, jako je třeba zobrazí: **C:\Logs**  
  
7.  Přidejte následující  **\<system.diagnostics >** elementu *Web.config* konfigurační soubor hned za uzavírací  **\</configSections >** element, jako je třeba zobrazí:  
  
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
    >  Zadaný v umístění adresáře **initializeData** atribut musí existovat předtím, než můžete začít protokolování. Pokud umístění ještě neexistuje, vytvoří se žádné protokoly.  
  
     Výše uvedených nastavení konfigurace se umožní **Verbose** trasování pro technologie WIF a výsledné protokol **C:logsWIF.xml** souboru.  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – otestování řešení  
 V tomto kroku otestujete aplikaci technologie ASP.NET s podporou technologie WIF ověření, že jsou zaznamenávány protokoly.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Chcete-li otestovat aplikaci technologie ASP.NET s podporou technologie WIF pro úspěšné trasování  
  
1.  Spuštění řešení stisknutím kombinace kláves **F5** klíč. Měli byste se výchozí domovskou stránku ASP.NET a automaticky ověřuje se uživatelské jméno *Terry*, což je výchozí uživatel, který je vrácen služba STS pro vývoj.  
  
2.  Zavřete okno prohlížeče a přejděte **C:\logs** složky. Otevřít **C:\logs\WIF.xml** soubor pomocí textového editoru.  
  
3.  Zkontrolujte **WIF.xml** souboru a ověřte, zda obsahuje položky počínaje  **\<E2ETraceEvent >**. Toto trasování bude obsahovat  **\<TraceRecord >** prvky s popisem trasovaných aktivity, jako například **ověření tokenu SecurityToken**.
