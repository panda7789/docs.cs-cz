---
title: Sdílení portů Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: d9c6caa546d9f31f4e68b850dc1b1e750da2e93c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598759"
---
# <a name="nettcp-port-sharing"></a>Sdílení portů Net.TCP
Windows Communication Foundation (WCF) poskytuje nový síťový protokol založený na TCP (NET. TCP://) pro vysoce výkonné komunikace. Služba WCF také zavádí novou součást systému, což je služba sdílení portů Net. TCP, která umožňuje sdílení portů Net. TCP napříč několika uživatelskými procesy.  
  
## <a name="background-and-motivation"></a>Pozadí a motivace  
 Po prvním zavedení protokolu TCP/IP se používá jenom malý počet aplikačních protokolů. Protokol TCP/IP používal čísla portů k rozlišení mezi aplikacemi tím, že každému aplikačnímu protokolu přiřadí jedinečné 16bitové číslo portu. Například provoz protokolu HTTP dnes je standardizován na použití portu TCP 80, protokol SMTP používá port TCP 25 a FTP používá porty TCP 20 a 21. Další aplikace používající protokol TCP jako přenos můžou zvolit jiné dostupné číslo portu, a to buď podle konvence, nebo prostřednictvím formální normalizace.  
  
 Použití čísel portů k rozlišení mezi aplikacemi mělo problémy se zabezpečením. Brány firewall jsou obecně nakonfigurované pro blokování provozu TCP na všech portech s výjimkou několika známých vstupních bodů, takže nasazení aplikace, která používá nestandardní port, je často komplikované nebo dokonce znemožňuje vzhledem k přítomnosti podnikových a osobních bran firewall. Aplikace, které mohou komunikovat přes standardní, dobře známé porty, které jsou již povoleny, omezují vnější plochu pro útok. Mnohé síťové aplikace využívají protokol HTTP, protože většina bran firewall je ve výchozím nastavení nakonfigurovaná tak, aby umožňovala provoz na portu TCP 80.  
  
 Protokol HTTP. Model SYS, ve kterém je v rámci platformy Windows na jednom portu TCP multiplexovaná provoz pro mnoho různých aplikací HTTP. Tato možnost poskytuje běžný bod řízení pro Správce brány firewall a umožňuje vývojářům aplikací minimalizovat náklady na nasazení nových aplikací, které mohou využívat síť.  
  
 Možnost sdílení portů mezi více aplikacemi HTTP byla dlouhodobě funkcí Internetová informační služba (IIS). Ale byl jenom s úvodem protokolu HTTP. SYS (naslouchací proces protokolu HTTP v režimu jádra) se službou IIS 6,0, že tato infrastruktura byla plně zobecněna. V důsledku toho HTTP. SYS umožňuje libovolným uživatelským procesům sdílet porty TCP vyhrazené pro přenosy HTTP. Tato možnost umožňuje mnoha aplikacím HTTP souběžně ve stejném fyzickém počítači v samostatných izolovaných procesech během sdílení síťové infrastruktury vyžadované pro odesílání a příjem provozu přes port TCP 80. Služba sdílení portů Net. TCP umožňuje stejný typ sdílení portů pro aplikace NET. TCP.  
  
## <a name="port-sharing-architecture"></a>Architektura sdílení portů  
 Architektura sdílení portů ve službě WCF má tři hlavní součásti:  
  
- Pracovní proces: jakýkoli proces, který komunikuje přes NET. TCP://používá sdílené porty.  
  
- Přenos WCF TCP: implementuje NET. TCP://Protocol.  
  
- Služba sdílení portů Net. TCP: umožňuje spoustě pracovních procesů sdílet stejný port TCP.  
  
 Služba sdílení portů Net. TCP je služba systému Windows v uživatelském režimu, která přijímá připojení NET. TCP://za pracovní procesy, které se k ní připojují. Když připojení soketu dorazí, služba sdílení portů zkontroluje datový proud příchozích zpráv, aby získal jeho cílovou adresu. Na základě této adresy může služba sdílení portů směrovat datový proud do aplikace, která ji nakonec zpracuje.  
  
 Když se otevře služba WCF, která používá sdílení NET. TCP://port, infrastruktura přenosu WCF TCP přímo neotevře soket TCP v procesu aplikace. Místo toho zaregistruje přenosová infrastruktura základní adresu identifikátoru URI (Uniform Resource Identifier) služby pomocí služby sdílení portů Net. TCP a počká, až služba sdílení portů naslouchat zprávám v jejím zastoupení.  Služba sdílení portů odesílá zprávy adresované službě Application Service při jejich doručení.  
  
## <a name="installing-port-sharing"></a>Instalace sdílení portů  
 Služba sdílení portů Net. TCP je dostupná ve všech operačních systémech, které podporují WinFX, ale služba není ve výchozím nastavení povolená. Z důvodu zabezpečení musí správce ručně povolit službu sdílení portů Net. TCP před prvním použitím. Služba sdílení portů Net. TCP zpřístupňuje možnosti konfigurace, které umožňují manipulovat s několika charakteristikami síťových soketů vlastněných službou Sdílení portů. Další informace najdete v tématu [Postup: povolení služby sdílení portů Net. TCP](how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Používání sdílení portů Net. TCP v aplikaci  
 Nejjednodušší způsob, jak použít sdílení NET. TCP://port v aplikaci WCF, je vystavit službu pomocí <xref:System.ServiceModel.NetTcpBinding> a pak povolit službu sdílení portů Net. TCP pomocí <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> Vlastnosti.  
  
 Další informace o tom, jak to provést, naleznete v tématu [How to: Configure a WCF Service to use sdílení portů](how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Vliv sdílení portů na zabezpečení  
 I když služba sdílení portů Net. TCP poskytuje vrstvu zpracování mezi aplikacemi a sítí, měly by být aplikace, které používají sdílení portů, i nadále zabezpečeny, jako by přímo naslouchaly v síti. Konkrétně aplikace, které používají sdílení portů, by měly vyhodnotit oprávnění procesu, na základě kterých se spouštějí. Zvažte spuštění aplikace pomocí integrovaného účtu síťové služby, který je spuštěn s minimální sadou oprávnění procesu vyžadovaných pro síťovou komunikaci.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace služby sdílení portů Net.TCP](configuring-the-net-tcp-port-sharing-service.md)
- [Hosting](hosting.md)
- [Postupy: Konfigurace používání sdílení portů ve službě WCF](how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Postupy: Povolení služby sdílení portů Net.TCP](how-to-enable-the-net-tcp-port-sharing-service.md)
