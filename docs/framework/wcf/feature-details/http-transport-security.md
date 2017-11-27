---
title: "Zabezpečení přenosu HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 414ae499b777be5536e64a86fa0c60f9cd2da25a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="http-transport-security"></a>Zabezpečení přenosu HTTP
Při použití protokolu HTTP jako přenos, je zabezpečení poskytované implementace Secure Sockets Layer (SSL). SSL je široce používaných na Internetu k ověřování klienta a potom k zajištění důvěrnosti (šifrování) do kanálu. Toto téma vysvětluje, jak funguje protokol SSL a jak jsou implementované v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="basic-ssl"></a>Základní SSL  
 Jak funguje SSL je nejlepší vysvětlené prostřednictvím Typický scénář, v takovém případě bank webu. Přihlaste se pomocí uživatelského jména a hesla zákazníkům umožňuje webu. Uživatel můžete po ověřovaného, provádění transakcí, jako je například zůstatky na účtu zobrazení, platit faktur a peníze přesunuty z jednoho účtu do jiného.  
  
 Pokud uživatel navštíví nejprve webu, mechanismus SSL zahájí řadu jednání, názvem *metody handshake*, s klientem uživatele (v tomto případě aplikace Internet Explorer). SSL poprvé ověří bank lokality tak, aby zákazník. Je to nezbytné, proto zákazníky musíte nejdřív znát, že komunikují s skutečné lokality a není falešná identita, který se pokouší je přesvědčit do zadáním v jejich uživatelské jméno a heslo. Protokol SSL nebude toto ověřování pomocí certifikátu protokolu SSL poskytované důvěryhodnou autoritou, jako je například VeriSign. Logika přejde takto: VeriSign poskytuje záruku identity webu bank. Protože aplikace Internet Explorer důvěřuje VeriSign, web není důvěryhodný. Pokud chcete zkontrolovat s VeriSign, můžete tak taky provést kliknutím na VeriSign logo. Příkaz pravosti, uvede se datum vypršení platnosti a který byl vydán pro (lokalita bank).  
  
 K zahájení zabezpečené relace, klient odešle serveru spolu s seznam kryptografických algoritmů můžete použít k přihlášení, generování hodnoty hash a šifrování a dešifrování s ekvivalentem "hello". V odpovědi, tato lokalita odesílá zpět potvrzení a jeho volbou jedné ze sad algoritmy. Během této počáteční metody handshake obě strany odesílat a přijímat náhodně generované identifikátory. A *hodnotu nonce* je náhodně generované část dat, který se používá v kombinaci s veřejný klíč lokality, vytvoření hodnoty hash. A *hash* je nové číslo, který je odvozený od dvou čísel pomocí standardních algoritmů, například SHA1. (Klient a webu také výměna zpráv souhlasit který algoritmus hash použít.) Hodnota hash je jedinečný a se používá pouze pro relace mezi klientem a webu k šifrování a dešifrování zprávy. Klient a služba mít původní hodnotu nonce a veřejný klíč certifikátu, takže na obou stranách může generovat stejnou hodnotu hash. Proto klient ověří hodnotu hash odeslaných službou (a) pomocí odsouhlaseného při algoritmus vypočítat hodnotu hash z dat, a (b) porovná je s hash odeslaných službou; Pokud se dva shodují, má klient záruku toho, že hodnota hash nikdo neoprávněně nemanipuloval. Klient může poté použít tato hodnota hash jako klíč pro šifrování zprávu, která obsahuje další nové hodnoty hash. Službu můžete dešifrování zprávy pomocí algoritmu hash a obnovit tato sekundu konečná hodnota hash. Na obou stranách se nyní označuje Akumulovaná informace (náhodně generované identifikátory, veřejný klíč a další data) a nelze vytvořit konečné hash (nebo hlavní klíč). Tento poslední klíč je odeslán šifrovaných pomocí algoritmu hash další poslední. Hlavní klíč je poté použít k šifrování a dešifrování zprávy pro resetování relace. Vzhledem k klient a služba používá stejný klíč, to se označuje taky jako *klíč relace*.  
  
 Klíč relace je taky vyznačují jako symetrický klíč, nebo "sdílený tajný klíč." Symetrický klíč je důležité, protože snižuje výpočet vyžadovanou obou stranách transakce. Pokud každá zpráva požadováno nové exchange náhodně generované identifikátory a hodnoty hash, by zhoršení výkonu. Konečným cílem protokolu SSL je proto používat symetrický klíč, který umožňuje zprávy volně tok mezi sociálními s vyšší úrovní zabezpečení a efektivitu.  
  
 Předchozí popis je zjednodušenou verzi co se stane, protože protokol se může lišit od lokalitami. Je také možné, že klient i lokality obě generovat náhodně generované identifikátory, které jsou spojené algorithmically během metody handshake přidat další složitosti a proto ochranu pro proces výměny dat.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certifikáty a infrastruktury veřejných klíčů  
 Během metody handshake služba rovněž odesílá klientovi svůj certifikát SSL. Certifikát obsahuje informace, jako je například datum vypršení platnosti vydání autoritě a v lokalitě identifikátor URI (Uniform Resource). Klient porovná identifikátor URI pro identifikátor URI měl původně kontaktovat zajistit shoda a také ověří datum a vydávající autorita.  
  
 Každý certifikát má dva klíče, privátní klíč a veřejný klíč a dva jsou známé jako *exchange pár klíčů*. Stručně řečeno privátní klíč je zná pouze vlastník certifikátu při čtení z certifikátu veřejného klíče. Ani jeden klíč slouží k zašifrování a dešifrování ověřování algoritmem digest, hash, nebo jiného klíče, ale pouze rozporu operace. Například pokud klient zašifruje pomocí veřejného klíče, pouze webu můžete dešifrování zprávy pomocí soukromého klíče. Podobně pokud webu zašifruje s privátním klíčem, klient může dešifrovat veřejným klíčem. To poskytuje záruku klientovi zprávy jsou během výměny pouze s vlastník privátního klíče, protože je pak možné dešifrovat jenom zprávy zašifrované pomocí privátního klíče pomocí veřejného klíče. Lokality je zajištěno, že jej vymění zprávy s klientem, který má šifrované pomocí veřejného klíče. Toto exchange je bezpečné pouze pro počáteční handshake, ale, což je důvod, proč mnoho dalších slouží k vytvoření skutečné symetrického klíče. Nicméně veškerá komunikace závisí na službu s platný certifikát SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementace protokolu SSL s použitím technologie WCF  
 Zabezpečení přenosu HTTP (nebo SSL) je k dispozici externě na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Můžete implementovat SSL v jednom ze dvou způsobů; rozhodujícím faktorem je, jak je vaše aplikace hostována:  
  
