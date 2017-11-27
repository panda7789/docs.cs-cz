---
title: "Principy WebRequest problémy a výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d29321297a880ca961805687e51c7bb63f70ffbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>Principy WebRequest problémy a výjimek
<xref:System.Net.WebRequest>a jejich odvozené třídy (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, a <xref:System.Net.FileWebRequest>) generování výjimek signál podmínku neobvyklé. Někdy není zřejmé řešení těchto problémů.  
  
## <a name="solutions"></a>Řešení  
 Zkontrolujte <xref:System.Net.WebException.Status%2A> vlastnost <xref:System.Net.WebException> ke zjištění problému. Následující tabulka uvádí některé možná řešení a několik hodnoty stavu.  
  
|Stav|Podrobnosti|Řešení|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> -nebo-<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|Došlo k potížím s základní soketu. Připojení byl resetován.|Připojte se znovu a odešlete požadavek znovu.<br /><br /> Ujistěte se, že je nainstalováno nejnovější aktualizaci service pack.<br /><br /> Zvýšit hodnotu <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> vlastnost.<br /><br /> Nastavit <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> k `false`.<br /><br /> Zvýšit číslo s maximální počet připojení <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost.<br /><br /> Zkontrolujte konfiguraci proxy serveru.<br /><br /> Pokud pomocí protokolu SSL, ujistěte se, že proces server má oprávnění k přístupu k úložišti certifikátů.<br /><br /> Pokud odesílá velké množství dat, nastavte <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> k `false`.|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|Nebylo možné ověřit certifikát serveru.|Zkuste otevřít identifikátor URI pomocí Internet Exploreru. Vyřešte všechny výstrahy zabezpečení aplikace Internet Explorer zobrazí. Pokud nelze vyřešit výstrahu zabezpečení, pak můžete vytvořit třídu Zásady certifikátů, která implementuje <xref:System.Net.ICertificatePolicy> , který vrací `true`, možností a předejte ji do <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.<br /><br /> Odkazovat na [http://support.microsoft.com/?id=823177](http://go.microsoft.com/fwlink/?LinkID=179653).<br /><br /> Ujistěte se, že certifikát certifikační autority, který podepsaný certifikát serveru se přidá do seznamu Důvěryhodné certifikační autority v aplikaci Internet Explorer.<br /><br /> Ujistěte se, že název hostitele v adrese URL odpovídá běžný název certifikátu serveru.|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|Došlo k chybě v transakci SSL, nebo došlo k potížím certifikátu.|Rozhraní .NET Framework verze 1.1 podporuje jenom SSL verze 3.0. Pokud server používá pouze protokol TLS verze 1.0 nebo SSL verze 2.0, je vyvolána výjimka. Upgrade na rozhraní .NET Framework verze 2.0 a nastavit <xref:System.Net.ServicePointManager.SecurityProtocol%2A> tak, aby odpovídaly serveru.<br /><br /> Klientský certifikát byl podepsán certifikační autority (CA), že server nedůvěřuje. Certifikát Certifikační autority nainstalujte na server. V tématu [http://support.microsoft.com/?id=332077](http://go.microsoft.com/fwlink/?LinkID=179654).<br /><br /> Ujistěte se, že máte nejnovější aktualizaci service pack nainstalována.|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|Spojení bylo přerušeno.|Brány firewall nebo proxy server blokuje připojení. Upravte brány firewall nebo proxy server, aby bylo připojení.<br /><br /> Explicitně určit <xref:System.Net.WebProxy> v aplikaci klienta voláním <xref:System.Net.WebProxy> – konstruktor (WebServiceProxyClass.Proxy = nové WebProxy ([http://server:80](http://server/), true)).<br /><br /> Spusťte Filemon nebo Regmon zajistit, že identitu pracovního procesu musí mít potřebná oprávnění k přístupu k WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache nebo HKLM\System\CurrentControlSet\Services\WinSock2.|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|Služby Domain Name Service nešlo přeložit název hostitele.|Konfigurace proxy serveru správně. V tématu [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Ujistěte se, jestli žádný nainstalovaný antivirový software nebo brána firewall neblokuje připojení.|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<xref:System.Net.WebRequest.Abort%2A>byl názvem, nebo se chyba došlo k chybě.|Tento problém může být způsobeno pod velkou zátěží na straně klienta nebo serveru. Snižte zatížení.<br /><br /> Zvýšit <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> nastavení.<br /><br /> V tématu [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) k úpravě nastavení výkonu webové služby.|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|Aplikace se pokusil o zápis do soketu, který již byl uzavřen.|Klient nebo server je přetížen. Snižte zatížení.<br /><br /> Zvýšit <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> nastavení.<br /><br /> V tématu [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) k úpravě nastavení výkonu webové služby.|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|Nastavený limit (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>) ve zprávě byla překročena délka.|Zvýšit hodnotu <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> vlastnost.|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|Služby Domain Name Service nešlo přeložit název hostitele proxy serveru.|Konfigurace proxy serveru správně. V tématu [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).<br /><br /> Platnost <xref:System.Net.HttpWebRequest> používat žádný proxy server nastavením <xref:System.Net.HttpWebRequest.Proxy%2A> vlastnost `null`.|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|Odpověď ze serveru není platná odpověď HTTP. K tomuto problému dochází, když rozhraní .NET Framework zjistí, že odpověď serveru není v souladu s HTTP 1.1 RFC. Tomuto problému může dojít, pokud odpověď obsahuje nesprávný hlavičky nebo nesprávné záhlaví oddělovače. Dokumentu RFC 2616 definuje HTTP 1.1 a platný formát pro odpověď ze serveru. Další informace najdete v tématu [http://www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388).|Získejte trasování sítě transakce a prověří hlavičky v odpovědi.<br /><br /> Pokud vaše aplikace vyžaduje odpověď serveru bez analýza (může se jednat o problém zabezpečení), sada `useUnsafeHeaderParsing` k `true` v konfiguračním souboru. V tématu [ \<httpWebRequest > elementu (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.Dns>
