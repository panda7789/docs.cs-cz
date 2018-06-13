---
title: Určování chování služby za běhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 61a81e342a16bd298cbebef2dc733b5ec631839c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807535"
---
# <a name="specifying-service-run-time-behavior"></a>Určování chování služby za běhu
Po dokončení návrhu smlouvy o poskytování služeb ([navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)) a implementace vašeho kontrakt služby ([implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md)) můžete nakonfigurovat chování operaci služby modulu runtime. Toto téma popisuje funkce služby poskytované systémem a operace chování a popisuje, kde najít další informace o vytvoření nové chování. Když některé chování se použijí jako atributy, mnoho se aplikují pomocí konfiguračního souboru aplikace nebo prostřednictvím kódu programu. Další informace o konfiguraci aplikace služby najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Přehled  
 Kontrakt definuje vstupy, výstupy, datové typy a funkce služby daného typu. Implementace kontraktu služby vytvoří třídu, která při konfiguraci s vazbou na adresu, plnit kontrakt implementuje. Smluvními, vazby a informace o adrese jsou všechny známé klientem; bez, nelze provádět klienta pomocí služby.  
  
 Specifika operace, jako je například dělení na vlákna problémy nebo Správa instancí jsou však neprůhledného klientům. Když naimplementujete vaše kontrakt služby, můžete nakonfigurovat velký počet charakteristik operace pomocí *chování*. Chování jsou objekty, které upravují runtime Windows Communication Foundation (WCF), a to nastavením vlastnosti runtime nebo vložením typu přizpůsobení do modulu runtime. Další informace o změně modulu runtime tak, že vytvoříte vlastní chování najdete v tématu [rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> atributy jsou nejčastěji užitečné chování a zveřejněte nejčastěji požadované funkce operaci. Protože jsou atributy, je použít na implementaci služby nebo operace. Další chování, jako <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, jsou obvykle použije pomocí konfiguračního souboru aplikace, přestože je možné použít prostřednictvím kódu programu.  
  
 Toto téma obsahuje přehled <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy, popisuje různé obory, na kterých mohou pracovat chování a poskytuje rychlý popis řadu poskytované systémem chování v různých obory, které může být určen vývojářům WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute a OperationBehaviorAttribute  
 Nejdůležitější chování jsou <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy, které můžete použít k řízení:  
  
-   Instance životnosti  
  
-   Podpora souběžnosti a synchronizace  
  
-   Konfigurace chování  
  
-   Chování transakce  
  
-   Chování serializace  
  
-   Metadata transformace  
  
-   Dobu platnosti relace  
  
-   Filtrování adres a zpracování záhlaví  
  
-   Zosobnění  
  
-   Pokud chcete použít tyto atributy, označte implementace služby nebo operace s atributem příslušné do tohoto oboru a nastavte vlastnosti. Například následující příklad kódu ukazuje implementaci operaci, která používá <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> vlastnost tak, aby vyžadovala, volající tuto operaci podporují zosobnění.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Mnoho vlastností vyžadovat další podporu vazby. Operace, která vyžaduje transakce z klienta musí být například nakonfigurován pro použití vazby, která podporuje sdružení probíhajících transakcí.  
  
### <a name="well-known-singleton-services"></a>Známé Singleton služby  
 Můžete použít <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy pro řízení určité životnosti, obě <xref:System.ServiceModel.InstanceContext> a objekty služby, které implementují operace.  
  
 Například <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak často <xref:System.ServiceModel.InstanceContext> vydání a <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> vlastnosti řízení uvolnění objektu služby.  
  
 Můžete však také vytvořit objekt služby sami a vytvořit hostitele služby pomocí tohoto objektu. To pokud chcete udělat, musíte taky nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.Single> nebo po otevření hostitele služby je vyvolána výjimka.  
  
 Použití <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktor k vytvoření těchto služeb. Poskytuje alternativu k implementaci vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> když chcete zadejte instanci určitý objekt pro použití službou typu singleton. Toto přetížení můžete použít, když vaše typem implementace služby je složité vytvořit (například pokud neimplementuje výchozí veřejný konstruktor, který nemá žádné parametry).  
  
 Všimněte si, že je-li do tohoto konstruktoru objekt, jinak fungovat některé funkce související s k Windows Communication Foundation (WCF) chování vytváření instancí. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je k dispozici instance dobře známé objektu. Podobně se ignoruje jakýmkoli jiným mechanismem verzi instance. <xref:System.ServiceModel.ServiceHost> Třída vždy chová jako kdyby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Další služby, koncový bod, kontrakt a operace chování  
 Chování, služby, jako <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut, provoz mezi celé služby. Například pokud nastavíte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> musí vlákno synchronizace problémy v jednotlivých operací ve služby zpracování sami. Koncový bod chování fungovat přes koncový bod; mnoho chování poskytované systémem koncový bod se pro funkce klienta. Kontrakt chování fungovat na úrovni kontraktu a chování operace upravit operaci doručení.  
  
 Mnoho z těchto projevů jsou definovány pro atributy a provedete pomocí z nich, jako <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy – použitím pro implementaci třídy nebo operace příslušnou službu. Další chování, jako <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior> objekty, se obvykle používají pomocí konfiguračního souboru aplikace, i když se lze také prostřednictvím kódu programu.  
  
 Například publikování metadat se konfiguruje pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objektu. Následující konfigurační soubor aplikace zobrazuje nejběžnější využití.  
  
 [!code-csharp[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.cs#1)]  
  
 Následující části popisují mnoho nejužitečnější poskytované systémem chování, které můžete použít k úpravě runtime doručování služba nebo klienta. Naleznete v tématu referenční určit, jak používat každé z nich.  
  
### <a name="service-behaviors"></a>Chování služby  
 Následujících chování pracovat na služby.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. U služby WCF indikující, zda lze tuto službu spustit [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] režimu kompatibility.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Určuje, jak služba povolí deklarace identity klienta.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Nakonfiguruje přihlašovací údaje služby. Tato třída slouží k zadání přihlašovacích údajů pro službu, jako je certifikát X.509.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Povolí ladění a pomoct informace o funkcích služby WCF.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Ovládací prvky publikování metadat služby a související informace.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Určuje chování auditování událostí zabezpečení.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje nastavení běhu propustnosti, která vám umožní ladit výkon služby.  
  
### <a name="endpoint-behaviors"></a>Koncový bod chování  
 Následujících chování pracovat na koncové body. Mnoho z těchto projevů se používají v klientských aplikacích.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Nakonfiguruje implementaci služby zpětného volání v aplikaci duplexní klienta.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Povolí ladění služby WCF zpětného volání objektu.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Umožňuje uživatelům konfigurovat přihlašovací údaje klienta a služby a také nastavení ověřování přihlašovacích údajů pro použití na klientovi služby.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Používají klienti k určení identifikátor URI (Uniform Resource) pro který by měl být vytvořen kanál přenosu.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Dá pokyn WCF zakázat `MustUnderstand` zpracování.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Dá pokyn modulu runtime použijte synchronního přijímat proces pro kanály.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optimalizuje operace příjmu pro přenosy, které obdrží podporu transakcí.  
  
### <a name="contract-behaviors"></a>Chování kontraktu  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Určuje požadavky funkce, které musíte zadat vazby pro implementaci služby nebo klienta.  
  
### <a name="operation-behaviors"></a>Operace chování  
 Následující operace chování zadejte ovládací prvky pro operace serializace a transakce.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Představuje spuštění chování <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Řídí chování běhové `XmlSerializer` a přidruží ji operaci.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Určuje úroveň, ve kterém přijímá operace služby hlavičku transakce.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md)  
 [Postupy: Řízení vytváření instancí služby](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