-   Pokud používáte Internetové informační služby (IIS) jako vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostitele, nastavit služby SSL pomocí infrastruktury služby IIS.  
  
-   Pokud vytváříte vlastním hostováním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, můžete vázat certifikát SSL na adresu pomocí nástroje HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Pomocí služby IIS pro zabezpečení přenosu  
  
#### <a name="iis-70"></a>Internetová informační služba 7,0  
 Nastavit [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jako zabezpečené hostitele (pomocí protokolu SSL), najdete v části [IIS 7.0 Beta: Konfigurace Secure Sockets Layer ve službě IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Pro konfiguraci certifikátů pro použití s [!INCLUDE[iisver](../../../../includes/iisver-md.md)], najdete v části [IIS 7.0 Beta: Konfigurace certifikátů serveru ve službě IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>Internetová informační služba 6.0  
 Nastavit [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jako zabezpečené hostitele (pomocí protokolu SSL), najdete v části [konfigurace Secure Sockets Layer](http://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Pro konfiguraci certifikátů pro použití s [!INCLUDE[iis601](../../../../includes/iis601-md.md)], najdete v části [Certificates_IIS_SP1_Ops](http://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Pomocí HttpCfg pro protokol SSL  
 Pokud vytváříte vlastním hostováním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, stáhněte si nástroj HttpCfg.exe k dispozici [lokality nástrojů podpory systému Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=29002).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí nástroje HttpCfg.exe nastavit port společně s certifikátem X.509, najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
