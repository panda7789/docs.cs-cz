---
title: Určování chování služby za běhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: ffa2f906ac2ff4630de83938ce365c1b9d5d4d64
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976636"
---
# <a name="specifying-service-run-time-behavior"></a>Určování chování služby za běhu
Po navržení smlouvy o poskytování služeb ([Navrhování kontraktů služeb](designing-service-contracts.md)) a implementaci kontraktu služby ([implementace kontraktů služeb](implementing-service-contracts.md)) můžete nakonfigurovat chování služby Service runtime. Toto téma popisuje chování služby a operace poskytnuté systémem a popisuje, kde najít další informace pro vytvoření nového chování. I když se některé chování aplikuje jako atributy, mnohé se aplikují pomocí konfiguračního souboru aplikace nebo prostřednictvím kódu programu. Další informace o konfiguraci aplikace služby najdete v tématu [Konfigurace služeb](configuring-services.md).  
  
## <a name="overview"></a>Přehled  
 Smlouva definuje vstupy, výstupy, datové typy a možnosti služby daného typu. Implementace kontraktu služby vytvoří třídu, která, pokud je nakonfigurována s vazbou na adrese, splní kontrakt, který implementuje. Informace o smluvních, vazbách a adresách jsou všechny známy u klienta. bez nich klient nemůže službu používat.  
  
 Nicméně konkrétní operace, jako jsou například problémy s vlákny nebo Správa instancí, jsou pro klienty neprůhledné. Po dokončení implementace kontraktu služby můžete nakonfigurovat velký počet charakteristik operací pomocí *chování*. Chování jsou objekty, které upravují modul runtime Windows Communication Foundation (WCF) buď nastavením běhové vlastnosti, nebo vložením typu vlastního nastavení do modulu runtime. Další informace o úpravách modulu runtime vytvořením uživatelsky definovaného chování naleznete v tématu [Rozšíření ServiceHost a vrstva modelu služby](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Atributy <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> jsou nejrozšířenějším užitečným chováním a zpřístupňují nejčastěji požadované funkce operace. Vzhledem k tomu, že se jedná o atributy, je můžete použít pro implementaci služby nebo operace. Jiné chování, například <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, se obvykle aplikují pomocí konfiguračního souboru aplikace, i když je můžete používat programově.  
  
 Toto téma obsahuje přehled atributů <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute>, popisuje různé obory, ve kterých může chování fungovat, a poskytuje rychlý popis mnoha systémových chování v různých oborech, které mohou být v zájmu WCF. pracující.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>Atribut ServiceBehaviorAttribute a OperationBehaviorAttribute  
 Nejdůležitější chování jsou atributy <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute>, které můžete použít k řízení:  
  
- Životnost instancí  
  
- Podpora souběžnosti a synchronizace  
  
- Chování konfigurace  
  
- Chování transakce  
  
- Chování serializace  
  
- Transformace metadat  
  
- Doba života relace  
  
- Filtrování adres a zpracování hlaviček  
  
- Zosobnění  
  
- Chcete-li použít tyto atributy, označte implementaci služby nebo operace s atributem odpovídajícím tomuto oboru a nastavte vlastnosti. Například následující příklad kódu ukazuje implementaci operace, která pomocí vlastnosti <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> vyžaduje, aby volající této operace podporoval zosobnění.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Mnohé z vlastností vyžadují další podporu vazby. Například operace, která vyžaduje transakci z klienta, musí být nakonfigurována tak, aby používala vazbu, která podporuje přetečení transakcí.  
  
### <a name="well-known-singleton-services"></a>Dobře známé služby s jedním prvkem  
 Atributy <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> lze použít k řízení určitých životností, obou <xref:System.ServiceModel.InstanceContext> a objektů služby, které implementují operace.  
  
 Například vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> určuje, jak často je <xref:System.ServiceModel.InstanceContext> vydaná, a ovládací prvek <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> vlastností, když je objekt služby uvolněn.  
  
 Můžete ale také vytvořit objekt služby sami a vytvořit hostitele služby pomocí tohoto objektu. K tomu je nutné také nastavit vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.InstanceContextMode.Single> nebo je vyvolána výjimka při otevření hostitele služby.  
  
 K vytvoření takové služby použijte konstruktor <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType>. Poskytuje alternativu k implementaci vlastního <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType>, pokud chcete poskytnout konkrétní instanci objektu pro použití ve službě typu singleton. Toto přetížení můžete použít, pokud je obtížné sestavit typ implementace služby (například pokud neimplementuje veřejný konstruktor bez parametrů).
  
 Všimněte si, že když je objekt poskytnut tomuto konstruktoru, některé funkce související s chováním vytváření instancí služby Windows Communication Foundation (WCF) fungují jinak. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, pokud je k dispozici dobře známá instance objektu. Podobně platí, že jakýkoli mechanismus uvolnění instancí se ignoruje. Třída <xref:System.ServiceModel.ServiceHost> se vždy chová, jako by vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> byla nastavena na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pro všechny operace.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Jiné chování služeb, koncových bodů, kontraktů a operací  
 Chování služby, jako je například atribut <xref:System.ServiceModel.ServiceBehaviorAttribute>, funguje v celé službě. Například pokud nastavíte vlastnost <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> musíte zpracovat problémy synchronizace vláken uvnitř každé operace v této službě sami. Chování koncového bodu funguje v rámci koncového bodu; Mnohé z chování koncových bodů poskytovaných systémem jsou určené pro funkce klienta. Chování kontraktu působí na úrovni smlouvy a chování operace upraví operace změny.  
  
 Mnohé z těchto chování jsou implementovány u atributů a vy je použijete jako atributy <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> – jejich použitím na příslušnou implementaci třídy služby nebo operace. Jiné chování, například objekty <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior>, se obvykle používají pomocí konfiguračního souboru aplikace, i když je lze také použít programově.  
  
 Například publikace metadat je nakonfigurována pomocí objektu <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Následující konfigurační soubor aplikace zobrazuje nejběžnější využití.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Následující části popisují mnoho z nejužitečnějších chování poskytovaných systémem, které můžete použít k úpravě doručování za běhu vaší služby nebo klienta. V tématu o tom, jak určit, jak se má používat, najdete v referenčním tématu.  
  
### <a name="service-behaviors"></a>Chování služby  
 Následující chování působí na služby.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Použito na službu WCF, která označuje, zda lze tuto službu spustit v režimu kompatibility ASP.NET.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Určuje, jak služba autorizuje deklarace identity klienta.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Nakonfiguruje pověření služby. Tato třída slouží k zadání přihlašovacích údajů pro službu, jako je například certifikát X. 509.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Povolí ladění a funkce informací o nápovědě pro službu WCF.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Řídí publikování metadat služby a přidružených informací.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Určuje chování auditu událostí zabezpečení.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje nastavení propustnosti v době běhu, které vám umožní ladit výkon služby.  
  
### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Následující chování fungují na koncových bodech. Mnohé z těchto chování se používají v klientských aplikacích.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Konfiguruje implementaci služby zpětného volání v duplexní klientské aplikaci.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Povoluje ladění služby pro objekt zpětného volání WCF.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Umožňuje uživateli konfigurovat pověření klienta a služby a také nastavení ověřování pověření služby pro použití v klientovi.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Klienti používají k určení identifikátoru URI, pro který má být vytvořen přenosový kanál.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Instruuje WCF, aby zakázal zpracování `MustUnderstand`.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Instruuje modul runtime, aby používal synchronní proces příjmu pro kanály.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optimalizuje operace přijímání pro přenosy, které podporují transakční příjem.  
  
### <a name="contract-behaviors"></a>Chování kontraktu  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Určuje požadavky na funkce, které musí vazby poskytovat službě nebo implementaci klienta.  
  
### <a name="operation-behaviors"></a>Chování operace  
 Následující chování operace určují serializaci a řízení transakcí pro operace.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Představuje chování při běhu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Řídí chování při běhu `XmlSerializer` a přidruží ho k operaci.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Určuje úroveň, ve které operace služby akceptuje hlavičku transakce.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb](configuring-services.md)
- [Postupy: Řízení vytváření instancí služby](./feature-details/how-to-control-service-instancing.md)
