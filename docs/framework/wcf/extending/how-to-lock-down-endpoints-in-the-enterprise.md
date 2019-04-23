---
title: 'Postupy: Uzamknutí koncových bodů v podniku'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: da90c2e9d096d32c819590058f1e513224fd9242
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305952"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Postupy: Uzamknutí koncových bodů v podniku
Velké podniky často vyžadují, že jsou aplikace vyvíjeny souladu se zásadami zabezpečení organizace. Následující téma popisuje, jak vyvíjet a instalace klienta validátor koncový bod, který slouží k ověření všech klientských aplikací Windows Communication Foundation (WCF) nainstalována na počítačích.  
  
 V takovém případě validátoru je program pro ověření klienta, protože toto chování koncového bodu je přidali do klienta [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu v souboru machine.config. WCF načte společné chování koncového bodu pouze pro klientské aplikace a načte společné chování služby pouze pro aplikace služby. Chcete-li nainstalovat tento stejný validátor pro služby aplikací, musí být validátor chování služby. Další informace najdete v tématu [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu.  
  
> [!IMPORTANT]
>  Chování služby nebo koncového bodu není označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA), které jsou přidány do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu konfiguračního souboru se nespustí, když aplikace běží v částečném vztahu důvěryhodnosti Pokud k tomu dojde, je vyvolána prostředí a žádná výjimka. Pokud chcete vynutit spuštění společné chování, jako je například validátory, musíte buď:  
>   
>  --Označit vaše běžné chování s <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut tak, aby ji můžete spustit po nasazení jako částečném vztahu důvěryhodnosti aplikace. Všimněte si, že položka registru můžete nastavit v počítači zabránit sestavení APTCA označené spouštění...  
>   
>  – Ujistěte se, že pokud je aplikace nasazená jako plně důvěryhodné aplikace, uživatelé nemohou měnit nastavení zabezpečení přístupu kódu a spusťte aplikaci v prostředí částečné důvěryhodnosti. Pokud můžete, vlastní validátor se nespustí a není vyvolána žádná výjimka. Jeden způsob, jak to zajistit, najdete v článku `levelfinal` možnost použití [nástroj zásad zabezpečení přístupu kódu (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Další informace najdete v tématu [částečné důvěryhodnosti osvědčené postupy](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) a [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Chcete-li vytvořit koncový bod validátoru  
  
1. Vytvoření <xref:System.ServiceModel.Description.IEndpointBehavior> požadovaného ověření provedením kroků v <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> metody. Následující kód obsahuje příklad. ( `InternetClientValidatorBehavior` Je převzata z [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) ukázka.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2. Vytvořit nový <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který registruje validátor koncový bod vytvořili v kroku 1. Následující příklad kódu ukazuje to. (Původní kód v tomto příkladu je v [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) ukázka.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3. Zajistěte, aby že zkompilovaného sestavení je podepsáno silným názvem. Podrobnosti najdete v tématu [nástroj Strong Name (sériové číslo. Soubor EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) a kompilátoru příkazy pro váš jazyk.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Chcete-li nainstalovat validátoru do cílového počítače  
  
1. Instalaci koncového bodu validátoru pomocí vhodný mechanismus. V podniku tím můžete pomocí zásad skupiny a Systems Management Server (SMS).  
  
2. Instalace sestavení se silným názvem do mezipaměti globálního sestavení pomocí [Gacutil.exe (Global Assembly Cache Tool)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
3. Použití <xref:System.Configuration?displayProperty=nameWithType> obor názvů, typy mají:  
  
    1.  Přidat rozšíření [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) části použití plně kvalifikovaný název typu a uzamčení elementu.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Přidat prvek chování `EndpointBehaviors` vlastnost [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bod a uzamčení elementu. (Pro instalaci ověřovací modul ve službě, musí být validátor <xref:System.ServiceModel.Description.IServiceBehavior> a přidán do `ServiceBehaviors` vlastnost.) Následující příklad kódu ukazuje správné konfigurace po krocích. a b. s jedinou výjimkou, že neexistuje žádná silného názvu.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Uložte soubor machine.config. Následující příklad kódu provede všechny úkoly v kroku 3, ale uloží kopii souboru machine.config změny místně.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat běžné chování machine.config souboru a uložte jeho kopii disku. `InternetClientValidatorBehavior` Je převzata z [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) vzorku.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Můžete také chtít šifrování souboru elementů konfigurace. Další informace najdete v části Viz také.  
  
## <a name="see-also"></a>Viz také:

- [Šifrování konfiguračních elementů souboru pomocí DPAPI](https://go.microsoft.com/fwlink/?LinkId=94954)
- [Šifrování konfigurační soubor prvky pomocí technologie RSA](https://go.microsoft.com/fwlink/?LinkId=94955)
