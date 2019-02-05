---
title: Zabezpečení přenosu HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 26d72bf234e66ccbf60305d7681f181077589ed0
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739511"
---
# <a name="http-transport-security"></a>Zabezpečení přenosu HTTP
Pokud přenos pomocí protokolu HTTP, je zabezpečení poskytovaný implementace vrstvy SSL (Secure Sockets). SSL se často používá na Internetu k ověření služby ke klientovi a potom k zajištění důvěrnosti (šifrování) do kanálu. Toto téma vysvětluje, jak funguje připojení SSL a jak je implementován ve Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Basic SSL  
 Jak funguje SSL je nejvhodnější je vysvětleno prostřednictvím typického scénáře, v tomto případě banka na webovém serveru. Webu umožňuje zákazníkovi se přihlásit pomocí uživatelského jména a hesla. Po ověřovaného, uživatel provádět transakce, jako je například zobrazení zůstatky na účtu, uhraďte a peníze přesunout z jednoho účtu do druhého.  
  
 Pokud uživatel nejprve navštíví web, mechanismus SSL zahájí řadu jednání, volá se *handshake*, s klientem uživatele (v tomto případě aplikace Internet Explorer). SSL poprvé ověří bank lokality tak, aby zákazník. To je zásadní krok, protože nejdřív musí zákazníci věděli, že komunikují s skutečné lokality a není falešného, který se pokusí přesvědčit do zadáte svoje uživatelské jméno a heslo. SSL nepodporuje ověřování pomocí certifikátu SSL poskytuje důvěryhodnou autoritou, jako je například VeriSign. Logika přejde takto: VeriSign zaručuje za identitu bank lokality. Protože aplikaci Internet Explorer důvěřuje VeriSign, je důvěryhodné lokalitě. Pokud chcete zkontrolovat s VeriSign, můžete to také provést kliknutím na logo společnosti VeriSign. Příkaz pravosti, který představuje se datum vypršení platnosti a na koho se vydává (bankovní lokality).  
  
 Zahájení zabezpečené relace, klient odešle serveru spolu s seznam kryptografických algoritmů můžete použít k podepsání, generování hodnoty hash a šifrování a dešifrování s ekvivalent "hello". V odpovědi, tato lokalita odesílá zpět potvrzení a jeho výběru jednoho z algoritmů sad. Během této metody handshake počáteční obou stran odesílat a přijímat náhodně generované identifikátory. A *nonce* je náhodně generované část dat, která se používá v kombinaci s veřejným klíčem tohoto webu, vytvoří hodnotu hash. A *hash* je nové číslo, který je odvozen z daných dvou čísel pomocí standardních algoritmů, jako je například SHA1. (Klient a webu také výměnu zpráv souhlas které hashovací algoritmus k použití.) Hodnota hash je jedinečný a slouží pouze pro relaci mezi klientem a webu k šifrování a dešifrování zprávy. Klient a služba mít původní hodnota nonce a veřejný klíč certifikátu, takže obě strany mohou generovat stejnou hodnotu hash. Proto se klient ověřuje-the-hash odeslaných službou (a) pomocí dohodnutých po algoritmus pro výpočet hodnoty hash z dat, a (b) porovnání této hodnoty hash odeslaných službou; Pokud se dva shodují, má klient jistotu, že-the-hash nebylo manipulováno. Klient pak můžete použít tato hodnota hash jako klíč k šifrování zpráv, který obsahuje další nová hodnota hash. Službu můžete dešifrování zprávy pomocí-the-hash a obnovit tato druhé konečná hodnota hash. Souhrnné informace (náhodně generované identifikátory, veřejný klíč a další data) se teď označuje pro obě strany a konečná hodnota hash (nebo hlavního klíče) je možné vytvořit. Tento poslední klíč je směrován šifrovaně využitím další poslední hodnotu hash. Hlavní klíč se pak používá k šifrování a dešifrování zprávy pro ostatní relace. Protože klient a služba používá stejný klíč, to se také nazývá *klíč relace*.  
  
 Klíč relace je také definovány jako symetrický klíč, nebo "sdílený tajný klíč." Symetrické klíče je důležité, protože snižuje výpočetní vyžaduje obě strany transakce. Pokud všechny zprávy vyžadované nové výměny náhodně generované identifikátory a hodnoty hash, by zhoršení výkonu. Proto konečným cílem SSL je použití symetrický klíč, který umožňuje zprávy tok volně mezi dvěma stranami s vyšší úrovní zabezpečení a efektivitu.  
  
 Předchozí popis je zjednodušenou verzí co se stane, protože protokol se může lišit od serveru lokality. Je také možné, že klienta i webu i vygenerovat náhodně generované identifikátory, které jsou spojené algorithmically při vyjednávání metodou handshake přidat další složitosti a proto ochrany, do procesu výměny dat.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certifikáty a infrastruktury veřejných klíčů  
 Při vyjednávání metodou handshake službu také odešle svůj certifikát SSL klienta. Tento certifikát obsahuje informace, například jeho platnosti, vydávání autority a tohoto webu identifikátor URI (Uniform Resource). Klient porovná identifikátor URI pro identifikátor URI měl původně kontaktovat a zkontrolujte shody a také ověří datum a vystavující autorita.  
  
 Každý certifikát má dva klíče, privátní klíč a veřejný klíč a dva jsou označovány jako *exchange pár klíčů*. Stručně řečeno jenom na vlastníka certifikát bude znám soukromý klíč při čtení z certifikátu veřejného klíče. Ani jeden klíč slouží k šifrování nebo dešifrování algoritmu digest, hodnota hash, nebo další klíč, ale pouze protikladné operace. Například pokud klient zašifruje pomocí veřejného klíče, pouze lokalitě můžete dešifrování zprávy pomocí soukromého klíče. Podobně pokud zašifruje web s privátním klíčem, klient může dešifrovat s veřejným klíčem. To poskytuje záruku klientovi zprávy jsou během výměny pouze s vlastník privátního klíče, protože mohou ho dešifrovat jenom zpráv šifrovaných pomocí privátního klíče pomocí veřejného klíče. Web je zajištěno, že je výměna zpráv pomocí klienta, který má šifrované pomocí veřejného klíče. Tato výměna je pouze pro počáteční handshake, ale, což je důvod, proč bezpečné spoustu dalších věcí slouží k vytvoření skutečné symetrický klíč. Veškerá komunikace se však závisí na služby, která má platný certifikát SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementace SSL s použitím technologie WCF  
 Zabezpečení přenosu HTTP (nebo SSL) je poskytováno externě WCF. SSL lze implementovat v jednom ze dvou způsobů; rozhodujícím faktorem je, jak je vaše aplikace hostovaná:  
  
