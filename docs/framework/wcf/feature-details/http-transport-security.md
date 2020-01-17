---
title: Zabezpečení přenosu HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 4bd3fbfd39538eee4344ef0a8ca4fe61b372ab70
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212136"
---
# <a name="http-transport-security"></a>Zabezpečení přenosu HTTP
Při použití protokolu HTTP jako přenosu je zabezpečení zajišťováno pomocí implementace SSL (Secure Sockets Layer) (SSL). Protokol SSL se v síti Internet často používá k ověření služby klientovi a pak k zajištění důvěrnosti (šifrování) kanálu. V tomto tématu se dozvíte, jak funguje SSL a jak je implementováno v Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Základní SSL  
 Princip fungování SSL je nejlépe vysvětlený obvyklým scénářem, v tomto případě na webu banky. Lokalita umožňuje zákazníkům přihlásit se pomocí uživatelského jména a hesla. Po ověření může uživatel provádět transakce, jako je například zobrazení zůstatků účtů, platby za placené platby a přesun peněz z jednoho účtu na jiný.  
  
 Když uživatel poprvé navštíví lokalitu, mechanismus SSL zahájí řadu vyjednávání označovaných jako *handshake*s klientem uživatele (v tomto případě Internet Exploreru). Protokol SSL nejprve ověřuje bankovní web u zákazníka. Toto je zásadní krok, protože zákazníci musí nejdřív zjistit, že komunikují se skutečnou lokalitou, a ne falešnou identitou, která je vyzkouší při psaní do svého uživatelského jména a hesla. SSL toto ověřování provádí pomocí certifikátu SSL poskytnutého důvěryhodnou autoritou, jako je například VeriSign. Tato logika bude vypadat takto: VeriSign ručí za identitu webu banky. Vzhledem k tomu, že Internet Explorer důvěřuje společnosti VeriSign, je tato lokalita důvěryhodná. Pokud chcete kontrolovat u společnosti VeriSign, můžete tak učinit také kliknutím na logo společnosti VeriSign. Který prezentuje prohlášení o pravosti s datem vypršení platnosti a jeho vystavení pro (bankovní Web).  
  
 Aby bylo možné zahájit zabezpečenou relaci, klient pošle ekvivalent "Hello" serveru společně se seznamem kryptografických algoritmů, které může použít k podepsání, generování hodnot hash a k šifrování a dešifrování pomocí. V reakci web pošle zpět potvrzení a zvolí jednu ze sad algoritmů. Během této počáteční metody handshake obě strany odesílají a přijímají hodnoty nonce. *Hodnota nonce* je náhodně generovaná část dat, která se používá v kombinaci s veřejným klíčem lokality k vytvoření hodnoty hash. *Hodnota hash* je nové číslo, které je odvozeno od dvou čísel pomocí standardního algoritmu, jako je SHA1. (Klient a lokalita také vyměňuje zprávy, aby se dohodli, který algoritmus hash použít.) Hodnota hash je jedinečná a používá se pouze pro relaci mezi klientem a serverem k šifrování a dešifrování zpráv. Klient i služba mají původní hodnotu nonce a veřejný klíč certifikátu, takže obě strany mohou vygenerovat stejnou hodnotu hash. Proto klient ověří hodnotu hash odeslanou službou pomocí (a) pomocí schváleného algoritmu, který vypočítá hodnotu hash z dat, a (b) porovná je hodnotě hash odesílané službou; Pokud se shoduje shoda, pak klient zaručuje, že hodnota hash nebyla úmyslně poškozena. Klient pak může tuto hodnotu hash použít jako klíč k šifrování zprávy, která obsahuje ještě jinou novou hodnotu hash. Služba může zprávu dešifrovat pomocí algoritmu hash a obnovit tento druhý-konečný hash. Shromážděné informace (hodnoty nonce, Public Key a další data) jsou nyní na obou stranách známy a lze vytvořit konečnou hodnotu hash (nebo hlavní klíč). Tento finální klíč se pošle zašifrovaný pomocí hodnoty hash Next-Last. Hlavní klíč se pak použije k šifrování a dešifrování zpráv pro zbytek relace. Vzhledem k tomu, že klient i služba používají stejný klíč, nazývá se taky *klíč relace*.  
  
 Klíč relace je také charakterizován jako symetrický klíč nebo "sdílený tajný klíč". Existence symetrického klíče je důležité, protože snižuje výpočet vyžadovaný oběma stranami transakce. Pokud každá zpráva vyvolala nové výměny hodnot nonce a hodnot hash, výkon by se zhoršil. Proto je konečným cílem protokolu SSL použití symetrického klíče, který umožňuje volně přetékání zpráv mezi dvěma stranami s větším stupněm zabezpečení a efektivity.  
  
 Předchozí popis je zjednodušená verze, co se stane, protože protokol se může lišit od lokality do lokality. Je také možné, že klient i lokalita vygeneruje náhodně generované identifikátory (algorithmically), které jsou kombinované během metody handshake pro přidání větší složitosti, a proto ochranu proti procesu výměny dat.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certifikáty a infrastruktura veřejných klíčů  
 Během metody handshake služba také odešle svůj certifikát SSL klientovi. Certifikát obsahuje informace, jako je datum vypršení platnosti, vydávající autorita a identifikátor URI (Uniform Resource Identifier) webu. Klient porovná identifikátor URI s identifikátorem URI, který byl původně kontaktován, aby zajistil shodu a také zkontroloval datum a vydávající autoritu.  
  
 Každý certifikát má dva klíče, privátní klíč a veřejný klíč a dva se označují jako *pár klíčů pro výměnu*. V krátké době se privátní klíč ví jenom na vlastníka certifikátu, zatímco veřejný klíč je čitelný z certifikátu. Libovolný klíč lze použít k šifrování nebo dešifrování algoritmu hash, hodnoty hash nebo jiného klíče, ale pouze v případě opaku operací. Pokud se třeba klient šifruje pomocí veřejného klíče, může zprávu dešifrovat jenom lokalitou pomocí privátního klíče. Podobně platí, že pokud se lokalita šifruje s privátním klíčem, může se klient dešifrovat pomocí veřejného klíče. To klientovi zajišťuje jistotu, že se zprávy vyměňují pouze s držitelem privátního klíče, protože je možné dešifrovat pouze zprávy zašifrované pomocí privátního klíče pomocí veřejného klíče. Lokalita je zajištěna tím, že vyměňuje zprávy pomocí klienta, který je zašifrovaný pomocí veřejného klíče. Tato výměna je zabezpečená jenom pro počáteční signalizaci, ale to je mnohem víc, abyste vytvořili skutečný symetrický klíč. Veškerá komunikace však závisí na službě, která má platný certifikát SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementace SSL pomocí WCF  
 Zabezpečení přenosu HTTP (nebo SSL) je poskytováno externě službě WCF. SSL můžete implementovat jedním ze dvou způsobů: rozhodující faktor je způsob hostování vaší aplikace:  
  
