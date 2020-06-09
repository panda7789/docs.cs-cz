---
title: Konfigurace serializace ve službě pracovních postupů
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597537"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Konfigurace serializace ve službě pracovních postupů
Služby pracovních postupů jsou služby Windows Communication Foundation (WCF), které mají možnost použít buď <xref:System.Runtime.Serialization.DataContractSerializer> (výchozí), nebo <xref:System.Xml.Serialization.XmlSerializer> . Při psaní služeb nesouvisejících s pracovními postupy je typ serializátoru, který se má použít, specifikovaný v kontraktu služby nebo operace. Při vytváření služeb pracovních postupů WCF neurčíte tyto smlouvy v kódu, ale místo toho jsou generovány za běhu odvozenou od smlouvy. Další informace o odvození smlouvy najdete v tématu [Použití kontraktů v pracovním postupu](using-contracts-in-workflow.md).  Serializátor je určen pomocí <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> Vlastnosti. To lze nastavit v návrháři, jak je znázorněno na následujícím obrázku.  
  
 ![Nastavení vlastnosti SerializerOption v okně Vlastnosti.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Serializátor lze také nastavit v kódu, jak je znázorněno v následujícím příkladu.  
  
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
  
  Známé typy lze také zadat ve službě pracovního postupu. Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md). Známé typy lze zadat v Návrháři nebo v kódu. Chcete-li v Návrháři zadat známé typy, klikněte na tlačítko se třemi tečkami vedle vlastnosti KnownTypes v **okně Vlastnosti** <xref:System.ServiceModel.Activities.Receive> aktivity, jak je znázorněno na následujícím obrázku.
  
 ![Snímek obrazovky dialogového okna vlastnosti KnownTypes](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Tím se zobrazí Editor kolekce typů, který umožňuje vyhledat a zadat známé typy.  
  
 ![Snímek obrazovky editoru kolekcí typů](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Klikněte na odkaz **Přidat nový typ** a pomocí rozevírací nabídky vyberte nebo vyhledejte typ, který chcete přidat do kolekce známých typů. Chcete-li zadat známé typy v kódu, použijte <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> vlastnost, jak je znázorněno v následujícím příkladu.  
  
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
