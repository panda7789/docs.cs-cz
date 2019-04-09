---
title: Atributy ServiceModel a odkazy ServiceDescription
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 022731d7d6e60d36c5f4a595edc90aaff0586a79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195342"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atributy ServiceModel a odkazy ServiceDescription
*Popis stromu* je hierarchie typů (počínaje <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> třídy), které popisují společně všechny aspekty služby. Windows Communication Foundation (WCF) používá k vytvoření modul runtime platný Publikovat Web Services Description Language (WSDL), schéma XML definice jazyk (XSD) a kontrolní výrazy zásad (metadata) o služby, který můžou klienti použít k popisu stromu Připojte se k a službu používat a generovat různé kódu a konfigurace souboru reprezentace hodnot stromu popis.  
  
 Toto téma popisuje, jak smlouvy související vlastnosti jsou získávány z kontrakt služby a jak jsou implementované a přidán do stromové struktury popis. V některých případech hodnoty atributů jsou převedena na vlastnosti chování a chování se potom vložen do stromu popis. Další informace o jak popis stromu hodnoty se převedou na metadata, najdete v části [ServiceDescription a referenční informace pro WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Operace mapování do stromu popis  
 Aplikace WCF, kontrakty služeb jsou modelovány pomocí rozhraní (nebo třídy), který použít atributy k označení seskupení operací rozhraní nebo třídu a její metody. Když <xref:System.ServiceModel.ServiceHost> třída se otevře, všechny kontrakty služeb a implementace se projeví za a sloučí s informacemi o konfiguraci do stromu popis.  
  
 Existují dva typy modelů operace: *parametr* modelu a *kontraktu zprávy* modelu. Parametr model používá spravované metody, které nemají parametr nebo návratovou hodnotu typu, která je označena <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> třídy. V tomto modelu vývojáři řídit serializace parametry a návratové hodnoty, ale WCF generuje hodnoty, které se používají k naplnění stromu popis služby a její smlouvy.  
  
 Přímo do se načtou vazbách určených v konfiguračních souborech <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> vlastnost.  
  
|Vlastnost atributu ServiceBehaviorAttribute|Hodnota Popis stromu vliv|  
|---------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> vlastnosti pro všechny operace.|  
|MaxItemsInObjectGraph|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> vlastnosti pro všechny operace.|  
  
|Vlastnost ServiceContractAttribute|Hodnota Popis stromu vliv|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> přidán ke všem operacím <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> a pravděpodobně podřazených úrovních ochrany. Další informace o hierarchii úroveň ochrany, naleznete v tématu [úroveň ochrany Principy](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Hodnota ServiceKnownTypesAttribute|Hodnota Popis stromu vliv|  
|--------------------------------------|-------------------------------------|  
|methodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Atribut OperationContractAttribute hodnota|Hodnota Popis stromu vliv|  
|--------------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pro výstupní zprávu nebo zprávu, v závislosti na smlouvy/zpětného volání kontraktu.|  
|AsyncPattern|Při hodnotě true se <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> a <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapuje se na jediného <xref:System.ServiceModel.Description.MessageDescription> v <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Name|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> a pravděpodobně podřazených úrovních ochrany. Další informace o hierarchii úroveň ochrany, naleznete v tématu [úroveň ochrany Principy](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|Třídu ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pro výstupní zprávu nebo zprávu, v závislosti na smlouvy/zpětného volání kontraktu.|  
  
|Hodnota FaultContractAttribute|Hodnota Popis stromu vliv|  
|----------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> v závislosti na smlouvy/zpětného volání kontraktu.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Name|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Hodnota atributu DataContractFormatAttribute|Hodnota Popis stromu vliv|  
|---------------------------------------|-------------------------------------|  
|Použití|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Je hodnota nastavena na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> pro operaci.|  
  
|Atribut XmlSerializerFormatAttribute hodnota|Hodnota Popis stromu vliv|  
|----------------------------------------|-------------------------------------|  
|Styl|To <xref:System.ServiceModel.XmlSerializerFormatAttribute> je nastavena na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
|Použití|<xref:System.ServiceModel.XmlSerializerFormatAttribute> Je nastavena na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
  
|Hodnota TransactionFlowAttribute|Hodnota Popis stromu vliv|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> Se přidá jako chování operaci <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> vlastnost.|  
  
|Hodnota MessageContractAttribute|Hodnota Popis stromu vliv|  
|------------------------------------|-------------------------------------|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Hodnota třídě MessageHeaderAttribute|Hodnota Popis stromu vliv|  
|----------------------------------|-------------------------------------|  
|objekt actor|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Propojení|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Třídu MessageBodyMemberAttribute hodnota|Hodnota Popis stromu vliv|  
|--------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> pro odpovídající část v <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> pro odpovídající část v <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Objednání|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> pro odpovídající část v <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> pro odpovídající část v <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Hodnota MessageHeaderArrayAttribute|Hodnota Popis stromu vliv|  
|---------------------------------------|-------------------------------------|  
|objekt actor|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|Třída protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Propojení|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Hodnota MessagePropertyAttribute|Hodnota Popis stromu vliv|  
|------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Hodnota MessageParameterAttribute|Hodnota Popis stromu vliv|  
|-------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> pro odpovídající část v <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Další informace o jak popis stromu hodnoty se převedou na metadata, najdete v části [ServiceDescription a referenční informace pro WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Viz také:

- [ServiceDescription and WSDL Reference](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
