---
title: Určování chování služby za běhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 246f16cee85633499a6a1c200e608ee7bccf133c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243099"
---
# <a name="specifying-service-run-time-behavior"></a>Určování chování služby za běhu
Po navržení servisní smlouvy[(Návrh servisních smluv)](designing-service-contracts.md)a implementaci servisní smlouvy[(Implementace servisních smluv)](implementing-service-contracts.md)můžete nakonfigurovat provozní chování zaběhu služby. Toto téma popisuje systémposkytované služby a chování operací a popisuje, kde najít další informace k vytvoření nové chování. Zatímco některé chování jsou použity jako atributy, mnoho z nich jsou použity pomocí konfiguračního souboru aplikace nebo programově. Další informace o konfiguraci aplikace služby naleznete v [tématu Configuring Services](configuring-services.md).  
  
## <a name="overview"></a>Přehled  
 Smlouva definuje vstupy, výstupy, datové typy a možnosti služby tohoto typu. Implementace smlouvy o poskytování služeb vytvoří třídu, která při konfiguraci s vazbou na adrese splňuje smlouvu, kterou implementuje. Klient zná smluvní, závazné a adresní informace; bez nich nemůže klient službu využít.  
  
 Specifika operace, jako jsou například problémy s podprocesem nebo správa instancí, jsou však pro klienty neprůhledné. Po implementaci smlouvy o poskytování služeb můžete nakonfigurovat velký počet charakteristik operací pomocí *chování*. Chování jsou objekty, které upravují za běhu Windows Communication Foundation (WCF) buď nastavením vlastnosti runtime nebo vložením typu vlastního nastavení do runtime. Další informace o úpravách běhu vytvořením uživatelem definovaných chování naleznete [v tématu Rozšíření servicehost a vrstvy modelu služby](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> Atributy <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> a jsou nejužitečnější chování a vystavit nejčastěji požadované funkce operace. Vzhledem k tomu, že se jedná o atributy, použijete je na implementaci služby nebo operace. Jiné chování, například <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>nebo , jsou obvykle použity pomocí konfiguračního souboru aplikace, i když je můžete použít programově.  
  
 Toto téma obsahuje <xref:System.ServiceModel.ServiceBehaviorAttribute> přehled <xref:System.ServiceModel.OperationBehaviorAttribute> atributů a, popisuje různé obory, ve kterých může fungovat chování, a poskytuje rychlý popis mnoha systémově poskytovaných chování v různých oborech, které mohou být zajímavé pro vývojáře WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>Atribut ServiceBehaviorAttribute a OperationBehaviorAttribute  
 Nejdůležitější chování jsou <xref:System.ServiceModel.ServiceBehaviorAttribute> atributy <xref:System.ServiceModel.OperationBehaviorAttribute> a, které můžete použít k řízení:  
  
- Životnost instance  
  
- Podpora souběžnosti a synchronizace  
  
- Chování konfigurace  
  
- Chování transakce  
  
- Chování serializace  
  
- Transformace metadat  
  
- Životnost relace  
  
- Filtrování adres a zpracování záhlaví  
  
- Zosobnění  
  
- Chcete-li použít tyto atributy, označte implementaci služby nebo operace atributem odpovídajícím tomuto oboru a nastavte vlastnosti. Například následující příklad kódu ukazuje implementaci operace, která používá <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> vlastnost vyžadovat, aby volající této operace podporují zosobnění.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Mnoho vlastností vyžaduje další podporu z vazby. Například operace, která vyžaduje transakci od klienta, musí být nakonfigurována tak, aby používala vazbu, která podporuje transakce s tokem.  
  
### <a name="well-known-singleton-services"></a>Známé singleton služby  
 Atributy <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> můžete použít k řízení určité doby <xref:System.ServiceModel.InstanceContext> životnosti, a to i objekty služby, které implementují operace.  
  
 Například <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost určuje, jak <xref:System.ServiceModel.InstanceContext> často je <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> uvolněna a vlastnosti a <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> řídit, kdy je objekt služby uvolněn.  
  
 Můžete však také vytvořit objekt služby sami a vytvořit hostitele služby pomocí tohoto objektu. Chcete-li tak učinit, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> musíte <xref:System.ServiceModel.InstanceContextMode.Single> také nastavit vlastnost nebo je vyvolána výjimka při otevření hostitele služby.  
  
 Pomocí <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> konstruktoru vytvořit takovou službu. Poskytuje alternativu k implementaci <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> vlastní, pokud chcete poskytnout konkrétní instance objektu pro použití službou singleton. Toto přetížení můžete použít, když je obtížné vytvořit typ implementace služby (například pokud neimplementuje public konstruktor bez parametrů).
  
 Všimněte si, že když je objekt k dispozici tohoto konstruktoru, některé funkce související s Windows Communication Foundation (WCF) instance chování pracovat jinak. Například volání <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nemá žádný vliv, když je k dispozici známá instance objektu. Podobně je ignorována jakákoli jiná instance uvolnění mechanismus. Třída <xref:System.ServiceModel.ServiceHost> se vždy chová, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> jako by <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> vlastnost je nastavena na pro všechny operace.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Jiné chování služeb, koncovýbod, smlouvy a operace  
 Chování služby, jako <xref:System.ServiceModel.ServiceBehaviorAttribute> je například atribut, pracovat v rámci celé služby. Například pokud nastavíte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> vlastnost, kterou musíte zpracovat problémy se synchronizací vláken uvnitř každé operace v této službě sami. Chování koncových bodů pracují v rámci koncového bodu. mnoho systémových koncových bodů chování jsou pro funkce klienta. Chování smlouvy pracovat na úrovni smlouvy a chování operace upravit doručení operace.  
  
 Mnoho z těchto chování jsou implementovány na atributy a můžete <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> využít je jako vy atributy – jejich použití na příslušnou třídu služby nebo provádění operace. Jiné chování, jako <xref:System.ServiceModel.Description.ServiceMetadataBehavior> jsou <xref:System.ServiceModel.Description.ServiceDebugBehavior> například objekty nebo, jsou obvykle použity pomocí konfiguračního souboru aplikace, i když mohou být také použity programově.  
  
 Například zveřejnění metadat je konfigurován pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objektu. Následující konfigurační soubor aplikace zobrazuje nejběžnější použití.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 Následující části popisují mnoho nejužitečnějších systémových chování, které můžete použít k úpravě dobového dodání služby nebo klienta. Informace o tom, jak se jednotlivé z nich používat, najdete v referenčním tématu.  
  
### <a name="service-behaviors"></a>Chování služby  
 Následující chování pracovat na služby.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Použitá služba WCF k označení, zda lze tuto službu spustit v režimu kompatibility ASP.NET.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Určuje, jak služba autorizuje deklarace klienta.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Konfiguruje pověření služby. Tato třída slouží k určení pověření pro službu, jako je například certifikát X.509.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Umožňuje funkce ladění a informací nápovědy pro službu WCF.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Řídí zveřejňování metadat služby a souvisejících informací.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Určuje chování auditu událostí zabezpečení.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje nastavení propustnost za běhu, které umožňují optimalizovat výkon služby.  
  
### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Následující chování pracovat na koncové body. Mnoho z těchto chování se používají v klientských aplikacích.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Konfiguruje implementaci služby zpětného volání v duplexní klientské aplikaci.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Povolí ladění služby pro objekt zpětného volání WCF.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Umožňuje uživateli konfigurovat pověření klienta a služby a také nastavení ověřování pověření služby pro použití v klientovi.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Klienti používají k určení identifikátoru URI jednotného prostředku (URI), pro který by měl být vytvořen kanál přenosu.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Dává pokyn WCF `MustUnderstand` zakázat zpracování.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Dává pokyn modulu runtime, aby pro kanály používal synchronní proces příjmu.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optimalizuje operace příjmu pro přenosy, které podporují transakční přijímá.  
  
### <a name="contract-behaviors"></a>Chování smlouvy  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Určuje požadavky na funkce, které musí vazby poskytnout implementaci služby nebo klienta.  
  
### <a name="operation-behaviors"></a>Chování operace  
 Následující chování operace určují serializaci a ovládací prvky transakcí pro operace.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Představuje chování za běhu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Řídí chování za běhu `XmlSerializer` a přidruží k operaci.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Určuje úroveň, ve které operace služby přijímá hlavičku transakce.  
  
## <a name="see-also"></a>Viz také

- [Konfigurace služeb](configuring-services.md)
- [Postupy: Řízení vytváření instancí služby](./feature-details/how-to-control-service-instancing.md)
