---
title: Služby pracovních postupů – přehled
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: eaf5fb4b20aca0983dcbe00724ab81803834940a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-services-overview"></a>Služby pracovních postupů – přehled
Služby pracovních postupů jsou služeb založených na WCF, které jsou implementovány pomocí pracovních postupů. Služby pracovních postupů jsou pracovní postupy, které používají zasílání zpráv aktivity pro odesílání a přijímání zpráv Windows Communication Foundation (WCF). Rozhraní .NET framework 4.5 zavádí několik zasílání zpráv aktivit, které umožňují odesílat a přijímat zprávy v rámci pracovního postupu. Další informace o zasílání zpráv aktivity a jak se lze použít k implementaci vzory jiná zpráva exchange najdete v tématu [zasílání zpráv aktivity](../../../../docs/framework/wcf/feature-details/messaging-activities.md).  
  
## <a name="benefits-of-using-workflow-services"></a>Výhody použití služby pracovních postupů  
 Jako stále stát distribuovat aplikace, budou jednotlivé služby zodpovědná za volání jinými službami a snižování zátěže část práce. Implementace těchto volání jako asynchronní operace zavádí některé složitost do kódu. Zpracování chyb přidá další složitosti ve formě zpracování výjimek a poskytuje podrobné informace o sledování. Některé služby jsou často dlouho běžící a může trvat až cenné systémové prostředky při čekání na vstup. Kvůli těmto problémům distribuované aplikace jsou často velmi složitá a obtížná k zápisu a údržbu. Pracovní postupy jsou přirozené způsoby, jak vyjádřit koordinaci asynchronní práce, zejména volání externích služeb. Pracovní postupy jsou také efektivní v představující dlouho běžící obchodní procesy. Je tyto vlastnosti, které je pracovní postup skvělé asset k vytváření služeb v distribuovaném prostředí.  
  
## <a name="implementing-a-workflow-service"></a>Implementace služby pracovních postupů  
 Při implementaci služby WCF, definujete číslo smlouvy, které popisují služby a data, která se odesílá a přijímá. Data je reprezentován jako kontrakty dat a kontrakty zpráv. Služby WCF a pracovní postup použít jako součást popis služby definice kontraktu dat kontrakt a zprávy. Službu samotnou popsali, jak službu vystavuje metadata (ve formě WSDL). Ve službě WCF definování kontraktů služby a operace kontraktů služby a operace, které podporuje. Ve službě pracovní postup, ale tyto smlouvy jsou součástí samotný proces firmy. Pomocí procesu nazývaného kontrakt odvození jsou vystaveny v metadatech. Když je pracovní postup služby hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, je zkontrolován definice pracovního postupu a kontraktu se vygeneruje na základě sady zasílání zpráv aktivity nalezen v pracovním postupu. Konkrétně tyto aktivity a vlastnosti jsou použita pro vytvoření kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive> Aktivity  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply> Aktivity  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity  
  
 Konečný výsledek kontrakt odvození je popis služby pomocí stejné datové struktury jako služby WCF a kontrakty operaci. Tyto informace se pak používá ke zveřejnění WSDL pro služby pracovního postupu.  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] neumožňuje můžete zapsat pomocí stávající definici kontraktu bez podpora některých dalších nástrojů služby pracovních postupů. Kontrakty služeb pracovních postupů jsou vytvořené pomocí procesu odvození smlouvy, jak jsme vysvětlili výše. Kontrakty zpráv kontraktů a kontraktů dat plně podporuje, ale.  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>Služby pracovních postupů a na základě služby MSMQ vazby  
 WCF definuje dvě vazby služby MSMQ na základě <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Na základě služby MSMQ vazby se často používají s služeb pracovních postupů z důvodu dlouhodobé povahu těchto služeb. Mají vazby služby MSMQ založené `ValidityDuration` vlastnost, která určuje, jak dlouho může převzít zpráv MSMQ platná. Z důvodu dlouhotrvající povaha služeb pracovních postupů je možné, že doba platnosti MSMQ zprávy, které může uplynout, než služby pracovního postupu může zpracovat. Je proto velmi důležité k nastavení doby platnosti vazby služby MSMQ na odpovídající hodnotu. Tato hodnota musí být vybrána na základě pracovního postupu a jak zpracovává zprávy. Například pokud máte pracovního postupu s <xref:System.ServiceModel.Activities.Receive> aktivity, za nímž následuje vlastní aktivitu, která přebírá 10 minut, za nímž následuje jiný <xref:System.ServiceModel.Activities.Receive> aktivity, správné hodnoty pro `ValidityDuration` by být větší než 10 minut.  
  
## <a name="hosting-a-workflow-service"></a>Hostování služby pracovního postupu  
 Jako služby WCF musí být hostované služby pracovních postupů. Použití služeb WCF <xref:System.ServiceModel.ServiceHost> třída pro hostování služeb a pracovní postup služby použijte <xref:System.ServiceModel.Activities.WorkflowServiceHost> pro hostování služeb. Jako služby WCF je možné hostovat služeb pracovních postupů v mnoha různými způsoby, například:  
  
-   Ve spravovaných [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace.  
  
-   V Internetové informační službě (IIS).  
  
-   V aktivační službě procesů systému Windows (WAS).  
  
-   Ve spravované službě Windows.  
  
 Pracovní postup služby hostované ve spravovaných [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace nebo spravované služby systému Windows vytvořit instanci <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy a předejte ji instanci <xref:System.ServiceModel.Activities.WorkflowService> obsahující definice pracovního postupu v rámci <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> vlastnost. Definice pracovního postupu, který obsahuje aktivity, zasílání zpráv je k dispozici jako služby pracovních postupů.  
  
 K hostování služby pracovního postupu ve službě IIS nebo WAS, umístěte .xamlx soubor, který obsahuje definici pracovního postupu služby do virtuálního adresáře. Výchozí koncový bod (pomocí <xref:System.ServiceModel.BasicHttpBinding>) je vytvoření automaticky Další informace najdete v části [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md). Také můžete umístit soubor Web.config ve virtuálním adresáři zadat vlastní koncové body. Pokud vaše definice pracovního postupu se v sestavení můžete umístit soubor .svc ve virtuálním adresáři a sestavení pracovního postupu v adresáři App_Code. Soubor .svc musíte zadat objekt pro vytváření hostitele služby a třídu, která implementuje služby pracovního postupu. Následující příklad ukazuje, jak zadat objekt pro vytváření hostitele služby a určit třídu, která implementuje služby pracovního postupu.  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```
