---
title: 'Postupy: Uzamknutí koncových bodů v podniku'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: d2a0299dd67e6efe3e3d9e6bae81265d4ad314ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040280"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Postupy: Uzamknutí koncových bodů v podniku

Velké podniky často vyžadují, aby se aplikace vyvinuly v souladu s podnikovými zásadami zabezpečení. Následující téma popisuje, jak vyvíjet a instalovat validátor koncového bodu klienta, který lze použít k ověření všech klientských aplikací Windows Communication Foundation (WCF) nainstalovaných v počítačích.

V tomto případě validátor je validátor klienta, protože toto chování koncového bodu je přidáno do oddílu [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) klienta v souboru Machine. config. WCF načte běžné chování koncových bodů jenom pro klientské aplikace a nahraje běžné chování služby jenom pro aplikace služeb. Pro instalaci stejného validátoru pro aplikace služby musí být validátorem chování služby. Další informace najdete v [ \<části > CommonBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) .

> [!IMPORTANT]
> Chování služby nebo koncového bodu není označeno <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA), který je přidán [ \<do oddílu CommonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) konfiguračního souboru, se nespustí, pokud je aplikace spuštěna v prostředí s částečným vztahem důvěryhodnosti a ne. Pokud k tomu dojde, je vyvolána výjimka. Aby se vynutilo spouštění běžných chování, jako jsou validátory, musíte:
>
> - Označte běžné chování <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem tak, aby mohl běžet při nasazení jako aplikace s částečnou důvěryhodností. Všimněte si, že položku registru lze nastavit na počítači, aby bylo možné zabránit spuštění sestavení označených APTCA.
>
> - Zajistěte, aby byla aplikace nasazena jako plně důvěryhodná aplikace, kterou uživatelé nemohou měnit nastavení zabezpečení přístupu kódu pro spuštění aplikace v prostředí s částečným vztahem důvěryhodnosti. Pokud je to možné, vlastní validátor se nespustí a není vyvolána žádná výjimka. Pro zajištění toho, aby to bylo možné, `levelfinal` Přečtěte si téma použití [nástroje zásady zabezpečení přístupu kódu (Caspol. exe)](https://go.microsoft.com/fwlink/?LinkId=248222).
>
> Další informace najdete v tématu věnovaném osvědčeným postupům pro [částečnou důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) a podporovaným [scénářům nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Vytvoření validátoru koncových bodů

1. Vytvořte pomocí požadovaných kroků ověření <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> v metodě. <xref:System.ServiceModel.Description.IEndpointBehavior> Následující kód poskytuje příklad. (Z ukázky [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) jepořízená.)`InternetClientValidatorBehavior`

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Vytvořte nový <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který registruje validátor koncového bodu vytvořený v kroku 1. Následující příklad kódu ukazuje toto. (Původní kód pro tento příklad je v ukázce [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) .)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Ujistěte se, že zkompilované sestavení je podepsáno silným názvem. Podrobnosti najdete v tématu [Nástroj silného názvu (Sn. EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) a příkazy kompilátoru pro váš jazyk.

### <a name="to-install-the-validator-into-the-target-computer"></a>Instalace validátoru do cílového počítače

1. Pomocí vhodného mechanismu nainstalujte validátor koncového bodu. V podniku můžete použít Zásady skupiny a Systems Management Server (SMS).

2. Nainstalujte sestavení se silným názvem do globální mezipaměti sestavení (GAC) pomocí nástroje [Gacutil. exe (nástroj Global Assembly Cache Tool)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).

3. <xref:System.Configuration?displayProperty=nameWithType> Typy oboru názvů použijte k těmto akcím:

    1. Přidejte rozšíření do [ \<oddílu BehaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) pomocí plně kvalifikovaného názvu typu a zamkněte element.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Přidejte prvek chování do `EndpointBehaviors` vlastnosti [ \<oddílu CommonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) a zamkněte prvek. (Chcete-li nainstalovat validátor na službu, musí být <xref:System.ServiceModel.Description.IServiceBehavior> validátor a přidán `ServiceBehaviors` do vlastnosti.) Následující příklad kódu ukazuje správnou konfiguraci po krocích a. a b. s jedinou výjimkou, že neexistuje silný název.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Uložte soubor machine.config. Následující příklad kódu provede všechny úlohy v kroku 3, ale uloží kopii upraveného souboru Machine. config místně.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak přidat do souboru Machine. config běžné chování a uložit kopii na disk. Je pořízen z ukázky [ověření zabezpečení.](../../../../docs/framework/wcf/samples/security-validation.md) `InternetClientValidatorBehavior`

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Můžete také chtít šifrovat prvky konfiguračního souboru. Další informace najdete v části Viz také.

## <a name="see-also"></a>Viz také:

- [Šifrování elementů konfiguračního souboru pomocí DPAPI](https://go.microsoft.com/fwlink/?LinkId=94954)
- [Šifrování elementů konfiguračního souboru pomocí RSA](https://go.microsoft.com/fwlink/?LinkId=94955)
