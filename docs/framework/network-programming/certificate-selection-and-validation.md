---
title: Výběr a ověření certifikátu
description: Přečtěte si několik způsobů, jak třídy System.Net nabízejí výběr a ověření certifikátů pro připojení SSL/TLS.
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: 2dc63413f5c3a5fadd0d62ad61f0b887697c6a45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502649"
---
# <a name="certificate-selection-and-validation"></a>Výběr a ověření certifikátu
<xref:System.Net>Třídy podporují několik způsobů, jak vybrat a ověřit <xref:System.Security.Cryptography.X509Certificates> připojení SSL (Secure Sockets Layer). Klient může vybrat jeden nebo více certifikátů, které se budou ověřovat na server. Server může vyžadovat, aby měl klientský certifikát pro ověřování jeden nebo více specifických atributů.  
  
## <a name="definition"></a>Definice  
 Certifikát je datový proud ASCII bajtů, který obsahuje veřejný klíč, atributy (například číslo verze, sériové číslo a datum vypršení platnosti) a digitální podpis od certifikační autority. Certifikáty slouží k navázání šifrovaného připojení nebo k ověřování klienta na serveru.  
  
## <a name="client-certificate-selection-and-validation"></a>Výběr a ověření klientského certifikátu  
 Klient může vybrat jeden nebo více certifikátů pro konkrétní připojení SSL. Klientské certifikáty je možné přidružit k připojení SSL k webovému serveru nebo poštovnímu serveru SMTP. Klient přidá certifikáty do kolekce <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektů nebo objektů třídy. Použití e-mailu jako příklad, kolekce certifikátů je instance a <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> ) přidružená k <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> vlastnosti <xref:System.Net.Mail.SmtpClient> třídy. <xref:System.Net.HttpWebRequest>Třída má podobnou <xref:System.Net.HttpWebRequest.ClientCertificates%2A> vlastnost.  
  
 Hlavním rozdílem mezi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídou a je, že privátní klíč musí být umístěn v úložišti certifikátů pro <xref:System.Security.Cryptography.X509Certificates.X509Certificate> třídu.  
  
 I když se do kolekce přidají certifikáty a přidruží se k určitému připojení SSL, na server se neodesílají žádné certifikáty, pokud je server nepožaduje. Pokud je u připojení nastaveno více klientských certifikátů, bude na základě algoritmu, který bere v úvahu shodu mezi seznamem vystavitelů certifikátů poskytovaných serverem a názvem vystavitele certifikátu klienta, použita nejlepší z nich.  
  
 <xref:System.Net.Security.SslStream>Třída poskytuje ještě větší kontrolu nad metodou handshake SSL. Klient může určit delegáta pro výběr klientského certifikátu, který se má použít.  
  
 Vzdálený server může ověřit, zda je klientský certifikát platný, aktuální a podepsaný příslušnou certifikační autoritou. Delegát může být přidán do, <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> aby vynutil ověření certifikátu.  
  
## <a name="client-certificate-selection"></a>Výběr klientského certifikátu  
 .NET Framework vybírá klientský certifikát k dispozici na serveru následujícím způsobem:  
  
1. Pokud byl na server dříve předložen klientský certifikát, certifikát se uloží do mezipaměti, když se poprvé předloží a znovu použije pro následné žádosti o certifikát klienta.  
  
2. Pokud je k dispozici delegát, vždy použijte výsledek z delegáta jako certifikát klienta k výběru. Pokud je to možné, zkuste použít certifikát uložený v mezipaměti, ale nepoužívejte anonymní přihlašovací údaje uložené v mezipaměti, pokud delegát vrátil hodnotu null a kolekce certifikátů není prázdná.  
  
3. Pokud je toto první výzvou pro klientský certifikát, rozhraní vytvoří výčet certifikátů v nástroji <xref:System.Security.Cryptography.X509Certificates.X509Certificate> nebo <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objektů tříd přidružených k danému připojení a vyhledá shodu mezi seznamem vystavitelů certifikátů, který poskytuje server a název vystavitele certifikátu klienta. První certifikát, který odpovídá, se pošle na server. Pokud se žádný certifikát neshoduje nebo je kolekce certifikátů prázdná, pošle se na server anonymní přihlašovací údaje.  
  
## <a name="tools-for-certificate-configuration"></a>Nástroje pro konfiguraci certifikátu  
 K dispozici je řada nástrojů pro konfiguraci certifikátu klienta a serveru.  
  
 Nástroj *WinHttpCertCfg. exe* lze použít ke konfiguraci klientských certifikátů. Nástroj *WinHttpCertCfg. exe* je k dispozici jako jeden z nástrojů se sadou Windows Server 2003 Resource Kit. Tento nástroj je k dispozici také jako součást nástrojů pro sadu Windows Server 2003 Resource Kit na adrese [www.Microsoft.com](https://www.microsoft.com).  
  
Nástroj *Httpcfg. exe* lze použít ke konfiguraci certifikátů serveru pro <xref:System.Net.HttpListener> třídu. Nástroj *Httpcfg. exe* je k dispozici jako jeden z nástrojů podpory pro systémy windows Server 2003 a Windows XP Service Pack 2. *Httpcfg. exe* a další nástroje podpory nejsou ve výchozím nastavení nainstalovány v systému windows Server 2003 nebo Windows XP. V systému Windows Server 2003. nástroje podpory se instalují samostatně z této složky a souboru na disk CD-ROM Windows serveru 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Pro použití s Windows XP Service Pack 2 jsou nástroje podpory Windows XP dostupné jako stahování z [www.Microsoft.com](https://www.microsoft.com).  
  
 Zdrojový kód pro verzi nástroje *Httpcfg. exe* je také k dispozici jako ukázka s Windows Server SDK. Zdrojový kód k ukázce *Httpcfg. exe* je ve výchozím nastavení nainstalován s ukázkami sítě jako součást Windows SDK v následující složce:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Kromě těchto nástrojů <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy a poskytují metody pro načtení certifikátu ze systému souborů.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení v síťovém programování](security-in-network-programming.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
