---
title: Ukázka zabezpečení zjišťování
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: 00f81d1879d9157a7ecdfa0db8d2ea0d505ad5b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183747"
---
# <a name="discovery-security-sample"></a>Ukázka zabezpečení zjišťování

Specifikace zjišťování nevyžaduje, aby koncové body, které se účastní procesu zjišťování, byly zabezpečené. Vylepšení zjišťování zpráv se zabezpečením zmírňuje různé typy útoků (změna zprávy, odmítnutí služby, přehrání, falšování. Tato ukázka implementuje vlastní kanály, které počítají a ověřují podpisy zpráv pomocí formátu kompaktního podpisu (popsaného v části 8.2 specifikace WS-Discovery). Ukázka podporuje [jak specifikaci 2005 Discovery,](http://specs.xmlsoap.org/ws/2005/04/discovery/ws-discovery.pdf) tak [verzi 1.1](http://docs.oasis-open.org/ws-dd/discovery/1.1/cs-01/wsdd-discovery-1.1-spec-cs-01.pdf).  
  
 Vlastní kanál se použije nad existující zásobník kanálu pro zjišťování a oznámení koncových bodů. Tímto způsobem je záhlaví podpisu použito pro každou odeslanou zprávu. Podpis je ověřen na přijatých zprávách a pokud se neshoduje nebo pokud zprávy nemají podpis, jsou zprávy vynechány. K podepisování a ověřování zpráv používá ukázka certifikáty.  
  
## <a name="discussion"></a>Diskuse  
 WCF je velmi rozšiřitelný a umožňuje uživatelům přizpůsobit kanály podle potřeby. Ukázka implementuje zjišťování zabezpečené vazby element, který vytváří zabezpečené kanály. Zabezpečené kanály platí a ověřují podpisy zpráv a jsou použity nad aktuálním zásobníkem.  
  
 Prvek zabezpečené vazby vytváří zabezpečené kanály továrny a naslouchací procesy kanálu.  
  
## <a name="secure-channel-factory"></a>Továrna zabezpečeného kanálu  
 Zabezpečená továrna kanálu vytvoří výstupní nebo duplexní kanály, které přidávají kompaktní podpis do záhlaví zpráv. Chcete-li zachovat zprávy co nejmenší, použije se formát kompaktního podpisu. Struktura kompaktního podpisu je uvedena v následujícím příkladu.  
  
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
> Byl `PrefixList` přidán do protokolu verze Discovery 2008.  
  
 Chcete-li vypočítat podpis, ukázka určuje rozbalené položky podpisu. Podpis XML`SignedInfo`( ) je `ds` vytvořen pomocí předpony oboru názvů, jak to vyžaduje specifikace WS-Discovery. Tělo a všechny hlavičky v oborech názvů zjišťování a adresování jsou v podpisu odkazovány, takže s nimi nelze manipulovat. Každý odkazovaný prvek je transformován pomocíhttp://www.w3.org/2001/10/xml-exc-c14n# exclusive canonicalization ( ) ahttp://www.w3.org/2000/09/xmldsig#sha1 pak je vypočítána hodnota digest SHA-1 ( ). Na základě všech odkazovaných prvků a jejich hodnot digest se vypočítáhttp://www.w3.org/2000/09/xmldsig#rsa-sha1 hodnota podpisu pomocí algoritmu RSA ( ).  
  
 Zprávy jsou podepsány certifikátem zadaným klientem. Umístění úložiště, název a název subjektu certifikátu musí být určeny při vytvoření prvku vazby. `KeyId` V kompaktním podpisu představuje identifikátor klíče podpisového tokenu a je identifikátor klíče subjektu (SKI) podpisového tokenu nebo (pokud SKI neexistuje) algoritmus hash SHA-1 veřejného klíče podpisového tokenu.  
  
## <a name="secure-channel-listener"></a>Naslouchací proces zabezpečeného kanálu  
 Naslouchací proces zabezpečeného kanálu vytvoří vstupní nebo duplexní kanály, které ověřují kompaktní podpis v přijatých zprávách. Chcete-li ověřit `KeyId` podpis, zadaný v kompaktním podpisu připojeném ke zprávě se používá k výběru certifikátu ze zadaného úložiště. Pokud zpráva nemá podpis nebo se nezdaří kontrola podpisu, zprávy jsou vynechány. Chcete-li použít zabezpečenou vazbu, ukázka definuje továrnu, která vytváří vlastní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> s přidaným discovery secure vazby elementu. Tyto zabezpečené koncové body lze použít v posluchači oznámení zjišťování a zjistitelné služby.  
  
## <a name="sample-details"></a>Podrobnosti ukázky  
 Ukázka obsahuje knihovnu a 4 konzolové aplikace:  
  
- **DiscoverySecurityChannels**: Knihovna, která zveřejňuje zabezpečené vazby. Knihovna vypočítá a ověří kompaktní podpis pro odchozí/příchozí zprávy.  
  
- **Služba**: Služba odhalující smlouvu ICalculatorService, vlastní hostované. Služba je označena jako zjistitelná. Uživatel specifikuje podrobnosti o certifikátu použitém k podepisování zpráv zadáním umístění úložiště a názvu úložiště a názvu subjektu nebo jiného jedinečného identifikátoru certifikátu a úložiště, kde jsou umístěny klientské certifikáty (certifikáty používané k zkontrolujte podpis pro příchozí zprávy). Na základě těchto podrobností je vytvořen a používán udpDiscoveryEndpoint s přidaným zabezpečením.  
  
- **Klient**: Tato třída se pokusí zjistit ICalculatorService a volat metody ve službě. Opět platí, že s přidanou <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> zabezpečení je sestaven a slouží k podepisování a ověřování zpráv.  
  
- **AnnouncementListener**: Samoobslužná služba, která naslouchá oznámením online a offline a používá koncový bod zabezpečeného oznámení.  
  
> [!NOTE]
> Pokud je soubor Setup.bat spuštěn vícekrát, správce certifikátu vás vyzve k výběru certifikátu, který chcete přidat, protože existují duplicitní certifikáty. V takovém případě by měl být soubor Setup.bat přerušen a soubor Cleanup.bat by měl být volán, protože duplikáty již byly vytvořeny. Cleanup.bat vás také vyzve k výběru certifikátu, který chcete odstranit. Vyberte certifikát ze seznamu a pokračujte ve provádění souboru Cleanup.bat, dokud nezůstanou žádné certifikáty.  
  
#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. Spusťte skript Setup.bat z příkazového řádku pro vývojáře pro visual studio. Ukázka používá certifikáty k podepisování a ověřování zpráv. Skript vytvoří certifikáty pomocí makecert.exe a potom je nainstaluje pomocí programu Certmgr.exe. Skript musí být spuštěn s oprávněními správce.  
  
2. Chcete-li vytvořit a spustit ukázku, otevřete soubor Security.sln v sadě Visual Studio a zvolte **Znovu sestavit vše**. Aktualizujte vlastnosti řešení a spusťte více projektů: vyberte **Spustit** pro všechny projekty kromě DiscoverySecureChannels. Spusťte řešení normálně.  
  
3. Po dokončení s ukázkou spusťte skript Cleanup.bat, který odebere certifikáty vytvořené pro tuto ukázku.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
