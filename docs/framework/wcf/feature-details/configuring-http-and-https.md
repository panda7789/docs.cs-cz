---
title: Konfigurace HTTP a HTTPS
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 36dbf725dfcd6fefe6482f7de69daea9356d3d07
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087696"
---
# <a name="configuring-http-and-https"></a>Konfigurace HTTP a HTTPS
Služby WCF a klienti mohou komunikovat prostřednictvím protokolu HTTP a HTTPS. Nastavení HTTP/HTTPS se konfigurují pomocí Internetové informační služby (IIS) nebo pomocí nástroje příkazového řádku. Když je služba WCF hostované na nastavení služby IIS protokolu HTTP nebo HTTPS lze nastavit v rámci služby IIS (pomocí nástroje inetmgr.exe). Pokud je služba WCF v místním prostředí, HTTP nebo HTTPS je nakonfigurováno pomocí nástroje příkazového řádku.  
  
 Minimálně můžete nakonfigurovat registraci adresy URL a přidat výjimku brány Firewall pro adresu URL vaší služby budete používat.  
  
 Tento nástroj umožňuje nakonfigurovat nastavení protokolu HTTP závisí na operační systém, který je spuštěna.  
  
 Při spuštění [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], použijte nástroj HttpCfg.exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Tento nástroj nainstaluje automaticky. Při spuštění [!INCLUDE[wxp](../../../../includes/wxp-md.md)], si můžete stáhnout nástroj na [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606). Další informace najdete v tématu [Httpcfg přehled](https://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Při spuštění [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo Windows 7, nakonfigurujte tato nastavení pomocí nástroje Netsh.exe.  
  
## <a name="configuring-namespace-reservations"></a>Konfigurace rezervace Namespace  
 Rezervace Namespace přiřadí oprávnění pro část oboru názvů HTTP URL ke konkrétní skupině uživatelů. Rezervace opravňuje tito uživatelé vytvářet služby, které naslouchat na část oboru názvů. Rezervace se předpony adres URL, to znamená, že rezervace se vztahuje na všechny dílčí cesty rezervaci cesty. Rezervace Namespace povolit dva způsoby, jak použít zástupné znaky. Popisuje dokumentace k rozhraní API serveru HTTP [pořadí rozlišení rozsahu deklarace identity oboru názvů, které se týkají zástupné znaky](https://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Podobně jako požadavek na přidání registrace oboru názvů můžete vytvořit běžící aplikaci. Registrace a rezervace soutěžit o části obor názvů. Rezervace mohou mít přednost před registrace podle pořadí podle rozlišení [pořadí rozlišení rozsahu deklarace identity oboru názvů, které se týkají zástupné znaky](https://go.microsoft.com/fwlink/?LinkId=94841). V takovém případě rezervace blokuje běžící aplikaci příjem požadavků.  
  
### <a name="running-windows-xp-or-server-2003"></a>Běžící Windows XP nebo Server 2003  
 Použití `httpcfg.exe set urlacl` příkaz, který změní rezervace oboru názvů. [Dokumentace nástrojů podpory Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) popisuje syntaxe pro nástroj Httpcfg.exe. Úprava oprávnění rezervace pro část oboru názvů, který vyžaduje oprávnění správce nebo vlastnictví část oboru názvů. Celý obor názvů HTTP na začátku patří do místního správce.  
  
 Následující příklad zobrazuje syntaxi příkazu Httpcfg s `set urlacl` možnost  
  
```  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /aACL  
```  
  
 `/u` Parametr je povinný při použití `set urlacl`. Řetězec, který obsahuje adresu URL plně kvalifikovaný, která slouží jako klíč záznamu pro rezervaci prováděné trvá.  
  
 `/a` Parametr je povinný. také při použití `set urlacl`. Řetězec, který obsahuje seznam řízení přístupu (ACL) ve formě řetězec zabezpečení SDDL Descriptor Definition Language () trvá.  
  
 Následuje příklad použití tohoto příkazu.  
  
```  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Systém Windows Vista, Windows Server 2008 R2 nebo Windows 7  
 Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 nebo Windows 7, pomocí nástroje Netsh.exe. Následuje příklad použití tohoto příkazu.  
  
```  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 Tento příkaz přidá rezervaci adresy URL pro obor názvů zadané adresy URL pro účet doména\uživatel.  Další informace o používání typ příkazu netsh "netsh http přidat urlacl" v příkazovém řádku a stiskněte klávesu enter.  
  
## <a name="configuring-a-firewall-exception"></a>Konfigurace výjimek brány Firewall  
 Při samoobslužné hostování služby WCF, který komunikuje přes protokol HTTP, výjimky musí být přidány do konfigurace brány firewall pro povolení příchozích připojení pomocí konkrétní adresy URL. Další informace najdete v tématu [otevření portu v bráně Windows Firewall (Windows 7)](https://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>Konfigurace certifikátů SSL  
 Protokol vrstvy SSL (Secure Sockets) používá certifikáty na klienta a serveru pro ukládání šifrovacích klíčů. Server poskytuje svůj certifikát SSL, když se vytvoří připojení tak, aby klient lze ověřit identitu serveru. Na serveru můžete také požádat o certifikát od klienta k zajištění vzájemného ověřování obou stranách připojení.  
  
 Certifikáty jsou uloženy v centralizované úložiště podle IP adresy a portu počtu připojení. Speciální IP adresu 0.0.0.0 odpovídá jakékoli IP adresu místního počítače. Všimněte si, že úložiště certifikátů nerozlišuje mezi adresy URL na základě cesty. Služby se stejnou IP adresu a port kombinací musí sdílet certifikáty, i v případě, že cesta v adrese URL pro služby se liší.  
  
 Podrobné pokyny najdete v tématu [postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>Konfigurace seznamu vlastností listenurimode nastavenou IP  
 Rozhraní API HTTP serveru vytvoří vazbu jenom na IP adresu a port jakmile se uživatel zaregistruje adresy URL. Ve výchozím nastavení rozhraní API serveru HTTP váže na port v adrese URL pro všechny IP adresy počítače. Konflikt nastane, pokud aplikace, které nepoužívají rozhraní API serveru HTTP byl dříve spojen daná kombinace IP adresy a portu. Seznam naslouchání IP umožňuje služeb WCF pro existovat současně s aplikací, které používají port pro některé z IP adresy počítače. Pokud IP naslouchání seznam obsahuje všechny položky, rozhraní API HTTP serveru pouze vytvoří vazbu tyto IP adresy, které určuje seznamu. Úprava seznamu naslouchání IP vyžaduje oprávnění správce.  
  
### <a name="running-windows-xp-or-server-2003"></a>Běžící Windows XP nebo Server 2003  
 Použijte nástroj httpcfg k úpravě seznamu naslouchání IP, jak je znázorněno v následujícím příkladu. [Dokumentace nástrojů podpory Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) popisuje syntaxe pro nástroj httpcfg.exe.  
  
```  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Systémem Windows Vista nebo Windows 7  
 Úprava seznamu naslouchání IP použijte nástroj netsh, jak je znázorněno v následujícím příkladu.  
  
```  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Další nastavení konfigurace  
 Při použití <xref:System.ServiceModel.WSDualHttpBinding>, připojení klienta používá výchozí hodnoty, které jsou kompatibilní s rezervace oboru názvů a brány Windows firewall. Pokud budete chtít upravit základní adresu duální připojení klienta, také musíte nakonfigurovat nastavení protokolu HTTP na straně klienta tak, aby odpovídala nové adrese.  
  
 Rozhraní API HTTP Server má nastavení některé pokročilé konfigurace, které nejsou k dispozici prostřednictvím HttpCfg. Tato nastavení se zachovají v registru a platí pro všechny aplikace spuštěné v systémech, které používají rozhraní API serveru HTTP. Informace o těchto nastaveních najdete v tématu [nastavení registru Http.sys pro službu IIS](https://go.microsoft.com/fwlink/?LinkId=94843). Většinu uživatelů by neměl muset tato nastavení změnit.  
  
## <a name="issues-specific-to-windows-xp"></a>Problémy specifické pro Windows XP  
 Služba IIS nepodporuje sdílení portů ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Pokud je spuštěna služba IIS a služby WCF se pokusí použít obor názvů se stejný port, nepodaří spustit službu WCF. Služba IIS a WCF, které oba ve výchozím nastavení používá port 80. Změňte přiřazení portů pro jednu ze služeb nebo pomocí seznamu naslouchání IP k přiřazení služby WCF na síťový adaptér není používaný službou IIS. Služba IIS 6.0 a novějším mají upravený tak, aby pomocí rozhraní API serveru HTTP.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
