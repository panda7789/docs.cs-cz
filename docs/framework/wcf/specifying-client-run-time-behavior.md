---
title: Nastavení běhového chování klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: bc104c4f51ebc64154bd3d9b39ac2bca13b2fab1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="specifying-client-run-time-behavior"></a>Nastavení běhového chování klienta
Pokud chcete změnit chování běhové tak, aby vyhovovala klientská aplikace lze nakonfigurovat klienty Windows Communication Foundation (WCF), jako jsou služby Windows Communication Foundation (WCF). Tři atributy jsou k dispozici pro určení chování klienta. Můžete použít objekty zpětné volání klienta duplexní <xref:System.ServiceModel.CallbackBehaviorAttribute> a <xref:System.ServiceModel.Description.CallbackDebugBehavior> atributy změnit jejich chování. Pro atribut, <xref:System.ServiceModel.Description.ClientViaBehavior>, lze použít k oddělení logické cílové z cílového okamžitou síť. Kromě toho můžete použít typů zpětného volání duplexní klientů některá chování straně služby. Další informace najdete v tématu [určení chování služby Run-Time](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Pomocí třídy CallbackBehaviorAttribute  
 Můžete nakonfigurovat nebo rozšíření pomocí chování při spuštění implementace kontraktu zpětného volání v aplikaci klienta <xref:System.ServiceModel.CallbackBehaviorAttribute> třídy. Tento atribut provádí podobné funkce pro třídu zpětného volání, jako <xref:System.ServiceModel.ServiceBehaviorAttribute> třída, s výjimkou vytváření instancí nastavení chování a transakce.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Třída musí být použita na třídu, která implementuje kontrakt zpětného volání. Pokud se aplikují implementaci podavače kontrakt, <xref:System.InvalidOperationException> v době běhu je vyvolána výjimka. Následující příklad kódu ukazuje <xref:System.ServiceModel.CallbackBehaviorAttribute> třída na objekt zpětného volání, která používá <xref:System.Threading.SynchronizationContext> objektem pro určení vlákno přeuspořádat, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> vlastnost vynutit zpráva ověření a <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> vlastnost, která má vrátit výjimky jako <xref:System.ServiceModel.FaultException> objekty ve službě pro účely ladění.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Použití CallbackDebugBehavior pro povolení toku informací spravované výjimky  
 Můžete povolit tok spravovaných výjimek informací v objektu zpětné volání klienta zpět na službu pro účely ladění nastavením <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost `true` souboru buď programově, nebo z konfigurace aplikace.  
  
 Vrací informace o spravovaných výjimce Services může být bezpečnostní riziko, protože podrobnosti o výjimce zveřejnění informace o interní klientovi implementace, která Neautorizováno služby využít. Kromě toho i když <xref:System.ServiceModel.Description.CallbackDebugBehavior> vlastnosti lze nastavit také prostřednictvím kódu programu, může být snadno nezapomněli zakázat <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> při nasazování.  
  
 Z důvodu zabezpečení problémy související se situací důrazně doporučujeme:  
  
-   Použití konfiguračního souboru aplikace nastavit hodnotu <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost `true`.  
  
-   Můžete udělat tak pouze v řídí ladění scénáře.  
  
 Následující příklad kódu ukazuje klienta konfiguračního souboru, který se dá pokyn WCF k vrácení informací spravované výjimky z klienta objekt zpětného volání ve zprávách protokolu SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Pomocí ClientViaBehavior chování  
 Můžete použít <xref:System.ServiceModel.Description.ClientViaBehavior> chování k určení Uniform Resource Identifier, pro který by měl být vytvořen kanál přenosu. Používejte toto chování, když cílový okamžitou síť není určený procesor zprávy. To umožňuje vícenásobných konverzace, když je volající aplikace nemusí nutně vědět ultimate cílové nebo když cíl `Via` hlavičky není adresu.  
  
## <a name="see-also"></a>Viz také  
 [Určování chování služby za běhu](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
