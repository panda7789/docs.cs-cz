---
title: Vývoj služby pracovního postupu s upřednostněním kontraktu
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 244a6973dde9aba860b08177a42a2ecd64f3479c
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380195"
---
# <a name="contract-first-workflow-service-development"></a>Vývoj služby pracovního postupu s upřednostněním kontraktu
Od verze rozhraní .NET Framework 4.5, Windows Workflow Foundation (WF) funkce lepší integrace mezi službami webové a pracovní postupy ve formuláři stavící do pracovního postupu vývoje. Pracovní postup kontraktem vývojový nástroj umožňuje navrhovat smlouvy v kódu. Nástroj potom automaticky vygeneruje šablonu aktivit v sadě nástrojů pro operace v kontraktu. Toto téma obsahuje přehled, jak aktivity a vlastností služby pracovního postupu se mapují na atributy smlouvy o poskytování služeb. Podrobný příklad vytvoření služby pracovních postupů kontraktem, naleznete v tématu [jak: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
- [Mapování atributů kontraktu služby pracovního postupu atributů](contract-first-workflow-service-development.md#MappingAttributes)  
  
    - [Atributy kontrakt služby](contract-first-workflow-service-development.md#ServiceContract)  
  
    - [Operace kontraktu atributy](contract-first-workflow-service-development.md#OperationContract)  
  
    - [Atributy kontrakt zprávy](contract-first-workflow-service-development.md#MessageContract)  
  
    - [Atributy kontraktu dat.](contract-first-workflow-service-development.md#DataContract)  
  
    - [Atributy kontrakt chyby](contract-first-workflow-service-development.md#FaultContract)  
  
- [Další podporu a informace o implementaci](contract-first-workflow-service-development.md#AdditionalSupport)  
  
    - [Nepodporované funkce kontraktu](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    - [Generování nakonfigurované zasílání zpráv aktivity](contract-first-workflow-service-development.md#ActivityGeneration)  
  
## <a name="MappingAttributes"></a> Mapování atributů kontraktu služby pracovního postupu atributů  
 Tabulky v následujících částech určit různé WCF atributy a vlastnosti a jak jsou mapovány na vlastnosti zasílání zpráv aktivity a v pracovním postupu upřednostnění kontraktu.  
  
- [Atributy kontrakt služby](contract-first-workflow-service-development.md#ServiceContract)  
  
- [Operace kontraktu atributy](contract-first-workflow-service-development.md#OperationContract)  
  
- [Atributy kontrakt zprávy](contract-first-workflow-service-development.md#MessageContract)  
  
- [Atributy kontraktu dat.](contract-first-workflow-service-development.md#DataContract)  
  
- [Atributy kontrakt chyby](contract-first-workflow-service-development.md#FaultContract)  
  
### <a name="ServiceContract"></a> Atributy kontrakt služby  
  
|Název vlastnosti|Podporováno|Popis|Ověření pracovního postupu|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|Ne|Získá nebo nastaví typ kontraktu zpětného volání, pokud kontrakt je oboustranný.|(N/A)|  
|ConfigurationName|Ne|Získá nebo nastaví název používaná k nalezení služby v konfiguračním souboru aplikace.|(N/A)|  
|HasProtectionLevel|Ano|Získá hodnotu určující, zda člen má přiřazena úroveň ochrany.|Receive.ProtectionLevel nesmí být null.|  
|Name|Ano|Získá nebo nastaví název \<portType > element v webové služby WSDL (Description Language).|Receive.ServiceContractName.LocalName by měl odpovídat.|  
|Obor názvů|Ano|Získá nebo nastaví obor názvů \<portType > element v webové služby WSDL (Description Language).|Receive.ServiceContractName.NameSpace by měl odpovídat.|  
|Třída protectionLevel|Ano|Určuje, zda vazba pro kontrakt musí podporovat hodnoty vlastnosti ProtectionLevel.|Receive.ProtectionLevel by měl odpovídat.|  
|SessionMode|Ne|Získá nebo nastaví, zda relace nejsou povoleny, povoleno nebo požadováno.|(N/A)|  
|TypeId|Ne|Při implementaci do odvozené třídy získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(N/A)|  
  
 Sem vložte text pododdílu.  
  
### <a name="OperationContract"></a> Operace kontraktu atributy  
  
|Název vlastnosti|Podporováno|Popis|Ověření pracovního postupu|  
|-------------------|---------------|-----------------|-------------------|  
|Akce|Ano|Získá nebo nastaví akci, WS-Adressing zprávy s požadavkem.|Receive.Action by měl odpovídat.|  
|AsyncPattern|Ne|Označuje, že operace je provedena asynchronně pomocí začátek\<methodName > a End\<methodName > dvojice metody v kontraktu služby.|(N/A)|  
|HasProtectionLevel|Ano|Získá hodnotu určující, zda zprávy pro tuto operaci musí šifrovat podepsané, nebo obojí.|Receive.ProtectionLevel nesmí být null.|  
|IsInitiating|Ne|Získá nebo nastaví hodnotu určující, zda metoda provádí operaci, která může iniciovat relaci na serveru (Pokud tato relace neexistuje).|(N/A)|  
|IsOneWay|Ano|Získá nebo nastaví hodnotu určující, zda operace vrátí zprávy s odpovědí.|(Bez odeslání odpovědi SendReply pro tuto přijímat nebo žádné ReceiveReply pro toto odeslání).|  
|IsTerminating|Ne|Získá nebo nastaví hodnotu určující, zda operace služby způsobí, že server k ukončení relace po zprávy s odpovědí, pokud existuje, je odeslána.|(N/A)|  
|Name|Ano|Získá nebo nastaví název operace.|Receive.OperationName by měl odpovídat.|  
|Třída protectionLevel|Ano|Získává nebo nastavuje hodnotu, která určuje, zda zprávy operace musí šifrovat podepsané, nebo obojí.|Receive.ProtectionLevel by měl odpovídat.|  
|Třídu ReplyAction|Ano|Získá nebo nastaví hodnotu akce SOAP pro odpověď operace.|SendReply.Action by měl odpovídat.|  
|TypeId|Ne|Při implementaci do odvozené třídy získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(N/A)|  
  
### <a name="MessageContract"></a> Atributy kontrakt zprávy  
  
|Název vlastnosti|Podporováno|Popis|Ověření pracovního postupu|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|Ano|Získá hodnotu, která označuje, zda zpráva má úroveň ochrany.|Bez ověřování (Receive.Content a SendReply.Content musí odpovídat typ kontraktu zprávy).|  
|Atribut IsWrapped nastaven|Ano|Získá nebo nastaví hodnotu, která určuje, zda text zprávy má element obálky.|Bez ověřování (Receive.Content a Sendreply.Content musí odpovídat typ kontraktu zprávy).|  
|Třída protectionLevel|Ne|Získává nebo nastavuje hodnotu, která zadat, zda zprávy musí šifrovat, přihlášení, nebo obojí.|(N/A)|  
|TypeId|Ano|Při implementaci do odvozené třídy získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|Bez ověřování (Receive.Content a SendReply.Content musí odpovídat typ kontraktu zprávy).|  
|WrapperName|Ano|Získá nebo nastaví název prvku obálky těla zprávy.|Bez ověřování (Receive.Content a SendReply.Content musí odpovídat typ kontraktu zprávy).|  
|WrapperNamespace|Ne|Získá nebo nastaví obor názvů obálky elementu těla zprávy.|(N/A)|  
  
### <a name="DataContract"></a> Atributy kontraktu dat.  
  
|Název vlastnosti|Podporováno|Popis|Ověření pracovního postupu|  
|-------------------|---------------|-----------------|-------------------|  
|isReference|Ne|Získá nebo nastaví hodnotu určující, jestli chcete zachovat data odkaz objektu.|(N/A)|  
|Name|Ano|Získá nebo nastaví název kontraktu dat pro typ.|Bez ověřování (Receive.Content a SendReply.Content musí odpovídat typ kontraktu zprávy).|  
|Obor názvů|Ano|Získá nebo nastaví obor názvů kontraktu dat pro typ.|Bez ověřování (Receive.Content a SendReply.Content musí odpovídat typ kontraktu zprávy).|  
|TypeId|Ne|Při implementaci do odvozené třídy získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(N/A)|  
  
### <a name="FaultContract"></a> Atributy kontrakt chyby  
  
|Název vlastnosti|Podporováno|Popis|Ověření pracovního postupu|  
|-------------------|---------------|-----------------|-------------------|  
|Akce|Ano|Získá nebo nastaví akci SOAP chybová zpráva, která je zadaná jako součást operace kontraktu.|SendReply.Action by měl odpovídat.|  
|DetailType|Ano|Získá typ serializovatelný objekt, který obsahuje informace o chybě.|SendReply.Content by měl odpovídat typu|  
|HasProtectionLevel|Ne|Získá hodnotu, která označuje, jestli se chybová zpráva SOAP přiřazena úroveň ochrany.|(N/A)|  
|Name|Ne|Získá nebo nastaví název chybová zpráva ve webové služby WSDL (Description Language).|(N/A)|  
|Obor názvů|Ne|Získá nebo nastaví obor názvů chybu protokolu SOAP.|(N/A)|  
|Třída protectionLevel|Ne|Určuje úroveň ochrany, které vyžaduje chybu protokolu SOAP z vazby.|(N/A)|  
|TypeId|Ne|Při implementaci do odvozené třídy získá jedinečný identifikátor pro tento atribut. (Zděděno z atributu).|(N/A)|  
  
## <a name="AdditionalSupport"></a> Další podporu a informace o implementaci  
  
- [Nepodporované funkce kontraktu](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
- [Generování nakonfigurované zasílání zpráv aktivity](contract-first-workflow-service-development.md#ActivityGeneration)  
  
### <a name="UnsupportedFeatures"></a> Nepodporované funkce kontraktu  
  
- Použití TPL (Task Parallel Library) úlohy v kontraktech není podporováno.  
  
- Dědičnost v kontraktech služeb není podporován.  
  
### <a name="ActivityGeneration"></a> Generování nakonfigurované zasílání zpráv aktivity  
 Dvě veřejné statické metody se přidají do <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivit za účelem podpory generování předem nakonfigurované aktivit zpráv při použití služby stavící do pracovního postupu.  
  
- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 Aktivita generovaných tyto metody by měl projít ověřením smlouvy, a proto tyto metody se používají interně jako součást logiky ověření pro <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A>, A <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> jsou všechny předem nakonfigurované tak, aby odpovídaly importovaných kontraktů. Na stránce Vlastnosti obsahu pro aktivity v Návrháři pracovních postupů **zpráva** nebo **parametry** oddíly jsou předem nakonfigurované tak, aby odpovídaly kontrakt.  
  
 Selhání WCF kontrakty zpracovávají také tak, že vrací samostatnou sadu nakonfigurované <xref:System.ServiceModel.Activities.SendReply> aktivit pro každou z chyb, které se zobrazí v <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.  
  
 Jiné části <xref:System.ServiceModel.Description.OperationDescription> , který nepodporuje WF services ještě dnes (např. WebGet nebo WebInvoke chování nebo vlastní operace chování), rozhraní API bude ignorovat tyto hodnoty jako součást generování a konfigurace. Žádné výjimky budou vyvolány.
