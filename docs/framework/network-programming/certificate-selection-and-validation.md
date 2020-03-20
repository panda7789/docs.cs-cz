---
title: Výběr a ověření certifikátu
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: aea47360ab1bb9dad446a5a7b19a91ea688953c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048752"
---
# <a name="certificate-selection-and-validation"></a>Výběr a ověření certifikátu
Třídy <xref:System.Net> podporují několik způsobů <xref:System.Security.Cryptography.X509Certificates> výběru a ověření připojení ssl (Secure Socket L). Klient může vybrat jeden nebo více certifikátů, které se ověří na serveru. Server může vyžadovat, aby klientský certifikát měl jeden nebo více specifických atributů pro ověřování.  
  
## <a name="definition"></a>Definice  
 Certifikát je datový proud bajtů ASCII, který obsahuje veřejný klíč, atributy (například číslo verze, sériové číslo a datum vypršení platnosti) a digitální podpis od certifikační autority. Certifikáty se používají k navázání šifrovaného připojení nebo k ověření klienta na serveru.  
  
## <a name="client-certificate-selection-and-validation"></a>Výběr a ověření klientského certifikátu  
 Klient může vybrat jeden nebo více certifikátů pro konkrétní připojení SSL. Klientské certifikáty mohou být přidruženy k připojení SSL k webovému serveru nebo poštovnímu serveru SMTP. Klient přidá certifikáty do <xref:System.Security.Cryptography.X509Certificates.X509Certificate> kolekce <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nebo třídy objektů. Použití e-mailu jako příklad, kolekce certifikátů je instancí <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) přidružené k <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> vlastnosti <xref:System.Net.Mail.SmtpClient> třídy. Třída <xref:System.Net.HttpWebRequest> má podobnou <xref:System.Net.HttpWebRequest.ClientCertificates%2A> vlastnost.  
  
 Hlavní rozdíl mezi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy je, že soukromý klíč musí <xref:System.Security.Cryptography.X509Certificates.X509Certificate> být umístěn v úložišti certifikátů pro třídu.  
  
 I v případě, že certifikáty jsou přidány do kolekce a přidruženy k určitému připojení SSL, nebudou na server odeslány žádné certifikáty, pokud o ně server nepožádá. Pokud je pro připojení nastaveno více klientských certifikátů, bude nejlepší použit na základě algoritmu, který bere v úvahu shodu mezi seznamem vystavitelů certifikátů poskytnutých serverem a názvem vystavitele klientského certifikátu.  
  
 Třída <xref:System.Net.Security.SslStream> poskytuje ještě větší kontrolu nad ssl handshake. Klient může určit delegáta, který vybere, který klientský certifikát má být používán.  
  
 Vzdálený server může ověřit, zda je klientský certifikát platný, aktuální a podepsaný příslušnou certifikační autoritou. Delegát může být přidán <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> do vynucení ověření certifikátu.  
  
## <a name="client-certificate-selection"></a>Výběr klientského certifikátu  
 Rozhraní .NET Framework vybere klientský certifikát, který se má serveru prezentovat následujícím způsobem:  
  
1. Pokud byl klientský certifikát předložen dříve serveru, je certifikát při prvním předložení uložen do mezipaměti a znovu použit pro následné žádosti o klientský certifikát.  
  
2. Pokud je přítomen delegát, vždy použijte výsledek z delegáta jako klientský certifikát pro výběr. Pokud je to možné, zkuste použít certifikát uložený v mezipaměti, ale nepoužívejte anonymní pověření uložená v mezipaměti, pokud delegát vrátil hodnotu null a kolekce certifikátů není prázdná.  
  
3. Pokud se jedná o první výzvu pro klientský certifikát, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> rozhraní <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> Framework vyjmenovává certifikáty nebo objekty třídy přidružené k připojení a hledá shodu mezi seznamem vystavitelů certifikátů poskytnutým serverem a názvem vystavitele klientského certifikátu. První certifikát, který odpovídá je odeslán na server. Pokud se žádný certifikát neshoduje nebo je kolekce certifikátů prázdná, bude na server odesláno anonymní pověření.  
  
## <a name="tools-for-certificate-configuration"></a>Nástroje pro konfiguraci certifikátu  
 Pro konfiguraci klientského a serverového certifikátu je k dispozici řada nástrojů.  
  
 Nástroj *Winhttpcertcfg.exe* lze použít ke konfiguraci klientských certifikátů. Nástroj *Winhttpcertcfg.exe* je k dispozici jako jeden z nástrojů sady Windows Server 2003 Resource Kit. Tento nástroj je také k dispozici ke stažení v rámci nástroje sady Windows Server 2003 Resource Kit na [www.microsoft.com](https://www.microsoft.com).  
  
Nástroj *HttpCfg.exe* lze použít ke konfiguraci <xref:System.Net.HttpListener> certifikátů serveru pro třídu. Nástroj *HttpCfg.exe* je k dispozici jako jeden z nástrojů podpory pro systémy Windows Server 2003 a Windows XP Service Pack 2. *Program HttpCfg.exe* a další nástroje podpory nejsou ve výchozím nastavení nainstalovány v systému Windows Server 2003 nebo Windows XP. V systému Windows Server 2003. Nástroje podpory jsou nainstalovány odděleně od následující složky a souboru na disku CD-ROM systému Windows Server 2003:  
  
 \Support\Nástroje\Suptools.msi  
  
 Pro použití se systémem Windows XP Service Pack 2 jsou nástroje podpory systému Windows XP k dispozici ke stažení z [www.microsoft.com](https://www.microsoft.com).  
  
 Zdrojový kód k verzi nástroje *HttpCfg.exe* je také k dispozici jako ukázka sady Windows Server SDK. Zdrojový kód do ukázky *HttpCfg.exe* je ve výchozím nastavení nainstalován s ukázkami sítě jako součást sady Windows SDK pod následující složkou:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Kromě těchto nástrojů, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy poskytuje metody pro načítání certifikátu ze systému souborů.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení v síťovém programování](security-in-network-programming.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
