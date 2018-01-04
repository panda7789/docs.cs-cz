---
title: "Výběr certifikátu a ověření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 54d1409b74793a8539f432ce0b43f410d578e934
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-selection-and-validation"></a>Výběr certifikátu a ověření
<xref:System.Net> Třídy podporují několik způsobů, jak vybrat a ověřit <xref:System.Security.Cryptography.X509Certificates> pro připojení Secure Socket Layer (SSL). Klienta můžete vybrat jeden nebo více certifikátů k vlastnímu ověření serveru. Server může vyžadovat, že klientský certifikát mají jeden nebo více konkrétních atributů pro ověřování.  
  
## <a name="definition"></a>Definice  
 Certifikát je tok bajtů ASCII, který obsahuje veřejný klíč, atributy (například číslo verze, sériové číslo a datum vypršení platnosti) a digitální podpis od certifikační autority. Certifikáty slouží k navázání šifrovaného připojení nebo k ověřování klienta k serveru.  
  
## <a name="client-certificate-selection-and-validation"></a>Výběr certifikátu klienta a ověření  
 Klienta můžete vybrat jeden nebo více certifikáty pro konkrétní připojení SSL. Klientské certifikáty lze přidružit připojení SSL k webového serveru nebo poštovní server SMTP. Klient přidá do kolekce certifikátů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy objektů. Jako příklad použijeme e-mailu, kolekci certifikátů je instance <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) přidružené k <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> vlastnost <xref:System.Net.Mail.SmtpClient> třídy. <xref:System.Net.HttpWebRequest> Třídy je podobná <xref:System.Net.HttpWebRequest.ClientCertificates%2A> vlastnost.  
  
 Hlavní rozdíl mezi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třída je, že privátní klíč se musí nacházet v úložišti certifikátů pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate> třídy.  
  
 I v případě, že certifikáty jsou přidány do kolekce a přidružené k určité připojení SSL se žádné certifikáty odesílat na server, pokud je server vyžádá. Pokud více klientských certifikátů jsou nastavené na připojení, nejlépe, budou použita založen na algoritmu, který zvažuje nalezena shoda mezi seznam vystavitelů certifikátů od serveru a název vystavitele certifikátu klienta.  
  
 <xref:System.Net.Security.SslStream> Třída poskytuje ještě větší kontrolu nad SSL handshake. Klienta můžete zadat delegáta a vyberte, jaký klientský certifikát používat.  
  
 Vzdálený server můžete ověřit, že klientský certifikát je platný, aktuální a podepsaný certifikační autoritou vhodné. Delegát lze přidat do <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> k vynucení ověřování certifikátu.  
  
## <a name="client-certificate-selection"></a>Výběr certifikátu klienta  
 Rozhraní .NET Framework vybere klientský certifikát na server k dispozici následujícím způsobem:  
  
1.  Pokud se klientský certifikát byl předložený dříve k serveru, certifikát se uloží do mezipaměti při prvním uvedené a se znovu použije pro následné požadavky certifikátu.  
  
2.  Pokud se nachází delegáta, vždy výsledek použijte z delegáta jako na klientský certifikát vybrat. Zkuste použít certifikát uložený v mezipaměti, pokud je to možné, ale nepoužívejte anonymní přihlašovací údaje v mezipaměti, pokud delegát vrátila hodnotu null a kolekci certifikátů není prázdná.  
  
3.  Pokud je to první výzvu pro klientský certifikát, rozhraní zobrazí certifikáty v <xref:System.Security.Cryptography.X509Certificates.X509Certificate> nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy objekty přidružené k připojení, hledá nalezena shoda mezi seznam vystavitelů certifikátů, které jsou poskytované Server a název vystavitele certifikátu klienta. První certifikát, který odpovídá je odeslána na server. Pokud žádné odpovídající položky certifikát nebo kolekci certifikátu je prázdný, pak anonymní přihlašovací údaje jsou odeslány server.  
  
## <a name="tools-for-certificate-configuration"></a>Nástroje pro konfiguraci certifikátu  
 Počet nástroje jsou k dispozici pro konfiguraci certifikátu klienta a serveru.  
  
 *Winhttpcertcfg.exe* nástroj lze použít ke konfiguraci klientských certifikátů. *Winhttpcertcfg.exe* nástroj je poskytován jako jeden z nástrojů s Windows Server 2003 Resource Kit. Tento nástroj je také k dispozici ke stažení v rámci Windows Server 2003 Resource Kit Tools na www.microsoft.com.  
  
 *Aplikaci HttpCfg.exe* nástroj lze použít ke konfiguraci certifikátů serveru pro <xref:System.Net.HttpListener> třídy. *HttpCfg.exe* nástroj je poskytován jako jeden z nástrojů podpory pro Windows Server 2003 a Windows XP Service Pack 2. *HttpCfg.exe* a dalších nástrojů podpory nejsou nainstalované ve výchozím nastavení v systému Windows Server 2003 nebo Windows XP. V systému Windows Server 2003. Nástroje pro podporu se instalují samostatně z následující složku a soubor na disku CD-ROM systému Windows Server 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Pro použití s Windows XP Service Pack 2 jsou k dispozici ke stažení z www.microsoft.com nástrojů podpory systému Windows XP.  
  
 Zdrojový kód na verzi *HttpCfg.exe* nástroj je k dispozici jako ukázku pomocí sady SDK serveru systému Windows. Zdrojový kód, který *HttpCfg.exe* ukázka je nainstalován ve výchozím nastavení se sítí ukázky jako součást sady Windows SDK v následující složce:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Kromě těchto nástrojů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy poskytuje metody pro načítání certifikát ze systému souborů.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
