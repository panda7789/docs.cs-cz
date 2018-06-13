---
title: 'Postupy: Ladění deklaracemi identity aplikace a služby pomocí WIF trasování'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0f2126a83e6a5638eb492bb2a529dbf4cdab1714
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408629"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Postupy: Ladění deklaracemi identity aplikace a služby pomocí WIF trasování
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Prohlížeč trasování služeb (SvcTraceViewer.exe)  
  
-   Řešení potíží a ladění aplikací WIF  
  
## <a name="summary"></a>Souhrn  
 Tento postup popisuje požadované kroky, jak nakonfigurovat WIF trasování, shromážděte protokoly trasování a jak analyzovat trasování protokoly, pomocí nástroje prohlížeče trasování. Poskytuje obecné mapování pro trasování položky na akce, které jsou potřebné k řešení potíží s WIF.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor  
  
-   Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování  
  
-   Krok 3 – lze vyřešit WIF identifikovat problémy související s  
  
-   Související položky  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurovat WIF trasování.  
  
-   V nástroji Prohlížeč trasování protokolů trasování zobrazení.  
  
-   Identifikovat WIF související s problémy v protokolech trasování.  
  
-   Použít opravné akce WIF problémům najít v protokolech trasování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor  
  
-   Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování  
  
-   Krok 3 – lze vyřešit WIF identifikovat problémy související s  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1 – konfigurace WIF trasování pomocí Web.config – konfigurační soubor  
 V tomto kroku přidáte změny konfigurační oddíly funkce v *Web.config* soubor, který povolit WIF sledovat události a uložit je do protokolu trasování.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Konfigurace trasování WIF pomocí konfiguračního souboru Web.config  
  
1.  Otevřete kořenu **Web.config** nebo **App.config** konfiguračního souboru v editoru Visual Studio poklepáním na na něm v **Průzkumníku řešení**. Pokud vaše řešení nemá **Web.config** nebo **App.config** konfigurační soubor, přidejte kliknutím pravým tlačítkem na řešení v **Průzkumníku řešení** a kliknutím na  **Přidat**, pak levým na **novou položku...** . Na **nová položka** vyberte **konfigurační soubor aplikace** pro **App.config** nebo **soubor webové konfigurace** pro **Web.config** ze seznamu a klikněte na tlačítko **OK**.  
  
2.  Přidejte konfigurační položky podobné následujícím do konfiguračního souboru uvnitř  **\<konfigurace >** uzlu na konci tohoto konfiguračního souboru:  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  Výše uvedené konfigurace dá pokyn WIF generovat události podrobného trasování a protokolování do *WIFTrace.e2e* souboru. Úplný seznam hodnot pro **switchValue** přepnout, naleznete v tabulce Úroveň trasování najít v následujícím tématu: [Konfigurace trasování](http://msdn.microsoft.com/library/ms733025.aspx).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2 – analyzovat WIF trasovací soubory pomocí nástroje prohlížeče trasování  
 V tomto kroku použijete nástroj Prohlížeč trasování (SvcTraceViewer.exe) k analýze protokolů trasování WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>K analýze protokolů trasování WIF pomocí nástroje prohlížeče trasování (SvcTraceViewer.exe)  
  
1.  Nástroj Prohlížeč trasování (SvcTraceViewer.exe) dodává jako součást sady Windows SDK. Pokud jste ještě nenainstalovali Windows SDK, můžete stáhnout tady: [Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  Spusťte nástroj Prohlížeč trasování (SvcTraceViewer.exe). Je obvykle dostupné v **Bin** složky cesty instalace.  
  
3.  Otevřete soubor protokolu WIF trasování, například WIFTrace.e2e výběrem **soubor**, **otevřete...** možnost v nabídce nebo pomocí **Ctrl + O** zástupce. Otevře se v nástroji Prohlížeč trasování soubor protokolu trasování.  
  
4.  Zkontrolujte položky v **aktivity** kartě. Každý záznam by měl obsahovat číslo aktivity, počet trasování, které byly zaznamenány do protokolu, doba trvání aktivity a jeho počáteční a koncové časová razítka.  
  
5.  Klikněte na **aktivity** kartě. Měli byste vidět podrobné trasování položky v oblasti hlavní nástroje. Použití **úroveň** rozevíracího seznamu v nabídce filtrovat konkrétní úroveň trasování, například: **všechny**, **upozornění**, **chyby**, **Informace**atd.  
  
6.  Kliknutím na konkrétní trasování záznamy pro podrobné informace v oblasti nižší nástroje. Podrobnosti lze zobrazit pomocí **formátu** a **XML** zobrazení tak, že zvolíte odpovídající karty.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3 – lze vyřešit WIF identifikovat problémy související s  
 V tomto kroku můžete identifikovat řešení s WIF problémy identifikovat pomocí protokolu trasování WIF a nástroj prohlížeče trasování. Popisuje obecné mapování WIF související výjimky možná řešení nebo požadované akce k odstranění problému.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>K identifikaci lze vyřešit WIF problémy související s  
  
1.  Přečtěte si následující tabulku WIF výjimky a požadované akce k opravě problémů.  
  
|**ID chyby**|**Chybová zpráva**|**Akce potřebné opravy chyby**|  
|-|-|-|  
|ID4175|Vystavitel tokenu zabezpečení nebyl rozpoznán IssuerNameRegistry.  Pokud chcete přijímat tokeny zabezpečení z vystaviteli, nakonfigurujte IssuerNameRegistry vrátit platný název pro tento vystavitele.|Tato chyba může být způsobeno kopírování kryptografický otisk z modulu snap-in konzoly MMC a vložíte ji do *Web.config* souboru. Konkrétně můžete získat velmi netisknutelný znak v textovém řetězci při kopírování v okně Vlastnosti certifikátu. Tento další znak způsobí selhání porovnávání kryptografický otisk. Postup pro správně kopírování kryptografický otisk naleznete zde: [http://msdn.microsoft.com/library/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)|  
  
## <a name="related-items"></a>Související položky  
  
-   [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](http://msdn.microsoft.com/library/aa751795.aspx)
