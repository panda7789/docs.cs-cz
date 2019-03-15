---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843926"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurace serializace ve službě pracovních postupů
Služby pracovních postupů jsou služby Windows Communication Foundation (WCF) a tak mají možnost používat buď <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí) nebo <xref:System.Xml.Serialization.XmlSerializer>. Při psaní mimo pracovní postup služby typu serializátoru je zadán u kontraktu služby nebo operace. Při vytváření služby pracovního postupu WCF nezadáte těchto smluv v kódu, ale místo toho jsou generovány v době běhu podle odvození kontraktu. Další informace o odvození smlouvy najdete v tématu [použití kontraktů v pracovním postupu](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Serializátoru, který je určen pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> vlastnost. To může být nastavit v návrháři, jak je znázorněno na následujícím obrázku.  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serializátor můžete nastavit také v kódu, jak je znázorněno v následujícím příkladu  
  
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
  
  Známé typy se dá nastavit na také služby pracovního postupu. Další informace o známé typy najdete v tématu [známé typy kontraktů dat](data-contract-known-types.md). Známé typy se dá nastavit v Návrháři nebo v kódu. K určení známých typů v návrháři, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okno vlastností** pro <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.   
  
 ![Snímek obrazovky dialogového okna Vlastnosti KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Zobrazí se Editor typu kolekce, která umožňuje hledat a zadejte známých typů.  
  
 ![Snímek obrazovky Editor typu kolekce.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Klikněte na tlačítko **přidat nový typ** propojit a pomocí rozevíracího seznamu ji můžete vybrat nebo vyhledejte typ můžete přidat do kolekce známých typů. K určení známé typy kódu používá <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.  
  
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
