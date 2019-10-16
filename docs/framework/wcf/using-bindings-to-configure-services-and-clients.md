---
title: Používání vazeb ke konfiguraci služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: dd83072d3a1c76279fcc00ea5b0a4a41e278e10a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321514"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Používání vazeb ke konfiguraci služeb a klientů
Vazby jsou objekty, které určují údaje o komunikaci požadované pro připojení ke koncovému bodu. Konkrétně vazby obsahují konfigurační informace, které se používají k vytvoření klienta nebo modulu runtime služby pomocí definování specifických přenosů, formátů drátů (kódování zpráv) a protokolů, které budou použity pro příslušný koncový bod nebo kanál klienta. Aby bylo možné vytvořit službu fungující Windows Communication Foundation (WCF), každý koncový bod ve službě vyžaduje vazbu. Toto téma vysvětluje, co jsou vazby, jak jsou definovány, a jak je pro koncový bod určena konkrétní vazba.  
  
## <a name="what-a-binding-defines"></a>Definice vazby  
 Informace ve vazbě mohou být velmi základní nebo velmi složité. Většina základních vazeb určuje pouze transportní protokol (například HTTP), který se musí použít pro připojení ke koncovému bodu. Obecně platí, že informace, které vazba obsahuje o tom, jak se připojit ke koncovému bodu, spadají do jedné z kategorií v následující tabulce.  
  
 Protokolů  
 Určuje mechanismus zabezpečení, který se používá, buď spolehlivé možnosti zasílání zpráv, nebo nastavení toku kontextu transakce.  
  
 Přepravu  
 Určuje podkladový transportní protokol, který se má použít (například TCP nebo HTTP).  
  
 Kódování  
 Určuje kódování zpráv, například text/XML, binární nebo mechanizmus pro optimalizaci přenosu zpráv (MTOM), který určuje, jak jsou zprávy vyjádřeny jako bajtové datové proudy na lince.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 WCF zahrnuje sadu vazeb poskytovaných systémem, které jsou navržené tak, aby pokryly většinu požadavků a scénářů aplikace. Následující třídy znázorňují některé příklady vazeb poskytovaných systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: vazba protokolu HTTP vhodná pro připojení k webovým službám, které odpovídají specifikaci 1,1 služby WS-I Basic Profile (například služby založené na službě ASP.NET Web Services [ASMX]).  
  
- <xref:System.ServiceModel.WSHttpBinding>: vazba protokolu HTTP vhodná pro připojení ke koncovým bodům, které odpovídají protokolům specifikace webové služby.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: používá technologii .NET Binary Encoding and rámce ve spojení s přenosem pojmenovaného kanálu Windows pro připojení k ostatním koncovým bodům WCF ve stejném počítači.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: používá technologii .NET Binary Encoding and rámce ve spojení se službou Řízení front zpráv (označovanou také jako MSMQ) k vytváření připojení zpráv ve frontě s ostatními koncovými body WCF.  
  
 Úplný seznam vazeb poskytovaných systémem, včetně popisů, najdete v tématu o [vazbách poskytovaných systémem](system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Pokud kolekce vazeb poskytnutá systémem nemá správnou kombinaci funkcí, které vyžaduje aplikace služby, můžete vytvořit vazbu <xref:System.ServiceModel.Channels.CustomBinding>. Další informace o prvcích <xref:System.ServiceModel.Channels.CustomBinding> vazba naleznete v tématu [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md) a [Custom Bindings](./extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Použití vazeb  
 Použití vazeb zahrnuje dva základní kroky:  
  
1. Vyberte nebo definujte vazbu. Nejjednodušší způsob je zvolit jednu ze zadaných vazeb ze systému a použít její výchozí nastavení. Můžete také zvolit systémovou vazbu a obnovit její hodnoty vlastností tak, aby vyhovovaly vašim požadavkům. Alternativně můžete vytvořit vlastní vazbu a nastavit všechny vlastnosti podle potřeby.  
  
2. Vytvořte koncový bod, který používá tuto vazbu.  
  
## <a name="code-and-configuration"></a>Kód a konfigurace  
 Můžete definovat nebo konfigurovat vazby prostřednictvím kódu nebo konfigurace. Tyto dva přístupy jsou nezávislé na typu použité vazby, například bez ohledu na to, zda používáte vazbu zadanou systémem nebo <xref:System.ServiceModel.Channels.CustomBinding>. Obecně platí, že použití kódu poskytuje plnou kontrolu nad definicí vazby při kompilaci. Pomocí konfigurace na druhé straně umožňuje správci systému nebo uživateli služby nebo klienta WCF měnit parametry vazeb. Tato flexibilita je často žádoucí, protože neexistuje žádný způsob, jak předpovědět konkrétní požadavky na počítač a síťové podmínky, do kterých se má nasadit aplikace WCF. Oddělení informací o vazbách (a adresách) z kódu umožňuje správcům změnit podrobnosti vazby bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci. Všimněte si, že pokud je vazba definována v kódu, přepíše všechny definice založené na konfiguraci provedené v konfiguračním souboru. Příklady těchto přístupů najdete v následujících tématech:  
  
- [Postupy: hostování služby WCF ve spravované aplikaci](how-to-host-a-wcf-service-in-a-managed-application.md) představuje příklad vytvoření vazby v kódu.  
  
- [Kurz: Vytvoření klienta Windows Communication Foundation](how-to-create-a-wcf-client.md) poskytuje příklad vytvoření klienta pomocí konfigurace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](endpoint-creation-overview.md)
- [Postupy: Určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Určení vazby služby v kódu](how-to-specify-a-service-binding-in-code.md)
- [Postupy: Určení vazby klienta v konfiguraci](how-to-specify-a-client-binding-in-configuration.md)
- [Postupy: Určení vazby klienta v kódu](how-to-specify-a-client-binding-in-code.md)
