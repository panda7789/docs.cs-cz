---
title: Ukázka zabezpečení zjišťování
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: e956b9f8162d55891233a3ab664b05658d50eeab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772997"
---
# <a name="discovery-security-sample"></a>Ukázka zabezpečení zjišťování
Specifikace zjišťování nevyžaduje, zabezpečené koncové body, které jsou součástí procesu zjišťování. Rozšíření zjišťování zpráv pomocí zabezpečení zmírní různé typy útoků (zpráva změnou, útok DOS, znovu přehrát, falšování identity). Tato ukázka implementuje vlastní kanály, které compute a ověřování podpisů zprávu ve formátu compact podpis (popsaný v části 8.2 specifikace WS-Discovery). Ukázka podporuje i [2005 zjišťování specifikace](https://go.microsoft.com/fwlink/?LinkId=177912) a [verze 1.1](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Vlastní kanál se použije nad rámec zásobníku existující kanál pro koncové body pro zjišťování a oznámení. Podpis záhlaví tímto způsobem, platí pro všechny zprávy odeslané. Podpis se neověřuje na přijaté zprávy a když neodpovídá nebo zprávy podpisy nejsou, se zahodí zprávy. Ukázka používá k podepisování a ověření zprávy, certifikáty.  
  
## <a name="discussion"></a>Diskuse  
 WCF je velmi rozšiřitelný a umožňuje uživatelům možnost přizpůsobit kanálů podle potřeby. Ukázka implementuje element bezpečnou vazbu a zjišťování, který vytváří zabezpečené kanály. Zabezpečené kanály použít a ověřit podpisy zpráv a se použije nad rámec aktuálního zásobníku.  
  
 Element vazby zabezpečení sestavení objekty pro vytváření zabezpečeného kanálu a moduly pro naslouchání kanálů.  
  
## <a name="secure-channel-factory"></a>Objekt pro vytváření zabezpečeného kanálu  
 Objekt pro vytváření zabezpečeného kanálu vytvoří výstup nebo duplexní kanály, které aplikacím dodávají compact podpis záhlaví zpráv. Zpráv pro zachování co nejmenší compact podpis formátu se používá. V následujícím příkladu se zobrazí strukturu compact podpis.  
  
```xml  
<d:Security ... >   
  [<d:Sig Scheme="xs:anyURI"   
         [KeyId="xs:base64Binary"]?  
          Refs="..."  
         [PrefixList]="xs:NMTOKENS"   
          Sig="xs:base64Binary"   
          ... />]?  
  ...   
</d:Security>  
```  
  
> [!NOTE]
>  `PrefixList` Se přidal ve verzi protokolu zjišťování 2008.  
  
 Vypočítat podpis, určuje ukázku rozšířené podpis položky. Podpis XML (`SignedInfo`) je vytvořený pomocí `ds` předponu oboru názvů, podle potřeb specifikaci WS-Discovery. Text a všechny hlavičky v zjišťování a adresování obory názvů jsou odkazovány v signatuře, aby nemohlo být manipulováno s. Každý prvek je transformovat pomocí exkluzivní převodu do kanonického tvaru (http://www.w3.org/2001/10/xml-exc-c14n# ), a pak je vypočítán hodnotu hodnotou hash SHA-1 (http://www.w3.org/2000/09/xmldsig#sha1 ). Na základě všechny odkazované elementy a jejich hodnoty ověřování algoritmem digest, hodnota podpisu je vypočítán s použitím algoritmu RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 Zprávy jsou podepsané certifikátem zadaného klienta. Umístění úložiště, název a název subjektu certifikátu musí zadat při vytváření elementu vazby. `KeyId` Compact podpis představuje identifikátor klíče podpisu tokenu a je předmět klíč identifikátor (identifikátor klíče subjektu) podpisového tokenu nebo (Pokud identifikátor klíče subjektu neexistuje) hodnotu hash SHA-1 podpisového tokenu veřejného klíče.  
  
## <a name="secure-channel-listener"></a>Modul pro naslouchání kanálu zabezpečení  
 Modul pro naslouchání kanálu zabezpečení vytváří vstupní nebo duplexní kanály, které ověřují compact podpis v přijaté zprávy. Ověření podpisu, `KeyId` podle zkomprimovat podpisu připojeného ke zprávě se používá k výběru certifikátu z určeného úložiště. Pokud zpráva nemá podpis nebo kontrolu podpisu selže, se zahodí zprávy. Použít zabezpečené vazby, ukázka definuje objekt factory, který vytvoří vlastní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> s elementem přidání zjišťování zabezpečené vazby. Naslouchací procesy oznámení zjišťování a zjistitelné služby je možné tyto zabezpečené koncové body.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázka zahrnuje knihovny a 4 konzolové aplikace:  
  
- **DiscoverySecurityChannels**: Knihovna, která poskytuje zabezpečené vazby. Knihovny vypočítá a ověří podpis compact odchozích/příchozích zpráv.  
  
- **Služba**: Služba zveřejňující ICalculatorService smlouvy, vlastní hostované. Služba je označena jako zjistitelné. Uživatel zadá podrobnosti certifikátu použitého k podepsání zprávy tak, že zadáte umístění úložiště a název a název subjektu nebo jiný jedinečný identifikátor pro tento certifikát a úložiště, kde jsou klientské certifikáty nachází (certifikátů používaných pro Kontrola podpisu pro příchozí zprávy). Na základě těchto podrobností, je UdpDiscoveryEndpoint s vyššího zabezpečení vytvořené a použít.  
  
- **Klient**: Tato třída se pokusí zjistit ICalculatorService a volat metody ve službě. Znovu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> s přidali zabezpečení je integrované a používá k podepsání a ověřte, zprávy.  
  
- **AnnouncementListener**: V místním prostředí služby, který naslouchá oznámení týkající se online i offline a používá koncový bod zabezpečené oznámení.  
  
> [!NOTE]
>  Pokud Setup.bat spustí více než jednou, správce certifikátů zobrazí výzvu pro výběr certifikátu, který chcete přidat, protože existují duplicitní certifikáty. V takovém případě by měl být přerušen Setup.bat a Cleanup.bat by měla být volána, protože tyto duplikáty již byly vytvořeny. CleanUp.bat také výzva k výběru certifikát k odstranění. Vyberte certifikát ze seznamu a pokračovat v provádění Cleanup.bat, dokud nezbývají žádné certifikáty.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1. Spusťte skript Setup.bat na příkazovém řádku pro vývojáře pro sadu Visual Studio. Ukázka používá certifikáty pro podepsání a ověření zprávy. Tento skript vytvoří certifikát pomocí Makecert.exe a nainstaluje je pomocí Certmgr.exe. Skript musí být spuštěn s oprávněním správce.  
  
2. Sestavte a spusťte ukázku, otevřete soubor Security.sln v sadě Visual Studio a zvolte **sestavit vše znovu**. Aktualizovat vlastnosti řešení, které chcete spustit více projektů: vyberte **Start** pro všechny projekty s výjimkou DiscoverySecureChannels. Normální spuštění řešení.  
  
3. Jakmile budete hotovi s ukázkou, spusťte Cleanup.bat skript, který odstraní certifikáty vytvořené pro tuto ukázku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
