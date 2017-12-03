---
title: "Konfigurace serializace ve službě pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78f963f61c7ec67d6104a90c047ce78b0470568a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurace serializace ve službě pracovních postupů
Služby pracovních postupů jsou [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služeb a tak mít možnost buď pomocí <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>. Při zápisu mimo pracovní postup služby typu serializátoru je zadán pro kontrakt služby nebo operace. Při vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] měnící nezadáte tyto služby pracovních postupů v kódu, ale místo jsou generovány při běhu pomocí odvození kontrakt. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Sbalit odvození najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializátor je zadán pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost. To je možné nastavit v návrháři, jak je znázorněno na následujícím obrázku.  
  
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
  
 Známé typy lze na i služeb pracovních postupů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Známé typy najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Známé typy mohou být zadané v Návrháři nebo v kódu. Chcete-li zadat známé typy v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v okně Vlastnosti pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.  
  
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
