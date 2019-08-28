---
title: Ukázka zabezpečení zjišťování
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
ms.openlocfilehash: dfc0dfcd3b4d814a158b328ef202d5438e583a8c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039818"
---
# <a name="discovery-security-sample"></a>Ukázka zabezpečení zjišťování
Specifikace zjišťování nevyžaduje, aby koncové body, které jsou součástí procesu zjišťování, byly zabezpečené. Zvýšením počtu zpráv zjišťování se zabezpečením sníží riziko různých typů útoků (Změna zprávy, odmítnutí služby, opětovné přehrání, falšování identity). Tato ukázka implementuje vlastní kanály, které počítají a ověřují signatury zpráv pomocí formátu kompaktního podpisu (popsaného v části 8,2 specifikace WS-Discovery). Ukázka podporuje [specifikaci zjišťování 2005](https://go.microsoft.com/fwlink/?LinkId=177912) i [verzi 1,1](https://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Vlastní kanál se použije na začátku existujícího zásobníku kanálů pro zjišťování a koncové body oznámení. Tímto způsobem se pro každou odeslanou zprávu použije záhlaví podpisu. Podpis se ověřuje u přijatých zpráv, a pokud se neshoduje nebo pokud zprávy nemají podpis, zprávy se zahozeny. Ukázka používá certifikáty, aby bylo možné podepsat a ověřit zprávy.  
  
## <a name="discussion"></a>Účely  
 WCF je velmi rozšiřitelné a umožňuje uživatelům přizpůsobit kanály podle potřeby. Ukázka implementuje zabezpečený prvek vazby zjišťování, který vytváří zabezpečené kanály. Zabezpečené kanály používají a ověřují podpisy zpráv a jsou použity na začátku aktuálního zásobníku.  
  
 Element Secure Binding vytváří objekty pro vytváření zabezpečených kanálů a naslouchací procesy kanálu.  
  
## <a name="secure-channel-factory"></a>Objekt pro vytváření zabezpečeného kanálu  
 Objekt pro vytváření zabezpečeného kanálu vytváří výstupní nebo duplexní kanály, které přidávají kompaktní podpis do záhlaví zpráv. Chcete-li zachovat zprávy co nejmenším možným způsobem, je použit formát kompaktního podpisu. V následujícím příkladu je uvedena struktura kompaktního podpisu.  
  
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
> `PrefixList` Byla přidána do protokolu verze zjišťování 2008.  
  
 Pro výpočet podpisu ukázka určuje rozšířené položky podpisu. Signatura XML (`SignedInfo`) se vytvoří `ds` pomocí předpony oboru názvů, jak vyžaduje specifikace WS-Discovery. V podpisu je odkazováno tělo a všechny hlavičky v názvech oborů zjišťování a adresování, takže je nelze považovat za neoprávněně. Každý odkazovaný element je transformován pomocí exkluzivního kanonikalizace (http://www.w3.org/2001/10/xml-exc-c14n# ) a pak je vypočítána hodnota digest SHA-1 (http://www.w3.org/2000/09/xmldsig#sha1 ). V závislosti na všech odkazovaných prvcích a jejich hodnotách Digest se hodnota signatury vypočítá pomocí algoritmu http://www.w3.org/2000/09/xmldsig#rsa-sha1 RSA ().  
  
 Zprávy jsou podepsány pomocí certifikátu zadaného klientem. Při vytvoření prvku vazby je nutné zadat umístění úložiště, název a název subjektu certifikátu. `KeyId` V kompaktním podpisu představuje identifikátor klíče podpisového tokenu, který je identifikátorem klíče subjektu (Ski) podpisového tokenu, nebo (Pokud není k dispozici) hodnota hash SHA-1 veřejného klíče podpisového tokenu.  
  
## <a name="secure-channel-listener"></a>Naslouchací proces zabezpečeného kanálu  
 Naslouchací proces zabezpečeného kanálu vytváří vstupní nebo duplexní kanály, které ověřují kompaktní podpis v přijatých zprávách. Chcete-li ověřit podpis, `KeyId` je k výběru certifikátu ze zadaného úložiště použit parametr zadaný v kompaktním podpisu připojeném ke zprávě. Pokud zpráva nemá podpis nebo se její podpis nepovede, jsou zprávy vyřazené. Chcete-li použít zabezpečenou vazbu, ukázka definuje objekt pro vytváření, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> který <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> vytvoří vlastní a s přidaným prvkem zabezpečené vazby zjišťování. Tyto zabezpečené koncové body lze použít v posluchačích oznámení zjišťování a zjistitelných službách.  
  
## <a name="sample-details"></a>Podrobnosti ukázky  
 Ukázka zahrnuje knihovny a 4 konzolové aplikace:  
  
- **DiscoverySecurityChannels**: Knihovna, která zveřejňuje zabezpečenou vazbu. Knihovna vypočítá a ověří kompaktní podpis pro odchozí a příchozí zprávy.  
  
- **Služba**: Služba, která zveřejňuje kontrakt ICalculatorService, který je hostován v místním prostředí. Služba je označená jako zjistitelná. Uživatel Určuje podrobnosti certifikátu používaného k podepisování zpráv zadáním umístění úložiště a názvu subjektu nebo jiného jedinečného identifikátoru pro certifikát a úložištěm, kde jsou umístěny klientské certifikáty (certifikáty použité pro kontrolovat podpis příchozích zpráv). Na základě těchto informací se sestaví a použije UdpDiscoveryEndpoint s přidaným zabezpečením.  
  
- **Klient**: Tato třída se pokusí zjistit ICalculatorService a volat metody ve službě. Znovu se vytvoří <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a s přidaným zabezpečením se sestaví a použije k podepsání a ověření zpráv.  
  
- **AnnouncementListener**: Samoobslužná služba, která naslouchá online a offline oznámením a používá koncový bod zabezpečeného oznámení.  
  
> [!NOTE]
> Pokud se instalační program. bat spustí víckrát, správce certifikátů vás vyzve k výběru certifikátu, který se má přidat, protože jsou k dispozici duplicitní certifikáty. V takovém případě by měl být Setup. bat přerušen a měl by být volán program Cleanup. bat, protože duplicity již byly vytvořeny. Vyčištění. bat vás také vyzve k výběru certifikátu, který chcete odstranit. Vyberte certifikát ze seznamu a pokračujte v provádění nástroje CleanUp. bat, dokud nebudou žádné certifikáty zbývající.  
  
#### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. Spusťte skript Setup. bat z Developer Command Prompt pro Visual Studio. Ukázka používá certifikáty k podepisování a ověřování zpráv. Skript vytvoří certifikáty pomocí nástroje MakeCert. exe a pak je nainstaluje pomocí nástroje Certmgr. exe. Skript musí být spuštěn s oprávněními správce.  
  
2. Chcete-li vytvořit a spustit ukázku, otevřete soubor Security. sln v aplikaci Visual Studio a vyberte možnost **znovu sestavit vše**. Aktualizovat vlastnosti řešení, aby bylo možné spustit více projektů: vyberte možnost **Spustit** pro všechny projekty s výjimkou DiscoverySecureChannels. Řešení spouštějte normálně.  
  
3. Až budete s ukázkou hotovi, spusťte skript Cleanup. bat, který odebere certifikáty vytvořené pro tuto ukázku.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
