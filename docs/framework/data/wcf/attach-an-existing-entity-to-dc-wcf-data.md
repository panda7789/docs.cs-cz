---
title: 'Postupy: připojení existující entity k DataServiceContext (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 7c8355ea9e9823e7cab6f43c0f3f901948d1d539
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569381"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Postupy: připojení existující entity k DataServiceContext (WCF Data Services)
V případě, že entita již v datové službě existuje, umožňuje Klientská knihovna WCF Data Services připojit objekt, který reprezentuje entitu přímo do <xref:System.Data.Services.Client.DataServiceContext> bez předchozího spuštění dotazu. Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit existující objekt `Customer`, který obsahuje změny, které mají být uloženy do datové služby. Objekt je připojen k kontextu a metoda <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> je volána k označení připojeného objektu jako <xref:System.Data.Services.Client.EntityStates.Modified> před voláním metody <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