-   Pokud používáte Internetové informační služby (IIS) jako hostitele WCF, nastavení služby SSL pomocí infrastruktury služby IIS.  
  
-   Při vytváření aplikace v místním prostředí WCF, můžete svázat certifikát SSL na adresu, pomocí nástroje HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Pomocí služby IIS pro zabezpečení přenosu  
  
#### <a name="iis-70"></a>Internetová informační služba 7,0  
 Chcete-li nastavit [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jako zabezpečené hostitele (pomocí protokolu SSL), najdete v článku [IIS 7.0 Beta: Konfigurace zabezpečeného Sockets Layer ve službě IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Konfigurace certifikátů pro použití s [!INCLUDE[iisver](../../../../includes/iisver-md.md)], naleznete v tématu [IIS 7.0 Beta: Konfigurace certifikátů serveru ve službě IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>Internetová informační služba 6.0  
 Chcete-li nastavit [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jako zabezpečené hostitele (pomocí protokolu SSL), najdete v článku [konfigurace Secure Sockets Layer](https://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Konfigurace certifikátů pro použití s [!INCLUDE[iis601](../../../../includes/iis601-md.md)], naleznete v tématu [Certificates_IIS_SP1_Ops](https://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Pomocí HttpCfg pro protokol SSL  
 Při vytváření aplikace v místním prostředí WCF, stáhněte si nástroj HttpCfg.exe, k dispozici na [webu podpory nástroje systému Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=29002).  
  
 Další informace o použití nástroje HttpCfg.exe nastavení portu s certifikátem X.509, naleznete v tématu [jak: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Viz také:
- [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
