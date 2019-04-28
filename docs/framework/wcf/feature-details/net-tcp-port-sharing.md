---
title: Sdílení portů Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: b04266b15f786e3a5a93ac1e9fff1754c397ccd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762749"
---
# <a name="nettcp-port-sharing"></a>Sdílení portů Net.TCP
Windows Communication Foundation (WCF) poskytuje nové založené na TCP síťový protokol (net.tcp://) pro vysoce výkonné komunikaci. WCF také zavádí nové součásti systému, služba Net.TCP Port Sharing umožňující portů net.tcp sdílet mezi více procesy uživatele.  
  
## <a name="background-and-motivation"></a>Na pozadí a motivace  
 Když protokol TCP/IP byla poprvé použita, pouze malý počet aplikačních protokolů provede využít. Čísla portů TCP/IP používá k rozlišení mezi aplikace přidělením jedinečné 16bitové číslo portu do každé aplikační protokol. Třeba přenosy pomocí protokolu HTTP se ještě dnes standardizované pro použití portu TCP 80, SMTP používá TCP port 25 a protokol FTP používá porty TCP, 20 a 21. Jiné aplikace pomocí protokolu TCP jako přenosového mechanismu můžete zvolit jiné číslo portu k dispozici, podle konvence nebo prostřednictvím formální standardizaci.  
  
 Pomocí čísla portů k rozlišení mezi aplikace měla problémy se zabezpečením. Nasazení aplikace, která používá nestandardního portu je často složitá nebo dokonce možné přidělit kvůli přítomnosti podnikové i osobní brány firewall zablokovat provoz TCP na všech portech kromě několika dobře známý vstupní body jsou obecně nakonfigurované brány firewall. Aplikace, které mohou komunikovat přes standardní a známé porty, které již nejsou povolené omezení možností útoku externí. Mnoho síťových aplikací využívají HTTP protokolu, protože většina bran firewall, které jsou nakonfigurované ve výchozím nastavení pro povolení provozu na portu TCP 80.  
  
 HTTP. SYS modelu, ve kterém je provoz k různým aplikacím HTTP multiplexní do jednoho portu TCP se stal standard na platformě Windows. Nabízí společný bod ovládacího prvku pro brány firewall správci zároveň umožní vývojářům aplikací, chcete-li minimalizovat náklady na nasazení vytváření nových aplikací, které můžete provést pomocí sítě.  
  
 Možnost sdílení portů ve více aplikacích HTTP byla dlouhou dobu funkce Internetové informační služby (IIS). Bylo ale jenom se zavedením HTTP. SYS (režimu jádra protokolu naslouchací proces protokolu HTTP) s [!INCLUDE[iis601](../../../../includes/iis601-md.md)] , který tato infrastruktura se plně zobecněn. Platná, protokolu HTTP. SYS umožňuje sdílení portů TCP, který je vyhrazený pro přenosy pomocí protokolu HTTP procesů libovolného uživatele. Tato funkce umožňuje mnoho aplikací HTTP existovat vedle sebe na stejný fyzický počítač v samostatné, izolovaných procesech při sdílení síťové infrastruktury vyžaduje odesílat a přijímat provoz přes TCP port 80. Služba sdílení portů Net.TCP umožňuje stejný typ portu pro net.tcp aplikace pro sdílení obsahu.  
  
## <a name="port-sharing-architecture"></a>Architektura sdílení portu  
 Architektura sdílení portů ve službě WCF má tři hlavní komponenty:  
  
- Pracovní proces: Jakýkoli proces komunikaci přes net.tcp:// pomocí sdílených portů.  
  
- Přenos WCF TCP: Implementuje protokol net.tcp://.  
  
- Služba sdílení portů Net.TCP: Umožňuje sdílet stejný port TCP mnoha pracovních procesů.  
  
 Služba sdílení portů Net.TCP je služba Windows uživatelského režimu, který přijímá připojení net.tcp:// jménem pracovních procesů, které se připojují přes něj. Po přijetí připojení soketu služby Sdílení portů kontroluje příchozí datový proud zpráv získat jeho cílové adresy. Na základě této adresy, služby Sdílení portů může směrovat na datový proud aplikace, takže v konečném důsledku zpracovává.  
  
 Když službu WCF používající sdílení portu net.tcp://, infrastruktura přenosu WCF TCP přímo neotevře soket TCP v procesu aplikace. Místo toho infrastruktury přenosu registruje služby základní adresu identifikátoru URI (Uniform Resource) služba Sdílení portů Net.TCP a čeká na naslouchat zprávám v jeho zastoupení služba Sdílení portů.  Služba sdílení portů odešle zprávy adresované na aplikační službu při jejich doručení.  
  
## <a name="installing-port-sharing"></a>Instalace sdílení portů  
 Služba sdílení portů Net.TCP je k dispozici ve všech operačních systémech, které podporují [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ale služba není ve výchozím nastavení povolena. Jako bezpečnostní opatření musí správce ručně povolit službu Net.TCP Port Sharing před prvním použitím. Služba sdílení portů Net.TCP poskytuje možnosti konfigurace, které vám umožňují pracovat s několika charakteristik síťové sokety vlastníkem služby Sdílení portů. Další informace najdete v tématu [jak: Povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Pomocí aplikace sdílení portů Net.tcp  
 Nejjednodušší způsob, jak použít port net.tcp:// sdílení aplikace WCF je zveřejnit službu pomocí <xref:System.ServiceModel.NetTcpBinding> a následné povolení služby Sdílení portů Net.TCP pomocí <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost.  
  
 Další informace o tom, jak to provést, najdete v části [jak: Konfigurace používání sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Sdílení portů vliv na zabezpečení  
 I když služba Sdílení portů Net.TCP poskytuje vrstvu zpracování mezi aplikacemi a síti, by měl být aplikace, které používají sdílení portů stále zabezpečen, jako kdyby byly přímo naslouchat na síti. Konkrétně aplikace, které používají sdílení portu by se měl vyhodnotit oprávnění procesu, za kterých spuštění. Zvažte spuštění aplikace pomocí předdefinovaným účtem Network Service, který se spouští s minimální sadou procesu oprávnění požadovaná pro síťovou komunikaci.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [Hostování](../../../../docs/framework/wcf/feature-details/hosting.md)
- [Postupy: Konfigurace používání sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Postupy: Povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
