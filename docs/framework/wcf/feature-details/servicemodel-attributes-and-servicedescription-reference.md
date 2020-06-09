---
title: Atributy ServiceModel a odkazy ServiceDescription
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 5e39a63d399edccc580b27ad4bfbc9ab05015ef9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600345"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atributy ServiceModel a odkazy ServiceDescription
*Popis stromu* je hierarchie typů (počínaje <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> třídou), která společně popisuje všechny aspekty služby. Windows Communication Foundation (WCF) používá ke sestavení platného modulu runtime služby, k publikování nástroje Web Services Description Language (WSDL), XML Schema Definition Language (XSD) a kontrolních výrazů zásad (metadata) o službě, kterou můžou klienti použít k připojení a používání služby, a k vygenerování různých kódů a souborů konfiguračního souboru popisů hodnot stromu.  
  
 Toto téma popisuje, jak se získávají vlastnosti související se smlouvou z kontraktu služby a jak se implementují a přidávají do stromu popis. V některých případech se hodnoty atributů převádějí do vlastností chování a chování se pak vloží do stromu popis. Další informace o tom, jak jsou hodnoty stromu popisu převedeny na metadata, naleznete v tématu [ServiceDescription a WSDL reference](servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Mapování operací na strom popisů  
 V aplikacích WCF jsou kontrakty služby modelovány pomocí rozhraní (nebo tříd), které používají atributy k označení rozhraní nebo třídy a jejích metod jako seskupení operací. Při <xref:System.ServiceModel.ServiceHost> otevření třídy se všechny kontrakty a implementace služby projeví a sloučí se s informacemi o konfiguraci do stromu popisů.  
  
 Existují dva typy modelů operací: model *parametrů* a model *kontraktu zpráv* . Model parametru používá spravované metody, které nemají parametr nebo návratový typ hodnoty, který je označen <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> třídou. V tomto modelu vývojáři řídí serializaci parametrů a vrácených hodnot, ale WCF generuje hodnoty, které slouží k naplnění stromu popisu služby a její smlouvy.  
  
 Vazby zadané v konfiguračních souborech jsou načteny přímo do <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> Vlastnosti.  
  
|Vlastnost ServiceBehaviorAttribute|Ovlivněná hodnota stromu popisu|  
|---------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> vlastnost pro všechny operace.|  
|MaxItemsInObjectGraph|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> vlastnost pro všechny operace.|  
  
|ServiceContractAttribute – vlastnost|Ovlivněná hodnota stromu popisu|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> přidáno do všech operací <xref:System.ServiceModel.Description.OperationDescription.Messages%2A> .|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|Platné|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A>a případně podřízené úrovně ochrany. Další informace o hierarchii na úrovni ochrany najdete v tématu [Principy úrovně ochrany](../understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Hodnota ServiceKnownTypesAttribute|Ovlivněná hodnota stromu popisu|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Hodnota atributu OperationContractAttribute|Ovlivněná hodnota stromu popisu|  
|--------------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>pro výstupní zprávu nebo vstupní zprávu v závislosti na kontraktu kontraktu nebo zpětného volání.|  
|AsyncPattern|Pokud má hodnotu true <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> a<xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapuje se na jeden <xref:System.ServiceModel.Description.MessageDescription> v<xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Name|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|Platné|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A>a případně podřízené úrovně ochrany. Další informace o hierarchii na úrovni ochrany najdete v tématu [Principy úrovně ochrany](../understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>pro výstupní zprávu nebo vstupní zprávu v závislosti na kontraktu kontraktu nebo zpětného volání.|  
  
|Hodnota FaultContractAttribute|Ovlivněná hodnota stromu popisu|  
|----------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>v závislosti na kontraktu smlouvy nebo zpětného volání.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Name|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|Platné|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Hodnota DataContractFormatAttribute|Ovlivněná hodnota stromu popisu|  
|---------------------------------------|-------------------------------------|  
|Použití|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A>Hodnota je nastavena <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> pro operaci.|  
  
|Hodnota XmlSerializerFormatAttribute|Ovlivněná hodnota stromu popisu|  
|----------------------------------------|-------------------------------------|  
|Styl|Tato <xref:System.ServiceModel.XmlSerializerFormatAttribute> vlastnost je nastavena <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
|Použití|<xref:System.ServiceModel.XmlSerializerFormatAttribute>Je nastaven v <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
  
|Hodnota TransactionFlowAttribute|Ovlivněná hodnota stromu popisu|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|Do <xref:System.ServiceModel.TransactionFlowAttribute> vlastnosti se přidá jako chování operace <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> .|  
  
|Hodnota MessageContractAttribute|Ovlivněná hodnota stromu popisu|  
|------------------------------------|-------------------------------------|  
|Platné|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|Obálka|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Hodnota třídě MessageHeaderAttribute|Ovlivněná hodnota stromu popisu|  
|----------------------------------|-------------------------------------|  
|Tříd|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Platné|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>pro odpovídající hlavičku v<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Hodnota MessageBodyMemberAttribute|Ovlivněná hodnota stromu popisu|  
|--------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pro odpovídající část v<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>pro odpovídající část v<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Objednání|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>pro odpovídající část v<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Platné|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>pro odpovídající část v<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Hodnota MessageHeaderArrayAttribute|Ovlivněná hodnota stromu popisu|  
|---------------------------------------|-------------------------------------|  
|Tříd|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|Platné|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Hodnota MessagePropertyAttribute|Ovlivněná hodnota stromu popisu|  
|------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Hodnota MessageParameterAttribute|Ovlivněná hodnota stromu popisu|  
|-------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>pro odpovídající část v<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Další informace o tom, jak jsou hodnoty stromu popisu převedeny na metadata, naleznete v tématu [ServiceDescription a WSDL reference](servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Viz také

- [ServiceDescription a referenční informace pro WSDL](servicedescription-and-wsdl-reference.md)
