---
title: Zabezpečení zpráv
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 1098057042c0842161258fd081d3ee63e82b4c5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395706"
---
# <a name="securing-messages-using-message-security"></a>Zabezpečení zpráv
Tato část popisuje zabezpečení zpráv WCF při použití <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
> Než si přečtete toto téma, doporučujeme, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující ilustrace poskytuje koncepční model komunikace ve frontě pomocí WCF. Tato ilustrace a terminologie slouží k vysvětlení  
  
 Koncepce zabezpečení přenosu.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distribuované – fronta – obrázek")  
  
 Při odesílání zpráv zařazených do fronty pomocí WCF je zpráva WCF připojena jako tělo zprávy služby Řízení front zpráv (MSMQ). I když zabezpečení přenosu zabezpečuje celou zprávu služby MSMQ, zabezpečení zprávy (nebo protokolu SOAP) zabezpečuje pouze tělo zprávy služby MSMQ.  
  
 Klíčovým konceptem zabezpečení zpráv je, že klient zabezpečuje zprávu pro přijímající aplikaci (službu), na rozdíl od zabezpečení přenosu, kde klient zabezpečuje zprávu pro cílovou frontu. V takovém případě služba MSMQ nehraje žádnou součást při zabezpečení zprávy WCF pomocí zabezpečení zpráv.  
  
 Zabezpečení zpráv WCF přidává záhlaví zabezpečení do zprávy WCF, která se integruje s existujícími infrastrukturami zabezpečení, jako je certifikát nebo protokol Kerberos.  
  
## <a name="message-credential-type"></a>Typ přihlašovacích údajů zprávy  
 Pomocí zabezpečení zpráv můžou služby a klienti zadat přihlašovací údaje pro jiné ověřování. Můžete vybrat zabezpečení zprávy nastavením režimu <xref:System.ServiceModel.NetMsmqBinding.Security%2A> na `Message` nebo `Both` (to znamená zabezpečení přenosu i zabezpečení zpráv).  
  
 Služba může pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> zkontrolovat přihlašovací údaje používané k ověřování klienta. Tato možnost se dá použít taky k dalším kontrolám autorizace, které služba zvolí k implementaci.  
  
 V této části jsou vysvětleny různé typy přihlašovacích údajů a jejich použití s frontami.  
  
### <a name="certificate"></a>Certifikát  
 Typ přihlašovacích údajů certifikátu používá k identifikaci služby a klienta certifikát X. 509.  
  
 V typickém scénáři klient a služba vydávají platný certifikát důvěryhodnou certifikační autoritou. Pak se připojení naváže, klient ověří platnost služby pomocí certifikátu služby a určí, jestli může službu důvěřovat. Podobně služba používá certifikát klienta k ověření vztahu důvěryhodnosti klienta.  
  
 Vzhledem k odpojené povaze front nemusí být klient a služba online ve stejnou dobu. V takovém případě musí klient a služba vyměňovat certifikáty vzdáleně. Konkrétně je potřeba, aby klient na základě držení certifikátu služby (který může být zřetězený k certifikační autoritě) ve svém důvěryhodném úložišti důvěřoval, že komunikuje se správnou službou. Pro ověřování klienta používá služba k ověření pravosti klienta certifikát X. 509 připojený ke zprávě, aby se shodoval s certifikátem v úložišti. Certifikát musí být znovu zřetězený s certifikační autoritou.  
  
 V počítači se systémem Windows jsou certifikáty uchovávány v několika druzích úložišť. Další informace o různých úložištích najdete v tématu [úložiště certifikátů](https://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ přihlašovacích údajů zprávy systému Windows používá protokol Kerberos.  
  
 Protokol Kerberos je bezpečnostní mechanismus, který ověřuje uživatele v doméně a umožňuje ověřeným uživatelům vytvářet zabezpečené kontexty s jinými entitami v doméně.  
  
 Problém s používáním protokolu Kerberos pro komunikaci ve frontě je, že lístky obsahující identitu klienta, které jsou distribuovány služba KDC (Key Distribution Center) (KDC), jsou poměrně krátkodobé. K lístku Kerberos, který označuje platnost lístku, je přidružená *Doba života* . V takovém případě s vysokou latencí nemůžete mít jistotu, že je token stále platný pro službu, která ověřuje klienta.  
  
 Všimněte si, že při použití tohoto typu pověření musí služba běžet pod účtem služby.  
  
 Protokol Kerberos se ve výchozím nastavení používá při výběru přihlašovacích údajů zprávy.
  
### <a name="username-password"></a>Heslo pro uživatelské jméno  
 Pomocí této vlastnosti může klient ověřit server pomocí hesla uživatele v záhlaví zabezpečení zprávy.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 Klient může použít službu tokenu zabezpečení k vydání tokenu, který je možné připojit ke zprávě, aby mohl ověřit klienta.  
  
## <a name="using-transport-and-message-security"></a>Použití přenosu a zabezpečení zpráv  
 Při použití zabezpečení přenosů a zabezpečení zpráv musí být certifikát použitý k zabezpečení zprávy jak v přenosu, tak i v úrovni zprávy protokolu SOAP.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
