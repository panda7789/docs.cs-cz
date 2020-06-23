---
title: Sdílení portů Net.TCP
description: Přečtěte si o protokolu založeném na protokolu TCP pro vysoce výkonné komunikace a službě, která umožňuje sdílení portů napříč několika uživatelskými procesy ve službě WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: a9579c588906f509dd835d3c9b25571495d147e0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245242"
---
# <a name="nettcp-port-sharing"></a>Sdílení portů Net.TCP
Windows Communication Foundation (WCF) poskytuje nový síťový protokol založený na TCP (NET. TCP://) pro vysoce výkonné komunikace. Služba WCF také zavádí novou součást systému, což je služba sdílení portů Net. TCP, která umožňuje sdílení portů Net. TCP napříč několika uživatelskými procesy.  
  
## <a name="background-and-motivation"></a>Pozadí a motivace  
 Po prvním zavedení protokolu TCP/IP se používá jenom malý počet aplikačních protokolů. Protokol TCP/IP používal čísla portů k rozlišení mezi aplikacemi tím, že každému aplikačnímu protokolu přiřadí jedinečné 16bitové číslo portu. Například provoz protokolu HTTP dnes je standardizován na použití portu TCP 80, protokol SMTP používá port TCP 25 a FTP používá porty TCP 20 a 21. Další aplikace používající protokol TCP jako přenos můžou zvolit jiné dostupné číslo portu, a to buď podle konvence, nebo prostřednictvím formální normalizace.  
  
 Použití čísel portů k rozlišení mezi aplikacemi mělo problémy se zabezpečením. Brány firewall jsou obecně nakonfigurované pro blokování provozu TCP na všech portech s výjimkou několika známých vstupních bodů, takže nasazení aplikace, která používá nestandardní port, je často komplikované nebo dokonce znemožňuje vzhledem k přítomnosti podnikových a osobních bran firewall. Aplikace, které mohou komunikovat přes standardní, dobře známé porty, které jsou již povoleny, omezují vnější plochu pro útok. Mnohé síťové aplikace využívají protokol HTTP, protože většina bran firewall je ve výchozím nastavení nakonfigurovaná tak, aby umožňovala provoz na portu TCP 80.  
  
 Model HTTP.SYS, ve kterém se na platformě Windows stane provoz pro mnoho různých aplikací HTTP na jednom portu TCP. Tato možnost poskytuje běžný bod řízení pro Správce brány firewall a umožňuje vývojářům aplikací minimalizovat náklady na nasazení nových aplikací, které mohou využívat síť.  
  
 Možnost sdílení portů mezi více aplikacemi HTTP byla dlouhodobě funkcí Internetová informační služba (IIS). Ale byl jenom s představením HTTP.SYS (naslouchací proces protokolu HTTP v režimu jádra) se službou IIS 6,0, že tato infrastruktura byla plně zobecněná. V důsledku toho HTTP.SYS umožňuje libovolným uživatelským procesům sdílet porty TCP vyhrazené pro přenosy HTTP. Tato možnost umožňuje mnoha aplikacím HTTP souběžně ve stejném fyzickém počítači v samostatných izolovaných procesech během sdílení síťové infrastruktury vyžadované pro odesílání a příjem provozu přes port TCP 80. Služba sdílení portů Net. TCP umožňuje stejný typ sdílení portů pro aplikace NET. TCP.  
  
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
