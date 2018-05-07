---
title: Ukázka zabezpečení zjišťování
ms.date: 03/30/2017
ms.assetid: b8db01f4-b4a1-43fe-8e31-26d4e9304a65
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a701a516a93cf94f76950b7b1b1c7f3a9b41214e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="discovery-security-sample"></a>Ukázka zabezpečení zjišťování
Specifikace zjišťování nevyžaduje, aby koncové body, které jsou součástí procesu zjišťování jako zabezpečené. Rozšíření zjišťování zprávy s zabezpečení snižuje různé typy útoků (zprávy změnou, odepření služby, opakování, falšování identity). Tato ukázka implementuje vlastní kanály, které výpočetní a ověřte podpisy zpráv compact podpis formátu (popsaný v části 8.2 specifikace WS-Discovery). Ukázka podporuje i [2005 zjišťování specifikace](http://go.microsoft.com/fwlink/?LinkId=177912) a [verze 1.1](http://go.microsoft.com/fwlink/?LinkId=179677).  
  
 Vlastní kanál je použita na existující zásobníku kanál pro oznámení a zjišťování koncových bodů. Tímto způsobem hlavičku podpis platí pro všechny zprávy určené. Ověření podpisu na přijatých zpráv a pokud neodpovídá nebo pokud zprávy neobsahuje podpis, jsou zprávy vyřadit. Příklad k podepisování a zkontrolujte zprávy, používá certifikáty.  
  
## <a name="discussion"></a>Diskusní  
 WCF velmi rozšiřitelný a umožňuje uživatelům možnost kanály podle potřeby přizpůsobit. Ukázka implementuje element zabezpečené vazby a zjišťování, který sestaví zabezpečené kanály. Zabezpečené kanály použít ověřte podpisy zpráv a uplatňují na základě aktuálního zásobníku.  
  
 Element zabezpečené vazby sestavení objektů Factory zabezpečeného kanálu a moduly pro naslouchání kanálu.  
  
## <a name="secure-channel-factory"></a>Zabezpečeného kanálu  
 Objekt factory zabezpečený kanál vytvoří výstupní nebo duplexní kanály, které přidat compact podpis do záhlaví zpráv. Chcete-li zachovat zprávy co nejmenší compact podpis formát byl použit. Struktura compact podpisu je znázorněno v následujícím příkladu.  
  
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
>  `PrefixList` Byl přidán protokolu verze zjišťování 2008.  
  
 Vypočítat podpis, určuje ukázku rozšířené podpis položky. Podpis XML (`SignedInfo`) je vytvořený pomocí `ds` předponu oboru názvů, podle potřeby ve specifikaci WS-Discovery. Text a všechny hlavičky v zjišťování a adresování obory názvů se odkazuje v podpisu, aby nemohlo být manipulováno s. Každý odkazovaný element převede pomocí výhradní kanonizace (http://www.w3.org/2001/10/xml-exc-c14n# ), a pak je počítaný hodnotou hodnotu hash SHA-1 (http://www.w3.org/2000/09/xmldsig#sha1 ). Na základě všechny odkazované elementy a jejich hodnoty digest, podpis hodnota je vypočítána pomocí algoritmu RSA (http://www.w3.org/2000/09/xmldsig#rsa-sha1 ).  
  
 Zprávy jsou podepsané certifikátem zadaného klienta. Umístění úložiště, název a název subjektu certifikátu musí zadat při vytváření prvku vazby. `KeyId` v compact podpis představuje identifikátor klíče podpisového tokenu a je subjektu klíč identifikátor (identifikátor klíče subjektu) podpisový tokenu nebo (Pokud identifikátor klíče subjektu neexistuje) hash SHA-1 podpisový tokenu veřejného klíče.  
  
## <a name="secure-channel-listener"></a>Zabezpečený kanál naslouchání  
 Naslouchací proces zabezpečený kanál vytvoří vstupní nebo duplexní kanály, které ověřují compact podpis v přijatých zpráv. Ověření podpisu, `KeyId` zadaný v zkomprimovat podpisu připojeného ke zprávě slouží k výběru certifikát z určeného úložiště. Pokud zpráva nemá podpis nebo Kontrola podpisu selže, jsou zprávy vyřadit. Pokud chcete používat zabezpečené vazby, ukázky definuje objekt factory, který vytvoří vlastní <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> s elementem zabezpečené vazby přidané zjišťování. Naslouchací procesy oznámení zjišťování a zjistitelný služeb lze tyto zabezpečené koncové body.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázka obsahuje knihovnu a 4 konzolové aplikace:  
  
-   **DiscoverySecurityChannels**: knihovnu, která zveřejňuje zabezpečené vazby. Knihovny vypočítá a ověří compact podpis pro odchozí nebo příchozí zprávy.  
  
-   **Služba**: vystavení ICalculatorService kontrakt služby s vlastním hostováním. Služba je označena jako zjistitelné. Určuje podrobnosti certifikát používaný k podepisování zpráv tak, že zadáte umístění úložiště a název a název předmětu nebo jiný jedinečný identifikátor pro certifikát uživatele a úložiště, kde jsou klientské certifikáty umístěny (certifikátů používaných pro Zkontrolujte, zda podpis pro příchozí zprávy). Podle toho, tyto podrobnosti, je UdpDiscoveryEndpoint s zvýšení zabezpečení vytvořené a používat.  
  
-   **Klient**: Tato třída se pokusí zjistit ICalculatorService a volat metody pro službu. Znovu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> s přidat zabezpečení je vytvořená a použít k podepsání a ověření zprávy.  
  
-   **AnnouncementListener**: samoobslužné hostovanou službu, která naslouchá online a offline oznámení a používá koncový bod zabezpečené oznámení.  
  
> [!NOTE]
>  Když Setup.bat je spustit vícekrát, vyzve vás správce certifikátů pro zvolit certifikát, který chcete přidat, protože existují duplicitní certifikáty. V takovém případě by měl být Setup.bat přerušena a Cleanup.bat by měla být volána, protože tyto duplikáty již byly vytvořeny. CleanUp.bat taky výzva k výběru certifikát odstranit. Vyberte certifikát ze seznamu a pokračovat v provádění Cleanup.bat, dokud se zbývající žádné certifikáty.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Spusťte skript Setup.bat z příkazového řádku Visual Studia. Ukázka používá certifikáty pro podepsání a ověření zprávy. Skript vytvoří certifikáty pomocí Makecert.exe a potom nainstaluje je pomocí Certmgr.exe. Skript musí být spuštěn s oprávněními správce.  
  
2.  Sestavení a spuštění ukázky, otevřete soubor Security.sln v sadě Visual Studio a zvolte **znovu vytvořit všechny**. Aktualizovat vlastnosti řešení spuštění více projektů: vyberte **spustit** pro všechny projekty s výjimkou DiscoverySecureChannels. Spuštění řešení normálně.  
  
3.  Jakmile jste hotovi s ukázkou spusťte Cleanup.bat skript, který odstraní certifikáty vytvořené pro tuto ukázku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DiscoveryScenario`  
  
## <a name="see-also"></a>Viz také
