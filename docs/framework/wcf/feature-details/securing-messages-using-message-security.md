---
title: Zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: cf014c8aa972c45140a523573b9806996062b40f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991026"
---
# <a name="securing-messages-using-message-security"></a>Zabezpečení zpráv
Tato část popisuje zabezpečení zpráv WCF při použití <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Před čtením prostřednictvím tohoto tématu, se doporučuje, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující obrázek poskytuje koncepční model komunikaci ve frontě pomocí technologie WCF. Tento obrázek a terminologie se používají k vysvětlení  
  
 koncepty zabezpečení přenosu.  
  
 ![Ve frontě diagramu aplikace](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Při odesílání zpráv zařazených do fronty pomocí technologie WCF, zprávy WCF je připojen jako text zprávy služby Řízení front zpráv (MSMQ). Při zabezpečení přenosu zabezpečuje celý MSMQ zprávy, zprávu (nebo SOAP) zabezpečení zabezpečuje pouze text zprávy služby MSMQ.  
  
 Klíčovým konceptem zabezpečení zpráv je, že klient zabezpečuje zprávu pro přijímající aplikace (služba), na rozdíl od přenosu zabezpečení, kde klient zabezpečuje pro cílovou frontu zprávy. V důsledku toho služba MSMQ hraje žádná část při zabezpečování zprávy WCF pomocí zabezpečení zpráv.  
  
 Zabezpečení zpráv WCF přidá hlavičky zabezpečení zprávy WCF, která lze integrovat s stávajících infrastruktur zabezpečení, jako je například certifikát nebo protokolu Kerberos.  
  
## <a name="message-credential-type"></a>Typ pověření zprávy  
 Zabezpečení zpráv pomocí, klienta a služby ale může představovat přihlašovací údaje k ověření navzájem. Zabezpečení zpráv můžete vybrat tak, že nastavíte <xref:System.ServiceModel.NetMsmqBinding.Security%2A> režimu `Message` nebo `Both` (to znamená použít zabezpečení přenosů a zpráv zabezpečení).  
  
 Můžete použít službu <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost ke kontrole přihlašovacích údajů pro ověření klienta. Může také sloužit pro další kontroly autorizace, který vybírá služby k implementaci.  
  
 Tato část popisuje typy různých přihlašovacích údajů a jejich použití v případě front.  
  
### <a name="certificate"></a>Certifikát  
 Typ přihlašovacích údajů certifikát certifikát X.509, který používá k identifikaci služby a klienta.  
  
 V rámci typického scénáře klient a služba vydal platný certifikát důvěryhodné certifikační autority. Potom se naváže připojení, klient se ověří platnost služby pomocí certifikátu služby se rozhodnout, jestli je vztah důvěryhodnosti služby. Podobně služba používá certifikát klienta pro ověření klienta vztah důvěryhodnosti.  
  
 Vzhledem k odpojené povaze fronty, klient a služba nemusí být online ve stejnou dobu. V důsledku toho klienta a služby mají k výměně certifikátů out-of-band. Zejména klienta tím, že podržíte ve svém úložišti důvěryhodných certifikátů služby, (která může být zřetězené k certifikační autoritě) musí důvěřovat, že komunikaci se službou správné. Pro ověření klienta, služba používá certifikát X.509 připojil se zpráva, která se mu odpovídá certifikátem v úložišti k ověření pravosti klienta. Znovu certifikát musí být zřetězené k certifikační autoritě.  
  
 Na počítači se systémem Windows jsou certifikáty uložené v několika druhů úložišť. Další informace o různých úložištích, naleznete v tématu [úložiště certifikátů](https://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ pověření zprávy Windows používá protokol Kerberos.  
  
 Protokol Kerberos je mechanismus zabezpečení, který ověřuje uživatele v doméně a umožňuje ověřeným uživatelům k navázání zabezpečené kontextů se ostatní entity v doméně.  
  
 Problém s pomocí protokolu Kerberos pro komunikaci ve frontě jsou relativně krátkodobou lístků, které obsahují identity klienta, který distribuuje na distribuční Center KDC (Key). A *životnost* souvisí s lístek služby Kerberos, který označuje platnost-the-ticket. V důsledku toho zadány vysokou latencí, vám nemůže být jisti, že token, který je stále platný pro službu, která ověřuje klienta.  
  
 Všimněte si, že při použití tento typ přihlašovacích údajů, služba musí být spuštěna pod účtem služby.  
  
 Protokol Kerberos se používá ve výchozím nastavení při výběru přihlašovacími údaji zprávy. Další informace najdete v tématu [zkoumání protokolu Kerberos, protokol pro distribuované zabezpečení ve Windows 2000](https://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Uživatelské jméno, heslo  
 Pomocí této vlastnosti se klient může ověřit pomocí uživatelského jména hesla v záhlaví zabezpečení zprávy se k serveru.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 K vydání tokenu, který lze připojit ke zprávě pro službu pro ověření klienta, můžete použít klienta služby tokenů zabezpečení.  
  
## <a name="using-transport-and-message-security"></a>Pomocí přenosu a zabezpečení zpráv  
 Při použití zabezpečení přenosů a zpráv zabezpečení, musí být certifikát používaný k zabezpečení i na úrovni zprávy protokolu SOAP a přenos zprávy stejná.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
