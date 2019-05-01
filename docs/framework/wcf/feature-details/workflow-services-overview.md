---
title: Přehled služeb pracovních postupů – WCF
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 1461ef545c4b31f84e62d82453320179d9aa74e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050334"
---
# <a name="workflow-services-overview"></a>Přehled služeb pracovních postupů

Služby pracovních postupů jsou službám WCF, které jsou implementovány pomocí pracovních postupů. Služby pracovních postupů jsou pracovní postupy, které používají zasílání zpráv aktivity pro odesílání a příjem zpráv Windows Communication Foundation (WCF). Rozhraní .NET framework 4.5 představuje počet zasílání zpráv aktivity, které umožňují odesílání a příjem zpráv z v rámci pracovního postupu. Další informace o zasílání zpráv aktivity a jak můžete použít k implementaci jiná zpráva exchange vzorů najdete v tématu [zasílání zpráv aktivity](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>Výhody používání služby pracovního postupu

Jak se stále stanou distribuované aplikace, jednotlivé služby převzít odpovědnost za volání jiné služby, přesměrovat na určitou část práce. Implementace těchto volání jako asynchronní operace zavádí některé složitost do kódu. Zpracování chyb přidá další složitosti ve formě zpracování výjimek a poskytuje podrobné informace o sledování. Některé služby jsou často trvají dlouho a může trvat až cenné systémové prostředky při čekání na vstup. Kvůli těmto problémům distribuované aplikace jsou často velmi složité a těžko napsat a udržovat. Pracovní postupy jsou přirozený způsob, jak vyjádřit koordinaci asynchronní práci, zejména volání externích služeb. Pracovní postupy platí také v představující dlouhotrvající obchodních procesů. Je tato kvality, kterým je pracovní postup skvělý prostředek k vytváření služeb v distribuovaném prostředí.

## <a name="implementing-a-workflow-service"></a>Implementace služby pracovních postupů

Při implementaci služby WCF, můžete definovat několik smluv, které popisují služby a data, která odesílá a přijímá. Data je vyjádřena jako data kontraktů a kontraktů zpráv. Služby WCF a pracovního postupu pomocí definice kontraktu dat kontrakt a zprávy jako součást služby popisy. Samotné služby zveřejňuje metadata (ve formě WSDL) pro popis operace služby. Ve službě WCF definování kontraktů služby a operace kontraktů služby a operace, které podporuje. Ve službě pracovního postupu, ale těchto smluv jsou součástí samotný proces firmy. Pomocí procesu nazývaného smlouvy odvození jsou vystaveny v metadatech. Když je hostované služby pracovních postupů, pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definice pracovního postupu je zkontrolován a kontrakt je generován a základě sadu zasílání zpráv aktivity v pracovním postupu nalezen. Zejména následující aktivity a vlastnosti slouží ke generování kontraktu:

<xref:System.ServiceModel.Activities.Receive> Aktivita

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> Aktivita

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivita

Konečný výsledek odvození smlouvy je popis služby pomocí stejné datové struktury jako služby WCF a kontrakty operace. Potom tyto informace slouží k vystavení WSDL pro službu pracovního postupu.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] neumožňuje zápis služeb pracovních postupů pomocí existující definici kontraktu bez podpory některé další nástroje. Kontrakty služeb pracovního postupu jsou vytvořené v procesu odvození smlouvy, jak jsme vysvětlili výše. Kontrakty zpráv a kontrakty dat jsou plně podporovány, ale.

## <a name="workflow-services-and-msmq-based-bindings"></a>Služby pracovních postupů a na základě služby MSMQ vazby

WCF definuje dvě vazby služby MSMQ podle <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  Na základě služby MSMQ vazby se často používají služby pracovního postupu z důvodu dlouhého povahu těchto služeb. Mít vazby služby MSMQ založené `ValidityDuration` vlastnost, která určuje, jak dlouho může převzít služby MSMQ zprávy platný. Vzhledem k povaze dlouhodobě spuštěných služeb pracovních postupů je možné, že doba platnosti služby MSMQ zprávy může uplynout, než ji může zpracovat služby pracovního postupu. Proto je velmi důležité nastavit doba platnosti vazby služby MSMQ na odpovídající hodnotu. Tato hodnota musí být vybrána na základě pracovního postupu a jak zpracovávat zprávy. Například pokud máte pracovní postup s <xref:System.ServiceModel.Activities.Receive> aktivity, za nímž následuje vlastní aktivitu, která přebírá 10 minut, za nímž následuje jiný <xref:System.ServiceModel.Activities.Receive> aktivity, správné hodnoty pro `ValidityDuration` by být delší než 10 minut.

## <a name="hosting-a-workflow-service"></a>Hostování služby pracovního postupu

Stejně jako služby WCF musí být hostovaný služeb pracovních postupů. Použití služby WCF <xref:System.ServiceModel.ServiceHost> třídy a hostování služeb pracovních postupů služby použijte <xref:System.ServiceModel.Activities.WorkflowServiceHost> pro hostování služeb. Stejně jako služby WCF je možné hostovat služby pracovního postupu mnoha různými způsoby, třeba:

- Ve spravovaných [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace.

- V Internetové informační službě (IIS).

- V aktivační službě procesů Windows (WAS).

- Ve spravované službě Windows.

Pracovní postup služby hostované ve spravovaných [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace nebo spravované služby Windows vytvořit instanci <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy a předat ji instance <xref:System.ServiceModel.Activities.WorkflowService> , který obsahuje definici pracovního postupu v rámci <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> vlastnost. Definice pracovního postupu, který obsahuje zasílání zpráv aktivity je vystavený jako služba pracovního postupu.

K hostování služby pracovního postupu v IIS nebo WAS, umístěte .xamlx souboru, který obsahuje definici služby pracovního postupu do virtuálního adresáře. Výchozí koncový bod (pomocí <xref:System.ServiceModel.BasicHttpBinding>) je automaticky vytvořen pro další informace, najdete v článku [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md). Můžete také umístit soubor Web.config ve virtuálním adresáři zadat vlastní koncové body. Pokud je vaše definice pracovního postupu v sestavení můžete umístit soubor .svc ve virtuálním adresáři a pracovní postup sestavení v adresáři App_Code. Souboru SVC musíte zadat objekt pro vytváření hostitele služby a třídy, která implementuje služba pracovního postupu. Následující příklad ukazuje, jak zadat objekt pro vytváření hostitele služby a určit třídu, která implementuje služba pracovního postupu.

```
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory
Service="EchoService"%>
```