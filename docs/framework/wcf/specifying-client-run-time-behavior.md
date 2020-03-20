---
title: Nastavení běhového chování klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f9c22d25bedc36b3515538a8785b488aaa547990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143236"
---
# <a name="specifying-client-run-time-behavior"></a>Nastavení běhového chování klienta
Klienty WCF (Windows Communication Foundation), jako jsou služby WCF (Windows Communication Foundation), lze nakonfigurovat tak, aby upravovaly chování za běhu tak, aby vyhovovalo klientské aplikaci. Pro určení chování klienta za běhu jsou k dispozici tři atributy. Duplexní klient zpětné volání <xref:System.ServiceModel.CallbackBehaviorAttribute> <xref:System.ServiceModel.Description.CallbackDebugBehavior> objekty můžete použít atributy a upravit jejich chování za běhu. Druhý atribut <xref:System.ServiceModel.Description.ClientViaBehavior>, lze oddělit logický cíl od bezprostředního cíle sítě. Kromě toho duplexní typy zpětného volání klienta můžete použít některé chování na straně služby. Další informace naleznete [v tématu Určení chování za běhu služby](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Použití atributu CallbackBehaviorAttribute  
 Můžete nakonfigurovat nebo rozšířit provádění chování implementace smlouvy zpětného volání <xref:System.ServiceModel.CallbackBehaviorAttribute> v klientské aplikaci pomocí třídy. Tento atribut provádí podobnou funkci pro <xref:System.ServiceModel.ServiceBehaviorAttribute> třídu zpětného volání jako třída, s výjimkou instance chování a nastavení transakce.  
  
 Třída <xref:System.ServiceModel.CallbackBehaviorAttribute> musí být použita pro třídu, která implementuje kontrakt zpětného volání. Pokud platí pro implementaci neduplexní smlouvy, je vyvolána <xref:System.InvalidOperationException> výjimka za běhu. Následující příklad kódu <xref:System.ServiceModel.CallbackBehaviorAttribute> ukazuje třídu na objekt <xref:System.Threading.SynchronizationContext> zpětného volání, který používá <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> objekt k určení vlákna <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> k zařazování do, vlastnost vynutit ověření zprávy a vlastnost vrátit výjimky jako <xref:System.ServiceModel.FaultException> objekty do služby pro účely ladění.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Použití callbackDebugBehavior k povolení toku informací o spravované výjimce  
 Tok informací o spravovaných výjimkách v objektu zpětného volání klienta <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> můžete `true` povolit zpětným způsobem pro účely ladění nastavením vlastnosti na programovou nebo z konfiguračního souboru aplikace.  
  
 Vrácení informací o spravované výjimce do služeb může být bezpečnostním rizikem, protože podrobnosti o výjimce zveřejňují informace o implementaci interního klienta, které by mohly používat neautorizované služby. Kromě toho, <xref:System.ServiceModel.Description.CallbackDebugBehavior> i když vlastnosti lze také nastavit programově, <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> může být snadno zapomenout zakázat při nasazování.  
  
 Z důvodu souvisejících problémů se zabezpečením se důrazně doporučuje:  
  
- K nastavení hodnoty vlastnosti <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> na `true`.  
  
- To provést pouze v řízených scénářích ladění.  
  
 Následující příklad kódu ukazuje konfigurační soubor klienta, který instruuje WCF vrátit spravované informace o výjimce z objektu zpětného volání klienta ve zprávách SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  

## <a name="using-the-clientviabehavior-behavior"></a>Použití chování ClientViaBehavior  
 <xref:System.ServiceModel.Description.ClientViaBehavior> Toto chování můžete použít k určení identifikátoru jednotného prostředku, pro který má být vytvořen kanál přenosu. Toto chování použijte v případě, že bezprostřední cíl sítě není zamýšlenýprocesor zprávy. To umožňuje konverzace s více směrováními, když volající aplikace nemusí `Via` nutně znát konečný cíl nebo pokud cílová hlavička není adresa.  
  
## <a name="see-also"></a>Viz také

- [Určování chování služby za běhu](specifying-service-run-time-behavior.md)
