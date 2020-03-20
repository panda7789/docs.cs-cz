---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185337"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurace serializace ve službě pracovních postupů
Pracovní postupy služby jsou Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> služby a tak <xref:System.Xml.Serialization.XmlSerializer>mají možnost použít (výchozí) nebo . Při zápisu služeb bez pracovního postupu je typ serializátoru, který chcete použít, určen ve smlouvě o službě nebo operaci. Při vytváření služeb pracovního postupu WCF nezadáte tyto smlouvy v kódu, ale spíše jsou generovány za běhu podle odvození smlouvy. Další informace o odvození smlouvy naleznete v [tématu Použití smluv v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializátor je <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> určen pomocí vlastnosti. To lze nastavit v návrháři, jak je znázorněno na následujícím obrázku.  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serializátor lze také nastavit v kódu, jak je znázorněno v následujícím příkladu,  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  Známé typy lze zadat také ve službách pracovního postupu. Další informace o známých typech naleznete v [tématu Data Contract Known Types](data-contract-known-types.md). Známé typy lze zadat v návrháři nebo v kódu. Chcete-li určit známé typy v návrháři, klepněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okně Vlastnosti** pro aktivitu, <xref:System.ServiceModel.Activities.Receive> jak je znázorněno na následujícím obrázku.
  
 ![Snímek obrazovky s dialogovým oknem vlastnosti KnownTypes](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Zobrazí se Editor kolekcí typů, který umožňuje vyhledávat a zadávat známé typy.  
  
 ![Snímek obrazovky editoru kolekcí typů](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Klikněte na odkaz **Přidat nový typ** a pomocí rozevíracího pole vyberte nebo vyhledejte typ, který chcete přidat do kolekce známých typů. Chcete-li určit známé <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> typy v kódu, použijte vlastnost, jak je znázorněno v následujícím příkladu.  
  
```csharp
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
