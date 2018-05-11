---
title: Konfigurace HTTP a HTTPS
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: ed9c7a444018e7c5e9ac00de82133cce633fac93
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="configuring-http-and-https"></a>Konfigurace HTTP a HTTPS
Služby WCF a klienti mohou komunikovat prostřednictvím protokolu HTTP a HTTPS. Konfigurace nastavení protokolu HTTP nebo HTTPS pomocí Internetové informační služby (IIS), nebo pomocí nástroje příkazového řádku. Když je služba WCF hostované v části Nastavení služby IIS protokolu HTTP nebo HTTPS lze konfigurovat v rámci služby IIS (pomocí nástroje inetmgr.exe). Pokud služby WCF s vlastním hostováním, HTTP nebo HTTPS je nakonfigurováno pomocí nástroje příkazového řádku.  
  
 V minimálním budete potřebovat ke konfiguraci registrace adresy URL a přidat výjimku brány Firewall pro adresu URL služby, které se budou používat.  
  
 Nástroj, který slouží ke konfiguraci nastavení HTTP závisí na operačním systému, které v počítači.  
  
 Při spuštění [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Tento nástroj automaticky nainstaluje. Při spuštění [!INCLUDE[wxp](../../../../includes/wxp-md.md)], si můžete stáhnout nástroj na [nástrojů podpory systému Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606). Další informace najdete v tématu [Httpcfg přehled](http://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Při spuštění [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo Windows 7, tato nastavení lze nakonfigurovat pomocí nástroje Netsh.exe.  
  
## <a name="configuring-namespace-reservations"></a>Konfigurace Namespace rezervací  
 Namespace rezervace přiřadí práva pro část oboru názvů URL protokolu HTTP pro konkrétní skupinu uživatelů. Rezervace dává uživatelům práva k vytvoření služeb, které čekají na část oboru názvů. Rezervace jsou předpony adres URL, což znamená, že rezervace se vztahuje na všechny dílčí cesty rezervace cesty. Namespace rezervace povolit dva způsoby, jak použít zástupné znaky. Popisuje dokumentaci rozhraní API serveru HTTP [pořadí rozlišení mezi deklarace oboru názvů, které zahrnují zástupné znaky](http://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Spuštěné aplikace můžete vytvořit podobné žádost o přidání registrace oboru názvů. Registrace a rezervace pokouší o části oboru názvů. Rezervace může mají přednost před registrace podle pořadí v řešení [pořadí rozlišení mezi deklarace oboru názvů, které zahrnují zástupné znaky](http://go.microsoft.com/fwlink/?LinkId=94841). V takovém případě rezervace blokuje běžící aplikaci příjem požadavků.  
  
### <a name="running-windows-xp-or-server-2003"></a>Spuštěný systém Windows XP nebo Server 2003  
 Použití `httpcfg.exe set urlacl` příkazu změníte vyhrazení oboru názvů. [Dokumentace nástrojů podpory systému Windows](http://go.microsoft.com/fwlink/?LinkId=94840) vysvětluje syntaxe pro nástroj Httpcfg.exe. Úprava rezervace práva pro část oboru názvů vyžaduje oprávnění správce nebo vlastnictví část oboru názvů. Celý obor názvů HTTP na začátku patří do místního správce.  
  
 Následující ukazuje syntaxi příkazu Httpcfg s `set urlacl` možnost  
  
```  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /aACL  
```  
  
 `/u` Parametr je povinný při použití `set urlacl`. Řetězec, který obsahuje adresu URL plně kvalifikovaný, která slouží jako klíč záznam pro rezervaci prováděné trvá.  
  
 `/a` Parametr je také nutný při použití `set urlacl`. Jak dlouho trvá řetězec, který obsahuje seznam řízení přístupu (ACL) ve formě řetězce zabezpečení SDDL Descriptor Definition Language ().  
  
 Následuje příklad použití tohoto příkazu.  
  
```  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Systém Windows Vista, Windows Server 2008 R2 nebo Windows 7  
 Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 nebo Windows 7, pomocí nástroje Netsh.exe. Následuje příklad použití tohoto příkazu.  
  
```  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 Tento příkaz přidá rezervaci adresy URL pro obor názvů zadané adresy URL pro účet doména\uživatel.  Další informace o používání daný typ příkazu netsh "netsh http přidat urlacl" v příkazovém řádku a stiskněte klávesu zadejte.  
  
## <a name="configuring-a-firewall-exception"></a>Konfigurace výjimek brány Firewall  
 Když vlastní hostování služby WCF, který komunikuje přes protokol HTTP, musí být přidaný výjimku pro konfiguraci brány firewall umožňuje příchozí připojení, pomocí konkrétní adresu URL. Další informace najdete v tématu [otevřít port v bráně Windows Firewall (Windows 7)](http://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>Konfigurace certifikátů protokolu SSL  
 Protokol Secure Sockets Layer (SSL) používá certifikáty na klientovi a serveru pro ukládání šifrovacích klíčů. Server poskytuje svůj certifikát SSL, když je vytvořeno připojení, takže klient může ověřit identitu serveru. Server můžete také žádost o certifikát od klienta k zajištění vzájemného ověřování obou koncích připojení.  
  
 Certifikáty jsou uložené v centralizované úložiště podle IP adresy a portu počet připojení. Speciální IP adresu 0.0.0.0 odpovídá jakékoli IP adresu pro místní počítač. Všimněte si, že úložiště certifikátů nerozlišuje adresy URL na základě cesty. Služeb se stejnou IP adresu a port kombinací musejí sdílet certifikáty, i v případě, že složka v adrese URL pro služby se liší.  
  
 Podrobné pokyny najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>Konfigurace seznamu naslouchání IP  
 Rozhraní API serveru HTTP se pouze váže k adresu IP a portu, jakmile se uživatel zaregistruje adresu URL. Ve výchozím nastavení rozhraní API serveru HTTP vytvoří vazbu k portu v adrese URL pro všechny IP adresy počítače. Dojde ke konfliktu, pokud má aplikace, která nepoužívá rozhraní API serveru HTTP dříve spojen tuto kombinaci IP adresy a portu. Seznam adres IP naslouchání umožňuje službám WCF existovat společně s aplikací, které používají port pro některé z IP adresy počítače. Pokud IP naslouchání seznam obsahuje všechny položky, rozhraní API serveru HTTP pouze sváže tyto IP adresy, které určuje, v seznamu. Úprava seznamu naslouchání IP vyžaduje oprávnění správce.  
  
### <a name="running-windows-xp-or-server-2003"></a>Spuštěný systém Windows XP nebo Server 2003  
 Pomocí nástroje httpcfg upravit naslouchání seznam adres IP, jak je znázorněno v následujícím příkladu. [Dokumentace nástrojů podpory systému Windows](http://go.microsoft.com/fwlink/?LinkId=94840) vysvětluje syntaxe pro nástroj httpcfg.exe.  
  
```  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Systém Windows Vista nebo Windows 7  
 Pomocí nástroje netsh upravit naslouchání seznam adres IP, jak je znázorněno v následujícím příkladu.  
  
```  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Další nastavení konfigurace  
 Při použití <xref:System.ServiceModel.WSDualHttpBinding>, připojení klienta používá výchozí nastavení, které jsou kompatibilní s rezervace obor názvů a brány Windows firewall. Pokud zvolíte možnost upravit základní adresu klienta duální připojení, potom také nakonfigurujte tato nastavení protokolu HTTP na straně klienta tak, aby odpovídala nové adresy.  
  
 Rozhraní API serveru protokolu HTTP má některá nastavení Pokročilé konfigurace, které nejsou k dispozici prostřednictvím HttpCfg. Tato nastavení se udržují v registru a platí pro všechny aplikace spuštěné na systémy, které používají rozhraní API serveru HTTP. Informace o těchto nastaveních najdete v tématu [nastavení registru Http.sys pro službu IIS](http://go.microsoft.com/fwlink/?LinkId=94843). Většina uživatelů by neměl muset změnit tato nastavení.  
  
## <a name="issues-specific-to-windows-xp"></a>Potíže specifické pro systém Windows XP  
 Služba IIS nepodporuje sdílení portů na [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Pokud je spuštěna služba IIS a služby WCF se pokusí použít obor názvů s stejný port, služby WCF se nepodaří spustit. Služba IIS a WCF, které obě výchozích nastavení používat port 80. Buď změňte přiřazení portů pro jednu ze služeb nebo pomocí seznamu naslouchání IP můžete přiřadit služby WCF na síťový adaptér nepoužívá se službou IIS. Služby IIS 6.0 a novějším mají lepší využití rozhraní API serveru HTTP.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
