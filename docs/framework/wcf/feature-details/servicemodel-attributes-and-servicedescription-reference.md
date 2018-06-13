---
title: Atributy ServiceModel a odkazy ServiceDescription
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: cc7c36ff7a1c81227f118ee7113be8f7f9eb2e9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505967"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>Atributy ServiceModel a odkazy ServiceDescription
*Popis stromu* je hierarchie typů (počínaje <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> třída) společně popisují všechny aspekty služby. Windows Communication Foundation (WCF) používá k vytvoření platný služby modulu runtime Publikovat Web Services Description Language (WSDL), jazyk definice schématu XML (XSD) a výrazy zásad (metadata) o službě, který můžou klienti používat pro popis stromu připojení k a používat službu a ke generování různé kódu a konfigurace souborů reprezentace strom hodnot popis.  
  
 Toto téma popisuje, jak kontrakt související vlastnosti jsou získávány z kontrakt služby, a jak jsou implementované a přidány do stromu popis. V některých případech hodnoty atributu se převedou na chování vlastnosti a chování se pak vloží do stromu popis. Další informace o tom, jak jsou hodnoty stromu popis převést do metadat najdete v tématu [ServiceDescription a referenční dokumentace schématu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Operace mapování do stromu popis  
 V aplikacích WCF, jsou modelovány kontraktů služby pomocí rozhraní (nebo třídy) k označení rozhraní nebo třídy a její metody jako seskupení operací, použijte atributy. Když <xref:System.ServiceModel.ServiceHost> třída je otevřen, všechny kontraktů služby a implementace jsou projeví přes a sloučit s informace o konfiguraci do stromu popis.  
  
 Existují dva typy modelů operace: *parametr* modelu a *kontrakt zprávy* modelu. Parametr model používá spravované metody, které nemají parametru nebo typu návratovou hodnotu, která je označena kvalifikátorem <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> třídy. V tomto modelu vývojáři řídit serializace parametry a návratové hodnoty, ale WCF generuje hodnoty, které slouží k naplnění stromu popis pro tuto službu a její smlouvy.  
  
 Jsou zadány v konfiguračních souborech vazby načíst přímo do <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> vlastnost.  
  
|Vlastnost ServiceBehaviorAttribute|Hodnota stromu popis vliv|  
|---------------------------------------|-------------------------------------|  
|Název|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> vlastnost pro všechny operace.|  
|maxItemsInObjectGraph|Nastaví <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> vlastnost pro všechny operace.|  
  
|Vlastnost ServiceContractAttribute|Hodnota stromu popis vliv|  
|---------------------------------------|-------------------------------------|  
|Třída CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> přidán ke všem operacím <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> a které by mohly mít podřízených úrovních ochrany. Další informace o hierarchii úroveň ochrany najdete v tématu [úroveň ochrany Principy](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|Hodnota ServiceKnownTypesAttribute|Hodnota stromu popis vliv|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|Hodnota OperationContractAttribute|Hodnota stromu popis vliv|  
|--------------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pro výstup zpráv nebo vstupní zprávy, v závislosti na kontrakt kontrakt/zpětného volání.|  
|Parametru AsyncPattern|V případě hodnoty true <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> a <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Mapy na jednu <xref:System.ServiceModel.Description.MessageDescription> v <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Název|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> a které by mohly mít podřízených úrovních ochrany. Další informace o hierarchii úroveň ochrany najdete v tématu [úroveň ochrany Principy](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> pro výstup zpráv nebo vstupní zprávy, v závislosti na kontrakt kontrakt/zpětného volání.|  
  
|Hodnota FaultContractAttribute|Hodnota stromu popis vliv|  
|----------------------------------|-------------------------------------|  
|Akce|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> v závislosti na kontrakt kontrakt/zpětného volání.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Název|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|Hodnota atributu DataContractFormatAttribute|Hodnota stromu popis vliv|  
|---------------------------------------|-------------------------------------|  
|Použití|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Hodnota se nastavuje na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> pro operaci.|  
  
|Hodnota XmlSerializerFormatAttribute|Hodnota stromu popis vliv|  
|----------------------------------------|-------------------------------------|  
|Styl|To <xref:System.ServiceModel.XmlSerializerFormatAttribute> je nastavena na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
|Použití|<xref:System.ServiceModel.XmlSerializerFormatAttribute> Je nastavený na <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> pro operaci.|  
  
|Hodnota TransactionFlowAttribute|Hodnota stromu popis vliv|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> Se přidá jako chování, operaci <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> vlastnost.|  
  
|Hodnota MessageContractAttribute|Hodnota stromu popis vliv|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|Hodnota MessageHeaderAttribute|Hodnota stromu popis vliv|  
|----------------------------------|-------------------------------------|  
|Objektu actor|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Atribut MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Název|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Předávání|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> odpovídající hlavičky v <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Hodnota MessageBodyMemberAttribute|Hodnota stromu popis vliv|  
|--------------------------------------|-------------------------------------|  
|Název|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> pro odpovídající součástí <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> pro odpovídající součástí <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Pořadí|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> pro odpovídající součástí <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> pro odpovídající součástí <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|Hodnota MessageHeaderArrayAttribute|Hodnota stromu popis vliv|  
|---------------------------------------|-------------------------------------|  
|Objektu actor|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|Atribut MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Název|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Obor názvů|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Předávání|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|Hodnota MessagePropertyAttribute|Hodnota stromu popis vliv|  
|------------------------------------|-------------------------------------|  
|Název|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|Hodnota MessageParameterAttribute|Hodnota stromu popis vliv|  
|-------------------------------------|-------------------------------------|  
|Název|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> pro odpovídající součástí <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Další informace o tom, jak jsou hodnoty stromu popis převést do metadat najdete v tématu [ServiceDescription a referenční dokumentace schématu WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [ServiceDescription a referenční informace pro WSDL](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
