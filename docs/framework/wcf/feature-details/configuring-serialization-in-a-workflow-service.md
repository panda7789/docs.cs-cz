---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488869"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurace serializace ve službě pracovních postupů
Služby pracovních postupů jsou služby Windows Communication Foundation (WCF), a tak mít možnost buď pomocí <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>. Při zápisu mimo pracovní postup služby typu serializátoru je zadán pro kontrakt služby nebo operace. Při vytváření pracovního postupu služby WCF v kódu nezadáte tyto smlouvy, ale místo jsou generovány při běhu pomocí odvození kontrakt. Další informace o odvození kontrakt najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializátor je zadán pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost. To je možné nastavit v návrháři, jak je znázorněno na následujícím obrázku.  
  
 ![Nastavení serializátoru](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 Serializátor lze nastavit i v kódu, jak je znázorněno v následujícím příkladu  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Známé typy lze na i služeb pracovních postupů. Další informace o známé typy najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Známé typy mohou být zadané v Návrháři nebo v kódu. Chcete-li zadat známé typy v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v okně Vlastnosti pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.  
  
 ![Vlastnost KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 Tato akce zobrazí Editor kolekcí typ, který vám umožní vyhledat a zadejte známé typy.  
  
 ![Přidání známé typy](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 Klikněte **přidat nový typ** propojit a pomocí rozevíracího dolů vyberte nebo vyhledejte typu můžete přidat do kolekce známé typy. Určete známé typy v kódu pomocí <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 Chcete-li zobrazit kompletní příklad znázorňující postup konfigurace serializace pro služby pracovního postupu najdete v části [formátování zprávy v služeb pracovních postupů](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).
