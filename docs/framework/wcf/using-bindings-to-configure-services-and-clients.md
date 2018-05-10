---
title: Používání vazeb ke konfiguraci služeb a klientů
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 8271f51885c0d7800d26018b94942a7d832bf4a5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Používání vazeb ke konfiguraci služeb a klientů
Vazby jsou objekty, které zadejte podrobnosti komunikace požadované pro připojení ke koncovému bodu. Přesněji řečeno vazby obsahovat informace o konfiguraci, která se používá k vytvoření klienta služby Windows nebo modul runtime definováním specifika přenosy, formáty (kódování zpráv) a protokoly pro příslušné kanál koncového bodu nebo klienta. Postup vytvoření funkční služby Windows Communication Foundation (WCF), každý koncový bod v rámci služby vyžaduje vazbu. Toto téma vysvětluje, co jsou vazby, jak jsou definovány a jak konkrétní vazbu je zadán pro koncový bod.  
  
## <a name="what-a-binding-defines"></a>Co definuje vazbu  
 Informace v vazbu může být velmi základní nebo velmi složité. Nejzákladnější vazba určuje pouze přenosový protokol (jako je například HTTP), musíte použít pro připojení ke koncovému bodu. Obecně platí informace, které obsahuje vazbu o tom, jak připojit ke koncovému bodu spadá do kategorií v následující tabulce.  
  
 protokoly  
 Určuje bezpečnostní mechanismus, používají, spolehlivého zasílání zpráv schopností nebo nastavení tok kontextu transakce.  
  
 Přenos  
 Určuje základní přenosový protokol použít (například protokol TCP nebo HTTP).  
  
 Kódování  
 Určuje kódování zpráv, například, text/XML, binární nebo zpráva přenosu optimalizace mechanismus (MTOM), která určuje, jak jsou zprávy reprezentovány jako bajtové datové proudy v drátové síti.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 WCF obsahuje sadu vazby poskytované systémem, které jsou navrženy tak, aby pokrývalo většina scénáře a požadavky na aplikace. Následující třídy představují některé příklady vazby poskytované systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: HTTP protokol vazby vhodný pro připojení k webovým službám, který odpovídá WS-I Basic Profile 1.1 specifikace (například webových služeb ASP.NET [ASMX]-služby).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Specifikace protokoly služeb protokol HTTP vazby vhodný pro připojení ke koncovým bodům, které odpovídají na webu.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Používá .NET binární kódování a počet rámců technologie ve spojení se systémem Windows s názvem kanálu přenosu pro připojení k jiné koncových bodů WCF na stejném počítači.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Používá k vytvoření zpráv zařazených ve frontě připojení pomocí dalších koncových bodů WCF .NET binární kódování a počet rámců technologie ve spojení s řízení front zpráv (MSMQ).  
  
 Úplný seznam vazeb poskytovaných systémem s popisy, najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Pokud kolekce vazby poskytované systémem nemá správnou kombinaci funkcí, které vyžaduje aplikaci služby, můžete vytvořit <xref:System.ServiceModel.Channels.CustomBinding> vazby. Další informace o jednotlivých prvcích <xref:System.ServiceModel.Channels.CustomBinding> vazby, najdete v části [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a [vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Používání vazeb  
 Používání vazeb zahrnuje dva základní kroky:  
  
1.  Vyberte nebo zadejte vazbu. Nejsnazší je pomocí výchozího nastavení a vyberte jednu z vazby poskytované systémem. Můžete také zvolit vazby poskytované systémem a obnovit jeho hodnoty vlastností podle svých potřeb. Alternativně můžete vytvořit vlastní vazby a nastavit každý vlastnost podle potřeby.  
  
2.  Vytvořte koncový bod, který používá tuto vazbu.  
  
## <a name="code-and-configuration"></a>Kód a konfigurace  
 Můžete definovat nebo nakonfigurovat vazby prostřednictvím kódu nebo konfigurace. Tyto dva přístupy, které jsou nezávislé na typ vazby, které používají, například, zda používáte poskytované systémem nebo <xref:System.ServiceModel.Channels.CustomBinding> vazby. Obecně platí pomocí kódu nabízí úplnou kontrolu nad definici vazby při kompilaci. Pomocí konfigurace, na druhé straně může správce systému nebo uživatele služby WCF nebo klienta, chcete-li změnit parametry vazby. Tuto flexibilitu potřebují je často žádoucí, protože neexistuje žádný způsob, jak předvídání požadavků na konkrétní počítač a síťové podmínky, do kterých se aplikace WCF je k nasazení. Oddělení závazné (a adresování) informace z kódu umožňuje správcům změnit podrobnosti o vazby bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci. Všimněte si, že pokud vazba je definována v kódu, přepíše všechny definice založené na konfiguraci v konfiguračním souboru. Příklady těchto přístupů najdete v následujících tématech:  
  
-   [Postupy: hostování služby WCF ve spravované aplikaci](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) poskytuje příklad vytvoření vazby v kódu.  
  
-   [Postupy: Konfigurace klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) poskytuje příklad vytvoření klienta pomocí konfigurace.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Postupy: Určení vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Postupy: Určení vazby služby v kódu](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [Postupy: Určení vazby klienta v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [Postupy: Určení vazby klienta v kódu](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
