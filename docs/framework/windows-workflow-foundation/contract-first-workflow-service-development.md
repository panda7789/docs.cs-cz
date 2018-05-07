---
title: Vývoj kontrakt první pracovní postup služby
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 10129fcb40d86d1ca7e42bce68b072e9118bcc88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="contract-first-workflow-service-development"></a>Vývoj kontrakt první pracovní postup služby
Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], funkce Windows Workflow Foundation (WF) lepší integrace mezi webové služby a pracovní postupy ve formě vývoj kontrakt první pracovního postupu. Nástroj pro vývoj kontrakt první pracovního postupu můžete navrhnout první kontrakt v kódu. Nástroj potom automaticky generuje šablonu aktivit v sadě nástrojů pro operace v kontraktu. Toto téma obsahuje přehled aktivit a vlastnosti ve službě pracovního postupu mapování do atributy kontraktu služby. Podrobný příklad vytváření pracovního postupu první kontraktu služby najdete v tématu [postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Mapování atributů kontraktu služby pracovního postupu atributů](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MappingAttributes)  
  
    -   [Atributy kontrakt služby](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
    -   [Operace kontrakt atributy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
    -   [Atributy kontrakt zprávy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
    -   [Atributy kontraktu dat](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
    -   [Selhání kontrakt atributy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
-   [Další podporu a informace o implementaci](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#AdditionalSupport)  
  
    -   [Funkce nepodporované služby kontraktu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    -   [Generování nakonfigurované aktivity zasílání zpráv](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
##  <a name="MappingAttributes"></a> Mapování atributů kontraktu služby pracovního postupu atributů  
 Tabulky v následujících částech zadejte jiný WCF atributy a vlastnosti a jak jsou mapované na zasílání zpráv aktivity a vlastnosti v pracovním postupu první kontrakt.  
  
-   [Atributy kontrakt služby](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ServiceContract)  
  
-   [Operace kontrakt atributy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#OperationContract)  
  
-   [Atributy kontrakt zprávy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#MessageContract)  
  
-   [Atributy kontraktu dat](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#DataContract)  
  
-   [Selhání kontrakt atributy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#FaultContract)  
  
###  <a name="ServiceContract"></a> Atributy kontrakt služby  
  
|Název vlastnosti|Podporováno|Popis|Ověření WF|  
|-------------------|---------------|-----------------|-------------------|  
|Třída CallbackContract|Ne|Získá nebo nastaví typ smlouvy, zpětného volání, když je kontrakt duplexního kontraktu.|(NENÍ K DISPOZICI)|  
|ConfigurationName|Ne|Získá nebo nastaví název používaná k nalezení službu v konfiguračním souboru aplikace.|(NENÍ K DISPOZICI)|  
|HasProtectionLevel|Ano|Získá hodnotu, která určuje, zda člen má přiřazené úroveň ochrany.|Receive.ProtectionLevel nesmí mít hodnotu null.|  
|Název|Ano|Získá nebo nastaví název \<portType > element v webové služby popis Language (WSDL).|Receive.ServiceContractName.LocalName by měl odpovídat.|  
|Obor názvů|Ano|Získá nebo nastaví obor názvů \<portType > element v webové služby popis Language (WSDL).|Receive.ServiceContractName.NameSpace by měl odpovídat.|  
|ProtectionLevel|Ano|Určuje, zda vazby pro daný kontrakt musí podporovat hodnotu vlastnosti ProtectionLevel.|Receive.ProtectionLevel by měl odpovídat.|  
|SessionMode|Ne|Získá nebo nastaví, zda relace nejsou povoleny, povoleno nebo požadováno.|(NENÍ K DISPOZICI)|  
|TypeId|Ne|Při implementaci v odvozené třídě získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(NENÍ K DISPOZICI)|  
  
 Sem vložte text pododdílu.  
  
###  <a name="OperationContract"></a> Operace kontrakt atributy  
  
|Název vlastnosti|Podporováno|Popis|Ověření WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akce|Ano|Získá nebo nastaví akci, WS-Addressing zprávy požadavku.|Receive.Action by měl odpovídat.|  
|Parametru AsyncPattern|Ne|Označuje, že operace je implementovaná asynchronně pomocí začátek\<methodName > a End\<methodName > metoda pár v kontraktu služby.|(NENÍ K DISPOZICI)|  
|HasProtectionLevel|Ano|Získá hodnotu, která určuje, zda zprávy pro tuto operaci musí šifrovaný podepsané, nebo obojí.|Receive.ProtectionLevel nesmí mít hodnotu null.|  
|IsInitiating|Ne|Získá nebo nastaví hodnotu, která určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru (pokud takové relace existuje).|(NENÍ K DISPOZICI)|  
|IsOneWay|Ano|Získá nebo nastaví hodnotu, která určuje, zda operace vrátí zprávu odpovědi.|(Přijímat žádné SendReply pro tuto nebo žádné ReceiveReply pro toto odesílání).|  
|IsTerminating|Ne|Získá nebo nastaví hodnotu, která určuje, zda operace služby způsobí, že server k ukončení relace po zprávy s odpovědí, pokud existuje, je odeslána.|(NENÍ K DISPOZICI)|  
|Název|Ano|Získá nebo nastaví název operace.|Receive.OperationName by měl odpovídat.|  
|ProtectionLevel|Ano|Získá nebo nastaví hodnotu, která určuje, jestli zprávy operace musí šifrovat podepsané, nebo obojí.|Receive.ProtectionLevel by měl odpovídat.|  
|ReplyAction|Ano|Získá nebo nastaví hodnotu akce protokolu SOAP zprávy s odpovědí operace.|SendReply.Action by měl odpovídat.|  
|TypeId|Ne|Při implementaci v odvozené třídě získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(NENÍ K DISPOZICI)|  
  
###  <a name="MessageContract"></a> Atributy kontrakt zprávy  
  
|Název vlastnosti|Podporováno|Popis|Ověření WF|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Ano|Získá hodnotu, která označuje, zda zpráva má úroveň ochrany.|Žádné ověření (Receive.Content a SendReply.Content musí odpovídat typ kontrakt zprávy).|  
|Atribut IsWrapped nastaven|Ano|Získá nebo nastaví hodnotu, která určuje, zda text zprávy má element obálku.|Žádné ověření (Receive.Content a Sendreply.Content musí odpovídat typ kontrakt zprávy).|  
|ProtectionLevel|Ne|Získá nebo nastaví hodnotu, která určí, zda zpráva musí zašifrován podepsané, nebo obojí.|(NENÍ K DISPOZICI)|  
|TypeId|Ano|Při implementaci v odvozené třídě získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|Žádné ověření (Receive.Content a SendReply.Content musí odpovídat typ kontrakt zprávy).|  
|WrapperName|Ano|Získá nebo nastaví název elementu obálku textu zprávy.|Žádné ověření (Receive.Content a SendReply.Content musí odpovídat typ kontrakt zprávy).|  
|WrapperNamespace|Ne|Získá nebo nastaví obor názvů elementu obálku textu zprávy.|(NENÍ K DISPOZICI)|  
  
###  <a name="DataContract"></a> Atributy kontraktu dat  
  
|Název vlastnosti|Podporováno|Popis|Ověření WF|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|Ne|Získá nebo nastaví hodnotu, která označuje, zda chcete zachovat objektu referenční data.|(NENÍ K DISPOZICI)|  
|Název|Ano|Získá nebo nastaví název kontraktu dat pro typ.|Žádné ověření (Receive.Content a SendReply.Content musí odpovídat typ kontrakt zprávy).|  
|Obor názvů|Ano|Získá nebo nastaví obor názvů pro kontrakt dat pro typ.|Žádné ověření (Receive.Content a SendReply.Content musí odpovídat typ kontrakt zprávy).|  
|TypeId|Ne|Při implementaci v odvozené třídě získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(NENÍ K DISPOZICI)|  
  
###  <a name="FaultContract"></a> Selhání kontrakt atributy  
  
|Název vlastnosti|Podporováno|Popis|Ověření WF|  
|-------------------|---------------|-----------------|-------------------|  
|Akce|Ano|Získá nebo nastaví akci zprávu protokolu SOAP selhání, který je zadaný jako součást operace kontrakt.|SendReply.Action by měl odpovídat.|  
|DetailType|Ano|Získá typ serializovatelný objekt, který obsahuje informace o chybě.|SendReply.Content by měl odpovídat typu|  
|HasProtectionLevel|Ne|Získá hodnotu, která označuje, zda má zprávu SOAP selhání přiřazené úroveň ochrany.|(NENÍ K DISPOZICI)|  
|Název|Ne|Získá nebo nastaví název chyby zprávy v webové služby popis Language (WSDL).|(NENÍ K DISPOZICI)|  
|Obor názvů|Ne|Získá nebo nastaví obor názvů chybu protokolu SOAP.|(NENÍ K DISPOZICI)|  
|ProtectionLevel|Ne|Určuje úroveň ochrany, kterou vyžaduje chybu protokolu SOAP z vazby.|(NENÍ K DISPOZICI)|  
|TypeId|Ne|Při implementaci v odvozené třídě získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(NENÍ K DISPOZICI)|  
  
##  <a name="AdditionalSupport"></a> Další podporu a informace o implementaci  
  
-   [Funkce nepodporované služby kontraktu](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
-   [Generování nakonfigurované aktivity zasílání zpráv](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md#ActivityGeneration)  
  
###  <a name="UnsupportedFeatures"></a> Funkce nepodporované služby kontraktu  
  
-   Použití TPL (Task Parallel Library) úloh v kontraktech není podporováno.  
  
-   Dědičnost v kontraktech služby není podporována.  
  
###  <a name="ActivityGeneration"></a> Generování nakonfigurované aktivity zasílání zpráv  
 Dvě veřejné statické metody jsou přidány do <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivit za účelem podpory generování předem nakonfigurované zpráva aktivity, při použití pracovního postupu první kontrakt služby.  
  
-   <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Aktivitu generovanou tyto metody by měl projít ověřením kontrakt, a proto tyto metody se používá interně jako součást logiku ověření pro <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, A <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> jsou všechny předem nakonfigurované tak, aby odpovídaly importované kontrakt. Na stránce Vlastnosti obsahu pro aktivity v Návrháři pracovních postupů **zpráva** nebo **parametry** oddíly jsou také předem nakonfigurovaná tak, aby odpovídaly kontrakt.  
  
 Selhání WCF kontrakty také zpracovává vrácení samostatnou sadu nakonfigurované <xref:System.ServiceModel.Activities.SendReply> aktivity pro každou z chyb, které se zobrazí v <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Pro ostatní části <xref:System.ServiceModel.Description.OperationDescription> jsou nepodporuje WF služby dnes (např. WebGet nebo WebInvoke chování nebo vlastní operaci chování), rozhraní API bude ignorovat tyto hodnoty jako součást generování a konfigurace. Bude vyvolána žádné výjimky.
