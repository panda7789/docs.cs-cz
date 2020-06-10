---
title: 'Postupy: Vytvoření jednosměrného kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 42c056c9b56ed1245290cd66833cc6565f517b66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593448"
---
# <a name="how-to-create-a-one-way-contract"></a>Postupy: Vytvoření jednosměrného kontraktu
V tomto tématu se dozvíte o základních krocích pro vytváření metod, které používají jednosměrný kontrakt. Tyto metody vyvolávají operace ve službě Windows Communication Foundation (WCF) z klienta, ale neočekávají odpověď. Tento typ kontraktu je možné použít například k publikování oznámení mnoha předplatitelům. Můžete také použít jednosměrné kontrakty při vytváření duplexních kontraktů (obousměrný), který umožňuje klientům a serverům vzájemně komunikovat nezávisle na sobě, takže mohou iniciovat volání do druhé. To může mít za následek to, že server může v případě jednosměrných volání klienta nakládat jako s událostmi. Podrobné informace o tom, jak zadat jednosměrné metody, naleznete v části <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Property a <xref:System.ServiceModel.OperationContractAttribute> Class.  
  
 Další informace o vytvoření klientské aplikace pro duplexní smlouvu najdete v tématu [Postup: přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Pracovní ukázku naleznete v ukázce [jednosměrového](../samples/one-way.md) vzorku.  
  
### <a name="to-create-a-one-way-contract"></a>Postup vytvoření jednosměrného kontraktu  
  
1. Vytvořte kontrakt služby tím, že použijete <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní, které definuje metody, které má služba implementovat.  
  
2. Určuje, které metody v rozhraní může klient vyvolávat použitím <xref:System.ServiceModel.OperationContractAttribute> třídy na ně.  
  
3. Nastavte vlastnost na hodnotu, která nesmí mít žádný výstup (žádnou návratovou hodnotu a žádné parametry ref) jako jednosměrný <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` . Všimněte si, že operace, které přenesou <xref:System.ServiceModel.OperationContractAttribute> třídu, ve výchozím nastavení vyhovět kontraktu požadavku a odpovědi, protože tato <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost je `false` standardně nastavená. Proto je nutné explicitně zadat hodnotu vlastnosti atributu, pokud chcete použít `true` jednosměrný kontrakt pro metodu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje kontrakt pro službu, která obsahuje několik jednosměrných metod. Všechny metody mají jednosměrné kontrakty s výjimkou `Equals` , která má výchozí hodnotu Request-Reply a vrací výsledek.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Navrhování a implementace služeb](../designing-and-implementing-services.md)
- [Postupy: Definování kontraktu služby](../how-to-define-a-wcf-service-contract.md)
- [Relace](../samples/session.md)
- [Postupy: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md)
