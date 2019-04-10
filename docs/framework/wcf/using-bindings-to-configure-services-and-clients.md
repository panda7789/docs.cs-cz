---
title: Používání vazeb ke konfiguraci služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 8080451d64f74629451c6ca66fb27d93c9f29ed8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209499"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Používání vazeb ke konfiguraci služeb a klientů
Vazby jsou objekty, které určují podrobnosti o komunikaci požadované pro připojení na koncový bod. Přesněji řečeno vazby obsahují informace o konfiguraci, která se používá k vytvoření modul runtime klienta nebo služby tak, že definujete, jaké jsou specifikace přenosy, formáty (kódování zpráv) a protokoly pro příslušného klienta nebo koncový bod kanálu. K vytvoření funkční služby Windows Communication Foundation (WCF), každý koncový bod služby vyžaduje vazbu. Toto téma vysvětluje, co jsou vazby, jak jsou definovány a jak je určeno konkrétní vazeb pro koncový bod.  
  
## <a name="what-a-binding-defines"></a>Co definuje vazbu  
 Informace v vazbu může být velmi základní nebo velmi složité. Základní vazby určuje pouze přenosový protokol (například HTTP), který se použije pro připojení ke koncovému bodu. Obecně platí informace, které obsahuje vazbu o tom, jak připojit ke koncovému bodu se dělí do kategorií v následující tabulce.  
  
 Protokoly  
 Určuje mechanismus zabezpečení, který je používán; funkce spolehlivé zasílání zpráv nebo nastavení toku kontextu transakce.  
  
 Přenos  
 Určuje základní přenos protokol, který použít (například protokol TCP nebo HTTP).  
  
 Kódování  
 Určuje kódování zpráv, například, text/XML, binární soubor nebo zpráv přenosu optimalizace mechanismus (MTOM), která určuje, jak jsou zprávy reprezentovaná jako bajtové datové proudy na lince.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 WCF obsahuje sadu vazeb poskytovaných systémem, které jsou navržené tak, aby pokryl většinu požadavků aplikace a scénáře. Následující třídy představují některé příklady vazeb poskytovaných systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Protokol HTTP vazby vhodné pro připojení k webovým službám, který odpovídá WS-I Basic Profile 1.1 specifikace (například webových služeb ASP.NET [ASMX] – na základě služby).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Specifikace protokoly služeb vazba vhodný pro připojení ke koncovým bodům, které odpovídají na webu protokolu HTTP.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Binární soubor .NET, kódování a rámců technologií ve spojení s Windows s názvem kanál přenosu používá pro připojení k jiné koncových bodů WCF na stejném počítači.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Binární soubor .NET, kódování a rámců technologií ve spojení s řízení front zpráv (MSMQ) používá k vytvoření zprávy ve frontě připojení pomocí dalších koncových bodů WCF.  
  
 Úplný seznam vazeb poskytovaných systémem s popisem, naleznete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Pokud kolekce vazeb poskytovaných systémem nemá správnou kombinaci funkcí, které vyžaduje služby aplikace, můžete vytvořit <xref:System.ServiceModel.Channels.CustomBinding> vazby. Další informace o jednotlivých prvcích <xref:System.ServiceModel.Channels.CustomBinding> vazby, naleznete v tématu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Používání vazeb  
 Používání vazeb zahrnuje dva základní kroky:  
  
1.  Vyberte nebo definujících vazbu. Nejjednodušším způsobem je použít výchozí nastavení a zvolte jednu z vazeb poskytovaných systémem. Můžete také zvolit vazeb poskytovaných systémem a obnovit jeho hodnotám vlastností tak, aby vyhovoval vašim požadavkům. Alternativně můžete vytvoření vlastní vazby a nastavit každé vlastnosti podle potřeby.  
  
2.  Vytvoření koncového bodu, který používá tuto vazbu.  
  
## <a name="code-and-configuration"></a>Kódu a konfigurace  
 Můžete definovat nebo nakonfigurujte vazby prostřednictvím kódu nebo konfigurace. Tyto dva přístupy platí bez ohledu na typ vazby používá, například, jestli používáte poskytovaných systémem nebo <xref:System.ServiceModel.Channels.CustomBinding> vazby. Obecně platí pomocí kódu vám plnou kontrolu nad definice vazbu při kompilaci. Použití konfigurace, umožňuje na druhé straně může správce systému nebo uživatele služby WCF nebo klienta můžete změnit parametry vazby. Díky této flexibilitě je často žádoucí, protože neexistuje žádný způsob, jak předvídat požadavky na konkrétní počítač a síťové podmínky, do které aplikace WCF je k nasazení. Informace o připojení (a adresování) z kódu oddělení umožňuje správcům změnit podrobnosti vazby bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci. Všimněte si, že pokud vazba je definováno v kódu, přepíše všechny definice podle konfigurace v konfiguračním souboru. Příklady těchto přístupů naleznete v následujících tématech:  
  
-   [Postupy: Hostování služby WCF ve spravované aplikace](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) poskytuje příklad vytvoření vazby v kódu.  
  
-   [Kurz: Vytvoření klienta Windows Communication Foundation](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) poskytuje příklad vytvoření klienta s použitím konfigurace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Postupy: Určení vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Určení vazby služby v kódu](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [Postupy: Určení klientské vazby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [Postupy: Určení klientské vazby v kódu](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
