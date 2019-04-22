---
title: Nastavení běhového chování klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f750978eaa617a5505bb27a1535797320a76b0d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164369"
---
# <a name="specifying-client-run-time-behavior"></a>Nastavení běhového chování klienta
Klienti Windows Communication Foundation (WCF), jako jsou služby Windows Communication Foundation (WCF), lze nastavit k úpravě chování za běhu tak, aby odpovídala klientské aplikace. Tři atributy jsou k dispozici pro určení chování klienta za běhu. Můžete použít objekty zpětného volání klienta duplexní <xref:System.ServiceModel.CallbackBehaviorAttribute> a <xref:System.ServiceModel.Description.CallbackDebugBehavior> atributů, které mají změna jejich chování za běhu. Ostatní atributy <xref:System.ServiceModel.Description.ClientViaBehavior>, můžete použít k oddělení logické cíl z cílového okamžitou síť. Kromě toho můžete použít typy zpětného volání klienta duplexní některá chování straně služby. Další informace najdete v tématu [určení chování za běhu služby](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Použití třídu CallbackBehaviorAttribute  
 Můžete nakonfigurovat nebo rozšíření pomocí chování při spuštění provádění zpětného volání kontraktu v klientské aplikaci <xref:System.ServiceModel.CallbackBehaviorAttribute> třídy. Tento atribut má podobnou funkci zpětného volání třídy jako <xref:System.ServiceModel.ServiceBehaviorAttribute> třídy, s výjimkou vytváření instancí nastavení chování a transakce.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Třídy je nutné použít na třídu, která implementuje tento kontrakt zpětného volání. Pokud se použije pro implementaci podavače kontraktu <xref:System.InvalidOperationException> je vyvolána výjimka za běhu. Následující příklad kódu ukazuje <xref:System.ServiceModel.CallbackBehaviorAttribute> třídy pro objekt zpětného volání, která používá <xref:System.Threading.SynchronizationContext> objektem pro určení vlákno zařazení, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> vlastnost k vynucení ověřování zpráv a <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> vlastnost vrátit výjimky jako <xref:System.ServiceModel.FaultException> objektů ve službě pro účely ladění.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Povolení toku informací o řízené výjimce pomocí CallbackDebugBehavior  
 Může být povolen tok informací o řízené výjimce do objektu zpětného volání klienta zpět do služby pro účely ladění tím, že nastavíte <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost `true` souboru prostřednictvím kódu programu nebo z konfigurace aplikace.  
  
 Vrací informace o spravované výjimce ke službám může představovat bezpečnostní riziko, protože podrobnosti o výjimce zobrazení informací o informace o klientovi interní implementace, která není autorizovaný. služby použít. Kromě toho Přestože <xref:System.ServiceModel.Description.CallbackDebugBehavior> vlastnosti můžete nastavit také prostřednictvím kódu programu, může být snadné zapomenout zakázat <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> při nasazování.  
  
 Z důvodu zabezpečení problematiku důrazně doporučujeme:  
  
-   Konfigurační soubor aplikace můžete nastavit hodnotu <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> vlastnost `true`.  
  
-   Provedete pouze v řízené ladění scénářů.  
  
 Následující příklad kódu ukazuje klienta konfigurační soubor, který dává pokyn k vrácení informací o spravované výjimce z klienta objekt zpětného volání v zprávy protokolu SOAP WCF.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Použití ClientViaBehavior chování  
 Můžete použít <xref:System.ServiceModel.Description.ClientViaBehavior> chování k určení Uniform Resource Identifier, pro který by měl být vytvořen přenosový kanál. Použijte toto chování, pokud cíl okamžitou síť není zamýšlený procesoru zprávy. To umožňuje vícenásobným směrováním konverzace, pokud volající aplikace neví nutně ultimate cíl nebo pokud cíl `Via` záhlaví není adresa.  
  
## <a name="see-also"></a>Viz také:

- [Určování chování služby za běhu](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