- Pokud jako hostitele WCF používáte Internetová informační služba (IIS), použijte k nastavení služby SSL infrastrukturu služby IIS.  
  
- Pokud vytváříte aplikaci WCF s místním hostováním, můžete k ní pomocí nástroje HttpCfg. exe vytvořit propojení certifikátu SSL s adresou.  
  
### <a name="using-iis-for-transport-security"></a>Zabezpečení přenosu pomocí služby IIS  
  
#### <a name="iis-70"></a>Internetová informační služba 7,0  
 Pokud chcete nastavit službu IIS 7,0 jako zabezpečeného hostitele (pomocí protokolu SSL), přečtěte si téma [konfigurace SSL (Secure Sockets Layer) ve službě IIS 7,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
Informace o konfiguraci certifikátů pro použití se službou IIS 7,0 najdete v tématu [Konfigurace certifikátů serveru ve službě iis 7,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>Internetová informační služba 6.0  
 Pokud chcete nastavit službu IIS 6,0 jako zabezpečeného hostitele (pomocí protokolu SSL), přečtěte si téma [konfigurace SSL (Secure Sockets Layer)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736992(v=ws.10)).  
  
 Pokud chcete nakonfigurovat certifikáty pro použití se službou IIS 6,0, přečtěte si téma [Certificates_IIS_SP1_Ops](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757474(v=ws.10)).  
  
### <a name="using-httpcfg-for-ssl"></a>Použití HttpCfg pro SSL  

 Pokud vytváříte aplikaci WCF s místním hostováním, použijte nástroj [Httpcfg. exe](/windows/win32/http/httpcfg-exe) .
  
 Další informace o použití nástroje HttpCfg. exe k nastavení portu s certifikátem X. 509 naleznete v tématu [How to: Configure a port with a Certificate SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
