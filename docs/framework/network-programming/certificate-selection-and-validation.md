---
title: Výběr a ověření certifikátu
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fe3b10e17c3cdf181f0b33b4305008655047fb0f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139264"
---
# <a name="certificate-selection-and-validation"></a>Výběr a ověření certifikátu
<xref:System.Net> Třídy podporují několik způsobů, jak vybrat a ověřit <xref:System.Security.Cryptography.X509Certificates> pro připojení vrstvy SSL (Secure Socket). Klienta můžete vybrat jeden nebo více certifikátů ke svému ověření serveru. Server může vyžadovat, že klientský certifikát mají jeden nebo více konkrétních atributů pro ověřování.  
  
## <a name="definition"></a>Definice  
 Certifikát je proud bajtů ASCII, který obsahuje veřejný klíč, atributů (jako je číslo verze, sériové číslo a datum vypršení platnosti) a digitální podpis od certifikační autority. Certifikáty se používají k navázání šifrovaného připojení a ověření klienta na server.  
  
## <a name="client-certificate-selection-and-validation"></a>Výběr certifikátu klienta a ověření  
 Klienta můžete vybrat jeden nebo více certifikátů pro konkrétní připojení protokolem SSL. Klientské certifikáty lze přidružit připojení SSL na webovém serveru nebo poštovnímu serveru SMTP. Klient přidá do kolekce certifikátů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy objektů. Jako příklad použijeme e-mailu, kolekci certifikátů je instance <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) přidružené k <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> vlastnost <xref:System.Net.Mail.SmtpClient> třídy. <xref:System.Net.HttpWebRequest> Třídy je podobná <xref:System.Net.HttpWebRequest.ClientCertificates%2A> vlastnost.  
  
 Hlavní rozdíl mezi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třída je, že privátní klíč se musí nacházet v úložišti certifikátů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> třídy.  
  
 Přestože certifikáty jsou přidána do kolekce a přidružené k určité připojení SSL, žádné certifikáty, se odešlou na server, pokud je server vyžádá. Pokud více klientských certifikátů jsou nastavené na připojení, podle to nejlepší, který bude použit algoritmus, který bere v úvahu shoda mezi seznam vystavitelů certifikátů, které jsou k dispozici na serveru a název vystavitele certifikátu klienta.  
  
 <xref:System.Net.Security.SslStream> Třída poskytuje ještě větší kontrolu nad metody handshake SSL. Klienta můžete zadat delegáta pro výběr jaký klientský certifikát k použití.  
  
 Vzdálený server můžete ověřit, že klientský certifikát je platný, aktuální a podepsaný certifikační autoritou odpovídající. Delegát lze přidat do <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> k vynucení ověřování certifikátu.  
  
## <a name="client-certificate-selection"></a>Výběru klientského certifikátu  
 Rozhraní .NET Framework zvolí klientský certifikát k dispozici server má následující omezení:  
  
1.  Pokud klientský certifikát byl dříve předloženým serveru, certifikát je uložen do mezipaměti při prvním zobrazí a je znovu použít pro další klientské žádosti o certifikát.  
  
2.  Pokud delegát je k dispozici, vždy použijte výsledek z delegáta jako na klientský certifikát a vyberte. Zkuste použít certifikát uložený v mezipaměti, pokud je to možné, ale nepoužívejte anonymní přihlašovací údaje v mezipaměti, pokud delegát vrátila hodnotu null a kolekci certifikátů není prázdný.  
  
3.  Pokud je toto první výzva pro klientský certifikát, rozhraní zobrazí certifikáty v <xref:System.Security.Cryptography.X509Certificates.X509Certificate> nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy objekty přidružené k připojení k vyhledávání shody mezi seznam vystavitelů certifikátů, které jsou poskytované Server a název vystavitele certifikátu klienta. První certifikát, který odpovídá je odeslána na server. Pokud žádné shody certifikátu nebo kolekci certifikátů je prázdný, pak je anonymní přihlašovací údaje odeslány na server.  
  
## <a name="tools-for-certificate-configuration"></a>Nástroje pro konfiguraci certifikátu  
 Různé nástroje jsou k dispozici pro konfiguraci certifikátu klienta a serveru.  
  
 *Winhttpcertcfg.exe* nástroj můžete použít ke konfiguraci klientských certifikátů. *Winhttpcertcfg.exe* nástroj je k dispozici jako jedna nástrojů se službou Windows Server 2003 Resource Kit. Tento nástroj je k dispozici ke stažení Windows Server 2003 Resource Kit Tools v rámci [www.microsoft.com](https://www.microsoft.com).  
  
*HttpCfg.exe* nástroj je možné nakonfigurovat certifikáty serveru <xref:System.Net.HttpListener> třídy. *HttpCfg.exe* nástroj je poskytován jako jeden z nástrojů podpory pro Windows Server 2003 a Windows XP Service Pack 2. *HttpCfg.exe* a dalších nástrojů podpory nejsou nainstalované ve výchozím nastavení v systému Windows Server 2003 nebo Windows XP. V systému Windows Server 2003. Podpora nástroje se instalují samostatně z následující složky a souboru na disku CD-ROM systému Windows Server 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Pro použití s Windows XP Service Pack 2, jsou k dispozici ke stažení z nástrojů podpory Windows XP [www.microsoft.com](https://www.microsoft.com).  
  
 Zdrojový kód na verzi *HttpCfg.exe* nástroj je k dispozici jako ukázku Windows SDK serveru. Zdrojový kód *HttpCfg.exe* ukázka nainstalovaný ve výchozím nastavení s ukázkami sítě jako součást sady Windows SDK v následující složce:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Kromě těchto nástrojů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy poskytuje metody pro načítání certifikátu ze systému souborů.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
