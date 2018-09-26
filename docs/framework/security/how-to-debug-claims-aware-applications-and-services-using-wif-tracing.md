---
title: 'Postupy: Ladění s deklaracemi identity aplikace a služby pomocí trasování WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: e10d8d2ea869b03586b4680ad8320aeb2de90620
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088123"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Postupy: Ladění s deklaracemi identity aplikace a služby pomocí trasování WIF
## <a name="applies-to"></a>Platí pro  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Prohlížeč trasování služeb (SvcTraceViewer.exe)  
  
-   Řešení potíží a ladění aplikací technologie WIF  
  
## <a name="summary"></a>Souhrn  
 Tento postup popisuje kroky pro postup konfigurace trasování WIF, shromažďovat protokoly trasování a protokoly jak analyzovat trasování pomocí nástroje prohlížeče trasování. Poskytuje obecné mapování trasování položky pro akce potřebné k řešení problémů souvisejících s technologie WIF.  
  
## <a name="contents"></a>Obsah  
  
-   Cíle  
  
-   Přehled kroků  
  
-   Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config  
  
-   Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování  
  
-   Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s  
  
-   Související položky  
  
## <a name="objectives"></a>Cíle  
  
-   Konfigurace trasování WIF.  
  
-   Protokoly trasování zobrazení v nástroji prohlížeče trasování.  
  
-   Identifikujte technologie WIF související s problémy v protokolech trasování.  
  
-   Použít opravné akce, které technologie WIF a související s problémy zjištěné v protokoly trasování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
-   Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config  
  
-   Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování  
  
-   Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1 – konfigurace technologie WIF trasování pomocí konfiguračního souboru Web.config  
 V tomto kroku přidáte změny do konfigurační oddíly funkce v *Web.config* soubor, který se povolit technologie WIF sledovat jeho události a uložit je do protokolu trasování.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Konfigurace trasování WIF je používán konfigurační soubor Web.config  
  
1.  Otevřít kořenové **Web.config** nebo **App.config** konfiguračním souboru v editoru sady Visual Studio, dvakrát klikněte na něj v **Průzkumníka řešení**. Pokud vaše řešení nemá **Web.config** nebo **App.config** konfigurace přidejte kliknutím pravým tlačítkem na řešení v **Průzkumníka řešení** a kliknete na  **Přidat**, pak levým na **novou položku...** . Na **nová položka** dialogového okna, vyberte **konfiguračního souboru aplikace** pro **App.config** nebo **souboru konfigurace webu** pro **Web.config** ze seznamu a klikněte na tlačítko **OK**.  
  
2.  Přidat položky konfigurace, který je podobný následujícímu do konfiguračního souboru uvnitř  **\<konfigurace >** uzlu na konci konfiguračního souboru:  
  
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
  
3.  V konfiguraci uvedené výš dává pokyn technologie WIF generování událostí na podrobné trasování a protokolování do *WIFTrace.e2e* souboru. Úplný seznam hodnot **switchValue** přepnout, naleznete v tabulce Úroveň trasování v následujícím tématu: [Konfigurace trasování](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2 – analýza souborů trasování WIF pomocí prohlížečem trasování  
 V tomto kroku použijete nástroj prohlížeče trasování (SvcTraceViewer.exe) k analýze protokolů trasování WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>K analýze protokolů trasování WIF pomocí nástroje prohlížeče trasování (SvcTraceViewer.exe)  
  
1.  Prohlížečem trasování (SvcTraceViewer.exe) dodávána jako součást sady Windows SDK. Pokud jste ještě nenainstalovali sady Windows SDK, můžete stáhnout tady: [sady Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2.  Spusťte nástroj prohlížeče trasování (SvcTraceViewer.exe). Je obvykle dostupná **Bin** složce instalační cesta.  
  
3.  Otevřít soubor protokolu technologie WIF trasování, například WIFTrace.e2e tak, že vyberete **souboru**, **otevřít...** Možnosti v nabídce nebo pomocí **Ctrl + O** zástupce. Soubor protokolu trasování se otevře v prohlížeči trasování nástroje.  
  
4.  Zkontrolujte záznamy v **aktivity** kartu. Každý záznam může obsahovat číslo aktivity, počet trasování, které byly zaznamenány, doba trvání aktivity a její spuštění a ukončení časová razítka.  
  
5.  Klikněte na **aktivity** kartu. Měli byste vidět položky podrobné trasování v hlavní oblasti nástroje. Použití **úroveň** rozevíracího seznamu v nabídce filtrovat konkrétní úroveň trasování, například: **všechny**, **upozornění**, **chyby**, **Informace**atd.  
  
6.  Klikněte na položky konkrétní trasování chcete podívat na podrobnosti ve spodní části nástroje. Podrobnosti lze zobrazit pomocí **formátu** a **XML** zobrazení výběrem příslušné karty.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3 – řešení Chcete-li vyřešit technologie WIF identifikovat problémy související s  
 V tomto kroku můžete identifikovat řešení pro související technologie WIF problémů zjištěných pomocí prohlížeče trasování nástroje a technologie WIF protokolu trasování. Popisuje obecné mapování technologie WIF související výjimky z možných řešení nebo požadované akce k odstranění tohoto problému.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>K identifikaci řešení Chcete-li vyřešit technologie WIF problémy související s  
  
1.  Projděte si následující tabulku výjimek technologie WIF a požadovaných akcí, chcete-li opravit problémy.  
  
|**ID chyby**|**Chybová zpráva**|**Akce potřebný k opravě chyby**|  
|-|-|-|  
|ID4175|IssuerNameRegistry nebyl rozpoznán vystavitele tokenu zabezpečení.  Přijímat tokeny zabezpečení od tohoto vydavatele, nakonfigurujte IssuerNameRegistry vrátit platný název pro tento vystavitele.|Tato chyba může být způsobena zkopírováním kryptografický otisk z modulu snap-in konzoly MMC a jeho vložením do *Web.config* souboru. Konkrétně můžete získat další netisknutelné znaky v textovém řetězci při kopírování z okna Vlastnosti certifikátu. Tento znak navíc způsobí, že shoda kryptografický otisk selhání. Postup pro správně kopírování kryptografický otisk najdete tady: [http://msdn.microsoft.com/library/ff359102.aspx](https://msdn.microsoft.com/library/ff359102.aspx)|  
  
## <a name="related-items"></a>Související položky  
  
-   [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
