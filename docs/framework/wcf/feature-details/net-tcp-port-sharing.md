---
title: Sdílení portů Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: 37c3d7580b48552b841823933958267cea815fab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497149"
---
# <a name="nettcp-port-sharing"></a>Sdílení portů Net.TCP
Windows Communication Foundation (WCF) poskytuje nový protokol sítě založené na protokolu TCP (net.tcp://) pro komunikaci s vysokým výkonem. WCF také zavádí novou součást systému, služba Net.TCP Port Sharing umožňující portů net.tcp ke sdílení více procesy uživatele.  
  
## <a name="background-and-motivation"></a>Pozadí a motivace  
 Když protokol TCP/IP byla poprvé použita, pouze malý počet aplikací protokoly provedené jeho použití. TCP/IP používá k rozlišení mezi aplikace přidělením jedinečné 16bitové číslo portu pro každý protokol aplikace čísla portů. Například přenos HTTP se ještě dnes standardizované využívá TCP port 80, SMTP používá TCP port 25 a server FTP použije porty TCP 20 a 21. Jiné aplikace pomocí protokolu TCP přenos můžete si vybrat jiný dostupný port číslo podle konvence nebo prostřednictvím formální standardizace.  
  
 Rozlišovat mezi jednotlivými aplikacemi pomocí čísla portů měly problémy se zabezpečením. Obecně jsou nakonfigurované brány firewall k blokování provozu TCP na všech portech s výjimkou pár dobře známé vstupním bodům, takže nasazení aplikace, která používá nestandardním portu, je často složité nebo dokonce možné z důvodu přítomnosti podnikových a osobní brány firewall. Aplikace, které mohou komunikovat přes standardní, dobře známé porty, které jsou již povoleny, redukovat prostor pro útok externí. Mnoho síťových aplikací využívat HTTP protokolu, protože většinu bran firewall jsou nakonfigurované ve výchozím nastavení, aby povolovala přenosy na portu TCP 80.  
  
 HTTP. SYS modelu, ve kterém je provoz pro mnoho různých aplikací HTTP multiplexní na jediný port TCP se stal standard na platformě Windows. To poskytuje společný bod ovládacího prvku pro brány firewall správci současně vývojáři aplikace k minimalizovat náklady na nasazení vytváření nové aplikace, které můžete provést pomocí sítě.  
  
 Sdílení portů napříč různými aplikacemi HTTP se dlouho funkce Internetové informační služby (IIS). Bylo ale pouze se zavedením HTTP. SYS (režimu jádra protokolu naslouchací proces protokolu HTTP) s [!INCLUDE[iis601](../../../../includes/iis601-md.md)] který byla tato infrastruktura plně zobecněn. V platit, HTTP. SYS umožní libovolný uživatelský procesy sdílet porty TCP, který je vyhrazený pro provoz protokolu HTTP. Tato funkce umožňuje mnoho aplikací HTTP nacházet na stejný fyzický počítač v samostatné, izolované procesy při sdílení síťové infrastruktury vyžaduje odesílat a přijímat provoz přes TCP port 80. Služba Net.TCP Port Sharing umožňuje stejný typ port pro net.tcp aplikace pro sdílení.  
  
## <a name="port-sharing-architecture"></a>Architektura sdílení portů  
 Architektura sdílení portů ve službě WCF má tři hlavní součásti:  
  
-   Pracovní proces: Jakýkoli proces komunikaci přes net.tcp:// pomocí sdíleného portů.  
  
-   Přenos WCF TCP: implementuje protokol net.tcp://.  
  
-   Služba sdílení portů Net.TCP: Umožňuje mnoha pracovních procesů sdílet stejný port TCP.  
  
 Služba Net.TCP Port Sharing je služba Windows uživatelského režimu, který přijímá připojení net.tcp:// jménem pracovních procesů, které se připojují přes něj. Pokud připojení soketu dorazí, zkontroluje služby Sdílení portů příchozí datový proud zpráv získat jeho cílové adresy. Na základě na tuto adresu, můžete služby Sdílení portů k aplikaci, která nakonec procesy směrovat datový proud.  
  
 Pokud službu WCF používající sdílení portu net.tcp://, infrastruktura přenosu WCF TCP přímo neotevře soketu TCP v aplikačním procesu. Místo toho infrastruktura přenosu zaregistruje základní adresu identifikátoru URI (Uniform Resource) se služba Net.TCP Port Sharing a čeká na služby přijímat zprávy jeho jménem sdílení portů.  Služby Sdílení portů expeduje zprávy adresované do služba aplikace, když dorazí.  
  
## <a name="installing-port-sharing"></a>Instalace sdílení portů  
 Služba Net.TCP Port Sharing je k dispozici ve všech operačních systémech, které podporují [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ale služba není ve výchozím nastavení povolena. Jako bezpečnostní opatření musí správce ručně povolit službu Net.TCP Port Sharing před první použití. Služba Net.TCP Port Sharing zpřístupní možnosti konfigurace, které umožňují pracovat s několik vlastností sítě soketů, které vlastní služby Sdílení portů. Další informace najdete v tématu [postupy: povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Použití v aplikaci pro sdílení portů Net.tcp  
 Nejjednodušší způsob, jak používat port net.tcp:// sdílení v aplikace WCF je vystavit služby pomocí <xref:System.ServiceModel.NetTcpBinding> a potom povolit služby Sdílení portů Net.TCP pomocí <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost.  
  
 Další informace o tom, jak to udělat najdete v tématu [postupy: Konfigurace používání sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Sdílení portů vliv na zabezpečení  
 I když služba Net.TCP Port Sharing zajišťuje vrstvu zpracování mezi aplikacemi a sítě, musí být aplikace, které používají sdílení portů stále zabezpečený, jako kdyby byly přímo naslouchání v síti. Aplikace, které používají sdílení portů konkrétně byste měli zvážit, proces oprávnění, pod kterým poběží. Zvažte spuštění vaší aplikace pomocí vestavěný účet Síťová služba, který se spouští s minimálním počtem proces oprávnění požadovaná pro síťovou komunikaci.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)  
 [Hostování](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Postupy: Konfigurace používání sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)  
 [Postupy: Povolení služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
