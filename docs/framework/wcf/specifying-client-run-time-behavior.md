---
title: Nastavení běhového chování klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 075f62526ace1ac49d12e1bdec39d8df4b0a3ff1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321412"
---
# <a name="specifying-client-run-time-behavior"></a>Nastavení běhového chování klienta
Klienti Windows Communication Foundation (WCF), jako jsou služby Windows Communication Foundation (WCF), je možné nakonfigurovat tak, aby upravili chování za běhu tak, aby vyhovovaly klientské aplikaci. Pro určení chování při běhu klienta jsou k dispozici tři atributy. Objekty duplexního zpětného volání klienta mohou použít atributy <xref:System.ServiceModel.CallbackBehaviorAttribute> a <xref:System.ServiceModel.Description.CallbackDebugBehavior> pro úpravu chování při běhu. Druhý atribut <xref:System.ServiceModel.Description.ClientViaBehavior> lze použít k oddělení logického cíle z bezprostředního síťového cíle. Kromě toho můžou některé z chování na straně služby používat i duplexní typy zpětného volání klienta. Další informace najdete v tématu [Určení chování služby za běhu](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Použití CallbackBehaviorAttribute  
 Chování provádění implementace kontraktu zpětného volání v klientské aplikaci můžete nakonfigurovat nebo roztáhnout pomocí třídy <xref:System.ServiceModel.CallbackBehaviorAttribute>. Tento atribut provádí podobnou funkci pro třídu zpětného volání jako třídu <xref:System.ServiceModel.ServiceBehaviorAttribute> s výjimkou chování vytváření instancí a nastavení transakcí.  
  
 Třídu <xref:System.ServiceModel.CallbackBehaviorAttribute> je nutné použít pro třídu, která implementuje kontrakt zpětného volání. Při použití na neduplexní implementaci kontraktu je vyvolána výjimka <xref:System.InvalidOperationException> v době běhu. Následující příklad kódu ukazuje třídu <xref:System.ServiceModel.CallbackBehaviorAttribute> na objektu zpětného volání, který používá objekt <xref:System.Threading.SynchronizationContext> k určení vlákna k zařazení do, vlastnosti <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> pro vykonání ověření zprávy a vlastnost <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> pro vrácení výjimek jako objektů <xref:System.ServiceModel.FaultException> do Služba pro účely ladění.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Povolení toku informací o spravovaných výjimkách pomocí CallbackDebugBehavior  
 Můžete povolit tok informací o spravovaných výjimkách v objektu zpětného volání klienta zpátky do služby pro účely ladění nastavením vlastnosti <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> na `true` buď programově, nebo z konfiguračního souboru aplikace.  
  
 Vrácení spravovaných informací o výjimkách do služeb může představovat bezpečnostní riziko, protože podrobnosti o výjimce zpřístupňují informace o implementaci interního klienta, které by mohly používat neautorizované služby. Kromě toho, i když lze vlastnosti <xref:System.ServiceModel.Description.CallbackDebugBehavior> nastavit také programově, lze při nasazování snadno zapomenout <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> zakázat.  
  
 Vzhledem k problémům se zabezpečením se důrazně doporučuje:  
  
- Pomocí konfiguračního souboru aplikace nastavíte hodnotu vlastnosti <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> na `true`.  
  
- Provedete to jenom v řízených scénářích ladění.  
  
 Následující příklad kódu ukazuje konfigurační soubor klienta, který instruuje technologii WCF, aby vrátila informace o spravované výjimce z objektu zpětného volání klienta ve zprávách SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Použití chování ClientViaBehavior  
 Pomocí chování <xref:System.ServiceModel.Description.ClientViaBehavior> můžete určit identifikátor URI, pro který má být vytvořen přenosový kanál. Toto chování použijte v případě, že okamžité síťové umístění není zamýšleným procesorem zprávy. Tím se povolí konverzace s více segmenty, když volající aplikace nutně neví o konečném cíli nebo když cílová hlavička `Via` není adresou.  
  
## <a name="see-also"></a>Viz také:

- [Určování chování služby za běhu](specifying-service-run-time-behavior.md)
