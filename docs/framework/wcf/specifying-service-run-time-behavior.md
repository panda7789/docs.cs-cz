---
title: Určování chování služby za běhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 9fa6e4114e9579079705700708840f2814b03b99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186872"
---
# <a name="specifying-service-run-time-behavior"></a>Určování chování služby za běhu
Jakmile jste vytvořili kontrakt služby ([navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)) a implementovat vaše smlouva na služby ([implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)) můžete nakonfigurovat chování operace služby modulu runtime. Toto téma popisuje poskytované systémem služby a operace chování a popisuje, kde najdete další informace k vytvoření nové chování. Některá chování se použijí jako atributy, mnoho se aplikují pomocí konfiguračního souboru aplikace nebo prostřednictvím kódu programu. Další informace o konfiguraci aplikace služby, najdete v části [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Přehled  
 Kontrakt definuje vstupů, výstupů, datové typy a funkce služby daného typu. Implementace kontraktu služby vytvoří třídu, která, když je nakonfigurována s vazbou na adrese, splňuje kontrakt implementuje. Smluvní, vazby a informace o adrese jsou všechny známé klientem; bez nich klienta nemůže provádět pomocí služby.  
  
 Specifika operace, jako je například práce s vlákny problémy nebo Správa instancí, ale neprůhledné pro klienty. Když naimplementujete servisní smlouvy, velký počet vlastností operace můžete nakonfigurovat pomocí *chování*. Chování jsou objekty, které upravují modul runtime Windows Communication Foundation (WCF) tak, že nastavíte vlastnost modulu runtime nebo vložením přizpůsobení typů do modulu runtime. Další informace o změnách tak, že vytvoříte uživatelem definované chování modulu runtime, naleznete v tématu [rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> vystavení nejčastěji požadované funkce operace a atributy jsou nejčastěji užitečné chování. Protože jsou atributy, použít je pro implementaci služby nebo operace. Další chování, například <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, jsou obvykle použity pomocí konfiguračního souboru aplikace, i když je můžete využít prostřednictvím kódu programu.  
  
 Toto téma obsahuje přehled <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy, jsou popsány různé obory, na kterých může pracovat chování a poskytuje stručný popis mnoha poskytované systémem chování v různých oborech, které mohou být zajímavé pro vývojáře technologie WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>Atribut ServiceBehaviorAttribute a OperationBehaviorAttribute  
 Jsou nejdůležitějšího chování <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy, které můžete použít k řízení:  
  
-   Životnost instance  
  
-   Podpora souběžnosti a synchronizace  
  
-   Konfigurace chování  
  
-   Chování při transakci  
  
-   Chování serializace  
  
-   Metadata transformace  
  
-   Životnost relace  
  
-   Filtrování adres a zpracování záhlaví  
  
-   Zosobnění  
  
-   Pokud chcete použít tyto atributy, označit jako vhodný pro daný rozsah implementace služby nebo operaci s atributem a nastavte vlastnosti. Například následující příklad kódu ukazuje implementaci operace, která používá <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> vlastnost tak, aby vyžadovala, že volající tuto operaci podporují zosobnění.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Mnoho vlastností vyžadovat další podporu vazby. Například operace, která vyžaduje transakce z klienta, musí být nakonfigurován pro použití vazbu, která podporuje sdružení transakcí.  
  
### <a name="well-known-singleton-services"></a>Deklarace služeb typu Singleton známé  
 Můžete použít <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributů, které mají určité doby života, oba ovládací prvek <xref:System.ServiceModel.InstanceContext> a objektů služeb, které implementují operace.  
  
 Například <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak často <xref:System.ServiceModel.InstanceContext> vydání a <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> vlastnosti řídit, že se uvolnilo objekt služby.  
  
 Můžete však také vytvořit objekt služby sami a vytvořit hostitele služby pomocí tohoto objektu. Uděláte to tak, musíte taky nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.Single> nebo dojde k výjimce při otevření hostitele služby.  
  
 Použití <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktor k vytvoření takové služby. Poskytuje alternativu k implementaci vlastní <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> když chcete poskytovat konkrétní objekt instance pro použití službou typu singleton. Toto přetížení můžete použít, když váš typ implementace služby se obtížně vytvořit (například pokud neimplementuje výchozí veřejný konstruktor, který nemá žádné parametry).  
  
 Všimněte si, že je-li do tohoto konstruktoru objekt, jinak fungovat některé funkce související s pro Windows Communication Foundation (WCF) vytváření instancí chování. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je k dispozici dobře známý objekt instance. Podobně jiný mechanismus uvolnění instance se ignoruje. <xref:System.ServiceModel.ServiceHost> Třídy vždy se chová jako by <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Jiné služby, koncový bod, kontrakt a operace chování  
 Chování služby, jako <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut, provoz napříč celou služby. Pokud nastavíte například <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> musí zpracovat synchronizací vlákna uvnitř jednotlivých operací ve tuto službu, sami. Chování koncového bodu provoz přes koncový bod; mnoho chování koncového bodu poskytované systémem se pro funkce klienta. Kontrakt chování pracovat na úrovni smlouvy a doručování operaci změnit chování operace.  
  
 Mnoho z těchto projevů jsou definovány pro atributy a ujistěte se, můžete použít z nich, stejně jako <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy – jeho použitím na implementaci tříd nebo operace příslušnou službu. Další chování, například <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior> objekty, se obvykle používají pomocí konfiguračního souboru aplikace, i když se lze také prostřednictvím kódu programu.  
  
 Například se konfiguruje v zveřejnění metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objektu. Následující konfigurační soubor aplikace zobrazí nejběžnější využití.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Následující části popisují řadu nejužitečnější poskytnuté systémem, které můžete použít k úpravě doručování modulu runtime služby ani klienta chování. V tématu referenční téma a zjistěte, jak používat každý z nich.  
  
### <a name="service-behaviors"></a>Chování služby  
 Následující chování pracovat na služby.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. U služby WCF k označení, zda je možné spustit tuto službu v [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] režim kompatibility.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Určuje, jak služba autorizuje deklarace identity klienta.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Nakonfiguruje přihlašovacích údajů pro služby. Tato třída slouží k zadání přihlašovacích údajů pro službu, jako je například certifikát X.509.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Povolí ladění a pomoct informace o funkcích služby WCF.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Určuje zveřejnění metadat služby a související informace.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Určuje chování auditování událostí zabezpečení.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje nastavení propustnosti za běhu, které vám umožní optimalizovat výkon služby.  
  
### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Následující chování provoz na koncové body. Mnoho z těchto projevů se používají v klientských aplikacích.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Nakonfiguruje implementaci zpětného volání služby v duplexním klientské aplikace.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Povolí ladění služby WCF objekt zpětného volání.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Umožňuje uživateli konfigurovat přihlašovací údaje klienta a služby, stejně jako nastavení ověřování přihlašovacích údajů pro použití v klientovi služby.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Používají klienti k určení identifikátor URI (Uniform Resource) pro který by měl být vytvořen přenosový kanál.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Dává pokyn WCF zakázat `MustUnderstand` zpracování.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Dá pokyn modulu runtime pomocí synchronního přijímat proces pro kanály.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optimalizuje operace příjmu pro přenosy, které obdrží podporu transakcí.  
  
### <a name="contract-behaviors"></a>Chování kontraktu  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Určuje požadavky na funkce, které vazby musí poskytnout implementaci služby ani klienta.  
  
### <a name="operation-behaviors"></a>Chování operace  
 Následující operace chování zadejte ovládací prvky pro operace serializace a transakce.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Reprezentuje chování za běhu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Řídí chování za běhu `XmlSerializer` a přidruží ji k operaci.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Určuje úroveň, ve kterém přijímá operace služby záhlaví transakce.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md)
- [Postupy: Řízení vytváření instancí služby](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
