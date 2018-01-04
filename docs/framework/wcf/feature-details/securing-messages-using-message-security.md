---
title: "Zabezpečení zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: be727fe2b69258a058ba99dc8aa40ae148d3dd99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securing-messages-using-message-security"></a>Zabezpečení zpráv
Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení zpráv při použití <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Než si přečtete prostřednictvím tohoto tématu, doporučujeme, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující obrázek poskytuje koncepční model komunikace ve frontě pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Tento obrázek a terminologie se používají k vysvětlují  
  
 koncepty zabezpečení přenosu.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Při odesílání zpráv zařazených do fronty pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy je připojen jako text zprávy služby Řízení front zpráv (MSMQ). Při zabezpečení přenosu zabezpečuje celý MSMQ zpráv, zpráv (nebo SOAP) zabezpečení pouze zabezpečuje tělo zprávy služby MSMQ.  
  
 Klíče koncept zabezpečení zpráv je, že klient zabezpečuje zprávu pro přijímající aplikace (služba), na rozdíl od zabezpečení přenosu, kde klient zabezpečuje zprávu pro cílové fronty. Jako takový MSMQ hraje žádná část při zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpráv pomocí zabezpečení zpráv.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpečení zpráv přidá záhlaví zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávu, která integrovat existující infrastruktury zabezpečení, jako certifikát nebo protokolu Kerberos.  
  
## <a name="message-credential-type"></a>Typ pověření zprávy  
 Pomocí zabezpečení zpráv, klienta a služby s sebou může nést přihlašovací údaje k ověření jednotlivých jiné. Zabezpečení zpráv můžete vybrat podle nastavení <xref:System.ServiceModel.NetMsmqBinding.Security%2A> režim `Message` nebo `Both` (to znamená, použijte zabezpečení přenosu a zabezpečení zpráv).  
  
 Můžete použít službu <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost zkontrolovat, že pověření použitá k ověření klienta. To lze také pro další kontroly autorizace, služba se rozhodne pro implementaci.  
  
 Tato část popisuje typy různých přihlašovacích údajů a způsob jejich používání s fronty.  
  
### <a name="certificate"></a>certifikát  
 Tento typ přihlašovacích údajů certifikátu používá k identifikaci služby a klient certifikát X.509.  
  
 V případě typické klienta a služby jsou vydávány platný certifikát důvěryhodné certifikační autority. Potom připojení, klient se ověří platnost služby pomocí certifikátu služby se rozhodnout, jestli je vztah důvěryhodnosti služby. Podobně služby používá certifikát klienta k ověření klienta vztah důvěryhodnosti.  
  
 Vzhledem k odpojené povaze fronty, klient a služba nemusí být online ve stejnou dobu. Klient a služba jako takový mít exchange out-of-band certifikáty. Konkrétně musí klient, na základě podržíte certifikátu služby, (který může být zřetězené certifikační autorita) ve svém úložišti důvěryhodných důvěřovat komunikuje s správné služby. Pro ověřování klienta, používá služba certifikátu X.509 připojené k zprávu, která se shoduje se s certifikátu v jeho úložiště k ověření pravosti klienta. Znovu musí být certifikát váže k certifikační autoritě.  
  
 V počítači se systémem Windows jsou certifikáty uložené v několik druhů úložišť. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jiné úložiště, najdete v části [úložiště certifikátů](http://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ přihlašovacích údajů zpráv systému Windows používá protokol Kerberos.  
  
 Protokol Kerberos je mechanismus zabezpečení, který ověřuje uživatele v doméně a umožňuje ověřeným uživatelům navázání zabezpečeného kontextů se ostatní entity v doméně.  
  
 Problém s použitím protokolu Kerberos pro komunikaci ve frontě je poměrně krátkodobou lístků, které obsahují identity klienta, který distribuuje distribuční Center KDC (Key). A *životnost* souvisí s lístek protokolu Kerberos, která určuje platnost lístku. Jako takový zadány vysokou latencí, vám nemůže být se, že token je stále platný pro službu, která ověřuje klienta.  
  
 Všimněte si, že při použití tento typ přihlašovacích údajů, služba musí být spuštěna pod účtem služby.  
  
 Při výběru pověření zprávy je ve výchozím nastavení používá protokol Kerberos. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zkoumání protokolu Kerberos, protokol pro distribuované zabezpečení ve Windows 2000](http://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Uživatelské jméno heslo  
 Pomocí této vlastnosti, můžete ověřovat klienta k serveru pomocí uživatelského jména hesla v záhlaví zabezpečení zprávy.  
  
### <a name="issuedtoken"></a>IssuedToken  
 K vydání tokenu, které lze připojit ke zprávě pro službu pro ověření klienta, můžete použít klienta služby tokenů zabezpečení.  
  
## <a name="using-transport-and-message-security"></a>Pomocí přenosu a zabezpečení zpráv  
 Při použití zabezpečení přenosu a zabezpečení zpráv, certifikát sloužící k zabezpečení zpráv, jak při přenosu a úroveň protokolu SOAP zprávy musí být stejné.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
