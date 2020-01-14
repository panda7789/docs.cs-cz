---
title: 'Postupy: uzamknutí koncových bodů v podniku'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 35b9a1dbebce48823799689a581033d0483c3984
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937683"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Postupy: uzamknutí koncových bodů v podniku

Velké podniky často vyžadují, aby se aplikace vyvinuly v souladu s podnikovými zásadami zabezpečení. Následující téma popisuje, jak vyvíjet a instalovat validátor koncového bodu klienta, který lze použít k ověření všech klientských aplikací Windows Communication Foundation (WCF) nainstalovaných v počítačích.

V tomto případě validátor je validátor klienta, protože toto chování koncového bodu je přidáno do části [> klienta\<CommonBehaviors](../../configure-apps/file-schema/wcf/commonbehaviors.md) v souboru Machine. config. WCF načte běžné chování koncových bodů jenom pro klientské aplikace a nahraje běžné chování služby jenom pro aplikace služeb. Pro instalaci stejného validátoru pro aplikace služby musí být validátorem chování služby. Další informace najdete v části [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) .

> [!IMPORTANT]
> Chování služby nebo koncového bodu není označeno atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA), který je přidán do oddílu [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) konfiguračního souboru, se nespustí, když aplikace běží v částečně důvěryhodném prostředí, a v případě, že dojde k výjimce, není vyvolána žádná výjimka. Aby se vynutilo spouštění běžných chování, jako jsou validátory, musíte:
>
> - Označte běžné chování atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> tak, aby mohl běžet při nasazení jako aplikace s částečnou důvěryhodností. Všimněte si, že položku registru lze nastavit na počítači, aby bylo možné zabránit spuštění sestavení označených APTCA.
>
> - Zajistěte, aby byla aplikace nasazena jako plně důvěryhodná aplikace, kterou uživatelé nemohou měnit nastavení zabezpečení přístupu kódu pro spuštění aplikace v prostředí s částečným vztahem důvěryhodnosti. Pokud je to možné, vlastní validátor se nespustí a není vyvolána žádná výjimka. Pokud to chcete zajistit, přečtěte si část `levelfinal` pomocí [nástroje zásady zabezpečení přístupu kódu (Caspol. exe)](../../tools/caspol-exe-code-access-security-policy-tool.md).
>
> Další informace najdete v tématu věnovaném [osvědčeným postupům pro částečnou důvěryhodnost](../feature-details/partial-trust-best-practices.md) a [podporovaným scénářům nasazení](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Vytvoření validátoru koncových bodů

1. V metodě <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> vytvořte <xref:System.ServiceModel.Description.IEndpointBehavior> s požadovanými kroky ověření. Následující kód poskytuje příklad. (`InternetClientValidatorBehavior` je pořízena z ukázky [ověření zabezpečení](../samples/security-validation.md) .)

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Vytvořte nový <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, který registruje validátor koncového bodu vytvořený v kroku 1. Následující příklad kódu ukazuje toto. (Původní kód pro tento příklad je v ukázce [ověření zabezpečení](../samples/security-validation.md) .)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Ujistěte se, že zkompilované sestavení je podepsáno silným názvem. Podrobnosti najdete v tématu [Nástroj silného názvu (Sn. EXE)](../../tools/sn-exe-strong-name-tool.md) a příkazy kompilátoru pro váš jazyk.

### <a name="to-install-the-validator-into-the-target-computer"></a>Instalace validátoru do cílového počítače

1. Pomocí vhodného mechanismu nainstalujte validátor koncového bodu. V podniku můžete použít Zásady skupiny a Systems Management Server (SMS).

2. Nainstalujte sestavení se silným názvem do globální mezipaměti sestavení (GAC) pomocí nástroje [Gacutil. exe (nástroj Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).

3. <xref:System.Configuration?displayProperty=nameWithType> typy oboru názvů použijte k těmto akcím:

    1. Přidejte rozšíření do oddílu [\<behaviorExtensions >](../../configure-apps/file-schema/wcf/behaviorextensions.md) pomocí plně kvalifikovaného názvu typu a zamkněte element.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Přidejte prvek chování do vlastnosti `EndpointBehaviors` části [\<commonBehaviors >](../../configure-apps/file-schema/wcf/commonbehaviors.md) a zamkněte prvek. (Chcete-li nainstalovat validátor na službu, musí být validátor <xref:System.ServiceModel.Description.IServiceBehavior> a přidán do vlastnosti `ServiceBehaviors`.) Následující příklad kódu ukazuje správnou konfiguraci po krocích a. a b. s jedinou výjimkou, že neexistuje silný název.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Uložte soubor machine.config. Následující příklad kódu provede všechny úlohy v kroku 3, ale uloží kopii upraveného souboru Machine. config místně.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak přidat do souboru Machine. config běžné chování a uložit kopii na disk. `InternetClientValidatorBehavior` je pořízena z ukázky [ověření zabezpečení](../samples/security-validation.md) .

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Můžete také chtít šifrovat prvky konfiguračního souboru. Další informace najdete v části Viz také.

## <a name="see-also"></a>Viz také:

- [Šifrování elementů konfiguračního souboru pomocí DPAPI](https://docs.microsoft.com/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [Šifrování elementů konfiguračního souboru pomocí RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))
