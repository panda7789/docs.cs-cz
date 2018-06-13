---
title: 'Postupy: Povolení WIF trasování'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 459d74f3faf9fab4cba047a87ccff77d193e9026
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399545"
---
# <a name="how-to-enable-wif-tracing"></a>Postupy: Povolení WIF trasování
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® webových formulářů  
  
## <a name="summary"></a>Souhrn  
 Tento postup obsahuje podrobné podrobné postupy pro povolení trasování WIF v aplikaci ASP.NET. Také poskytuje pokyny testování aplikace ověřit, jestli naslouchací proces trasování a protokol jsou správně funguje. Tento návod neobsahuje podrobné pokyny pro vytvoření služby tokenů zabezpečení (STS) a namísto toho používá službu STS určenou pro vývoj, která je součástí instalace nástroje Identity and Access Tool. Služba STS pro vývoj neprovádí skutečné ověřování a je určena pouze pro testovací účely. Abyste mohli dokončit postupy v tomto návodu, je třeba nainstalovat nástroj Identity and Access Tool. Ho můžete stáhnout z následujícího umístění: [identita a přístup](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Povolení trasování WIF u pasivních aplikací, to znamená, aplikace, které používají protokol WS-Federation, mohou potenciálně odhalit aplikaci útoků DoS (DoS) a zpřístupnění informací škodlivý strany. To zahrnuje pasivní RPs a pasivní STSes. Z tohoto důvodu doporučujeme není povolit WIF trasování pro pasivní RPs nebo STSes v produkčním prostředí.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled  
  
-   Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování  
  
-   Krok 2 – testování řešení  
  
## <a name="objectives"></a>Cíle  
  
-   Vytvořit jednoduchou aplikaci ASP.NET, která používá WIF a vývoj služby tokenů zabezpečení z Identity a přístup  
  
-   Povolení trasování a ověřte, zda je funkční  
  
## <a name="overview"></a>Přehled  
 Trasování umožňuje ladění a odstraňování potíží mnoho typů problémů s WIF, včetně tokeny, soubory cookie, deklarace identity, zprávy protokolu a další. WIF trasování je podobné trasování WCF; Například můžete podrobností trasování do všechno kritické zprávy zobrazit všechny zprávy. WIF trasování může být generována v **.xml** soubory nebo v **.svclog** soubory, které je možné zobrazit pomocí nástroje pro prohlížeč trasování služby. Tento nástroj se nachází v **bin** directory sady Windows SDK instalační cesty v počítači, například: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování  
  
-   Krok 2 – testování řešení  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Krok 1 – Vytvoření jednoduché rozhraní ASP.NET Web Forms aplikace a povolení trasování  
 V tomto kroku vytvoříte novou aplikaci webových formulářů ASP.NET a upravit *Web.config* souboru povolení trasování.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Chcete-li vytvořit jednoduchou aplikaci ASP.NET  
  
1.  Spuštění sady Visual Studio a klikněte na tlačítko **soubor**, **nový**a potom **projektu**.  
  
2.  V **nový projekt** okně klikněte na tlačítko **aplikaci webových formulářů ASP.NET**.  
  
3.  V **název**, zadejte `TestApp` a stiskněte klávesu **OK**.  
  
4.  Klikněte pravým tlačítkem myši **TestApp** projektu v části **Průzkumníku řešení**, pak vyberte **identit a přístupu**.  
  
5.  **Identit a přístupu** se zobrazí v okně. V části **zprostředkovatelé**, vyberte **testování vaší aplikace pomocí místní služby tokenů zabezpečení vývoj**, pak klikněte na tlačítko **použít**.  
  
6.  Vytvořte novou složku s názvem v **protokoly** v kořenovém **C:** jednotky, jako je třeba vidět: **C:\logs**  
  
7.  Přidejte následující  **\<system.diagnostics >** elementu, který chcete *Web.config* konfigurační soubor okamžitě po zavření  **\</configSections >** element, jako je třeba zobrazí:  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
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
    >  Zadaný v umístění adresáře **initializeData –** atributu musí existovat, než můžete začít protokolování. Pokud umístění neexistuje, vytvoří se žádné protokoly.  
  
     Povolí výše uvedených nastavení konfigurace **podrobné** trasování pro WIF a výsledný protokolu, který chcete uložit **C:logsWIF.xml** souboru.  
  
## <a name="step-2--test-your-solution"></a>Krok 2 – testování řešení  
 V tomto kroku budete testovat aplikace ASP.NET WIF povoleno ověření, že se mají zaznamenávat protokoly.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>K testování aplikace WIF technologie ASP.NET pro úspěšné trasování  
  
1.  Spuštění řešení stisknutím **F5** klíč. Můžete by měl mít výchozí domovskou stránku ASP.NET a automaticky k ověření pomocí uživatelského jména *Terry*, což je výchozí uživatel, který je vrácena službou tokenů zabezpečení vývoj.  
  
2.  Zavřete okno prohlížeče a pak přejděte do **C:\logs** složky. Otevřete **C:\logs\WIF.xml** souboru pomocí textového editoru.  
  
3.  Zkontrolujte **WIF.xml** souboru a ověřte, zda obsahuje položky počínaje  **\<E2ETraceEvent >**. Bude obsahovat toto trasování  **\<TraceRecord >** elementů s popisy trasovaná aktivity, jako například **ověřování SecurityToken**.
