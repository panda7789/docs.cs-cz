---
title: 'Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: 604ebf5ad71197f6614ffa45b6d7c181d474e1aa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990484"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Postupy: Ladění aplikací a služeb pracujících s deklaracemi s trasováním WIF
## <a name="applies-to"></a>Platí pro  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Prohlížeč trasování služeb (SvcTraceViewer.exe)  
  
- Řešení potíží a ladění aplikací WIF  
  
## <a name="summary"></a>Souhrn  
 Tento postup popisuje nezbytné kroky, jak nakonfigurovat trasování WIF, shromažďovat protokoly trasování a analyzovat protokoly trasování pomocí nástroje Trace Viewer. Poskytuje obecné mapování pro položky trasování k akcím, které jsou potřeba k řešení problémů souvisejících s WIF.  
  
## <a name="contents"></a>Obsah  
  
- Cíle  
  
- Přehled kroků  
  
- Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config  
  
- Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer  
  
- Krok 3 – určení řešení pro opravu problémů spojených s WIF  
  
- Související položky  
  
## <a name="objectives"></a>Cíle  
  
- Nakonfigurujte trasování WIF.  
  
- Zobrazit protokoly trasování v nástroji Prohlížeč trasování.  
  
- Identifikujte problémy související s WIF v protokolech trasování.  
  
- Použijte opravné akce, které WIF související problémy nalezené v protokolech trasování.  
  
## <a name="summary-of-steps"></a>Přehled kroků  
  
- Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config  
  
- Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer  
  
- Krok 3 – určení řešení pro opravu problémů spojených s WIF  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Krok 1 – Konfigurace trasování WIF pomocí konfiguračního souboru Web. config  
 V tomto kroku přidáte změny do konfiguračních oddílů v souboru *Web. config* , které umožní WIF trasování událostí a jejich uložení do protokolu trasování.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Konfigurace trasování WIF pomocí konfiguračního souboru Web. config  
  
1. Otevřete kořenový konfigurační soubor **Web. config** nebo **App. config** v editoru sady Visual Studio tak, že na něj dvakrát kliknete v **Průzkumník řešení**. Pokud vaše řešení neobsahuje konfigurační soubor **Web. config** nebo **App. config** , přidejte jej kliknutím pravým tlačítkem na řešení v **Průzkumník řešení** a kliknutím na tlačítko **Přidat**a kliknutím na položku **Nová položka...** . V dialogovém okně **Nová položka** vyberte v **seznamu konfigurační soubor aplikace** pro soubor **App. config** nebo **webový konfigurační soubor** pro **Web. config** a klikněte na tlačítko **OK**.  
  
2. Do konfiguračního souboru  **\<v uzlu Konfigurace >** na konci konfiguračního souboru přidejte položky konfigurace podobné následujícímu:  
  
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
  
3. Výše uvedená konfigurace instruuje WIF k vygenerování podrobných událostí trasování a jejich protokolování do souboru *WIFTrace. e2e* . Úplný seznam hodnot pro přepínač **určit atributy switchValue** najdete v tabulce úrovně trasování, kterou najdete v následujícím tématu: [Konfigurace trasování](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Krok 2 – analýza trasovacích souborů WIF pomocí nástroje Trace Viewer  
 V tomto kroku použijete nástroj Prohlížeč trasování (SvcTraceViewer. exe) k analýze protokolů trasování WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Analýza protokolů trasování WIF pomocí nástroje Trace Viewer (SvcTraceViewer. exe)  
  
1. Nástroj Prohlížeč trasování (SvcTraceViewer. exe) se dodává jako součást Windows SDK. Pokud jste ještě Windows SDK nenainstalovali, můžete si ho stáhnout tady: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2. Spusťte nástroj Prohlížeč trasování (SvcTraceViewer. exe). Obvykle je k dispozici ve složce **bin** instalační cesty.  
  
3. Otevřete soubor protokolu trasování WIF, například WIFTrace. e2e tak, že vyberete **soubor**, **otevřete...** v nabídce nebo pomocí klávesové zkratky **CTRL + O** . Soubor protokolu trasování se otevře v nástroji Prohlížeč trasování.  
  
4. Zkontrolujte položky na kartě **aktivita** . Každá položka by měla obsahovat číslo aktivity, počet zaznamenaných trasování, dobu trvání aktivity a její počáteční a koncové časové razítko.  
  
5. Klikněte na kartu **aktivita** . V hlavní oblasti nástroje by se měly zobrazit podrobné položky trasování. Pomocí rozevíracího seznamu **úrovně** v nabídce můžete filtrovat konkrétní úroveň trasování, například: **Vše**, **Upozornění**, **chyby**, **informace**atd.  
  
6. Klikněte na konkrétní položky trasování a zkontrolujte podrobnosti v dolní oblasti nástroje. Podrobnosti lze zobrazit pomocí **formátovaného** a **XML** zobrazení výběrem odpovídajících karet.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Krok 3 – určení řešení pro opravu problémů spojených s WIF  
 V tomto kroku můžete identifikovat řešení potíží souvisejících s WIF, které jsou identifikované pomocí protokolu trasování WIF a nástroje Trace Viewer. Popisuje obecné mapování WIF souvisejících s výjimkami na potenciální řešení nebo požadované akce pro řešení tohoto problému.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>Určení řešení pro opravu problémů souvisejících s WIF  
  
1. Projděte si následující tabulku výjimek WIF a požadované akce Opravte problémy.  
  
|**ID chyby**|**Chybová zpráva**|**Akce nutná k opravě chyby**|  
|-|-|-|  
|ID4175|Vystavitel tokenu zabezpečení nebyl rozpoznán pomocí IssuerNameRegistry.  Pokud chcete z tohoto vystavitele přijímat tokeny zabezpečení, nakonfigurujte IssuerNameRegistry tak, aby vracel platný název tohoto vystavitele.|Tato chyba může být způsobena zkopírováním kryptografického otisku z modulu snap-in konzoly MMC a vložením do souboru *Web. config* . Konkrétně můžete v textovém řetězci při kopírování z okna vlastností certifikátu získat další netisknutelný znak. Tento znak navíc způsobí selhání porovnávání kryptografických otisků. Postup pro správné kopírování kryptografického otisku se dá najít v [jednotném přihlašování založeném na deklaracích webu a Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).|  
  
## <a name="related-items"></a>Související položky  
  
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
