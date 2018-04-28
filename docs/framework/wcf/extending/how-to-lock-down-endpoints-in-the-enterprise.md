---
title: 'Postupy: uzamčení koncových bodů v podnikové síti'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5b10665e9a820c7057231c684769bddf9cb0c79
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Postupy: uzamčení koncových bodů v podnikové síti
Velké podniky často vyžadují, že se aplikace vyvinuté souladu se zásadami zabezpečení organizace. Následující téma popisuje, jak vyvíjet a instalovat klienta validátoru koncový bod, který lze ověřit, zda všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientské aplikace nainstalované na počítačích.  
  
 V takovém případě validátor je ověření klienta, protože toto chování koncový bod se přidá do klienta [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddíl v souboru machine.config. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] načte společné chování koncový bod pouze pro klientské aplikace a načte společné chování služby pouze pro aplikace služby. Chcete-li nainstalovat tento stejný validátor pro aplikace služby, musí být validátor chování služby. Další informace najdete v tématu [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) části.  
  
> [!IMPORTANT]
>  Služba nebo koncový bod chování neoznačené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA), které jsou přidány do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu konfiguračního souboru se nespustí, pokud je aplikace spuštěná v částečné důvěryhodnosti v takovém případě je vyvolána prostředí a žádná výjimka. Pokud chcete vynutit spuštění společné chování, například validátory, které je nutné buď:  
>   
>  --Označit chování vaší běžné s <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut, aby se může spustit při nasazení jako částečné důvěryhodnosti aplikace. Všimněte si, že položka registru lze nastavit v počítači aby označena APTCA sestavení spouštění...  
>   
>  – Zkontrolujte, zda Pokud je aplikace nasazená jako plně důvěryhodné aplikace, uživatelé nemohou upravovat nastavení zabezpečení přístupu kódu ke spuštění aplikace v prostředí částečné důvěryhodnosti. Pokud se zachovají, vlastní validátor nespustí a nedojde k výjimce. Jeden způsob, jak zajistit to, najdete v článku `levelfinal` možnost pomocí [nástroj zásad zabezpečení přístupu kódu (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Další informace najdete v tématu [částečné důvěryhodnosti osvědčené postupy](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) a [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Chcete-li vytvořit validátor koncový bod  
  
1.  Vytvoření <xref:System.ServiceModel.Description.IEndpointBehavior> s požadované ověřovací kroky v <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> metoda. Následující kód představuje příklad. ( `InternetClientValidatorBehavior` Jsou převzaty z [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) ukázkové.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Vytvořit nový <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , zaregistruje koncový bod validátoru vytvořili v kroku 1. Následující příklad kódu ukazuje to. (Původní kód v tomto příkladu je v [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) ukázkové.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Zkontrolujte, zda že je podepsán kompilované sestavení se silným názvem. Podrobnosti najdete v tématu [Strong Name Tool (SN. Soubor EXE)](http://go.microsoft.com/fwlink/?LinkId=248217) a příkazy kompilátoru pro svůj jazyk.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Chcete-li nainstalovat validátor do cílového počítače  
  
1.  Nainstalujte validátor koncový bod pomocí příslušné mechanismu. V podniku tím můžete pomocí zásad skupiny a Systems Management Server (SMS).  
  
2.  Instalace sestavení se silným názvem do sestavení v globální mezipaměti pomocí [Gacutil.exe (Global Assembly Cache Tool)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Použití <xref:System.Configuration?displayProperty=nameWithType> typů obor názvů, který:  
  
    1.  Přidejte rozšíření do [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) část pomocí názvu plně kvalifikovaný typ a uzamčení elementu.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Chování elementu, který chcete přidat `EndpointBehaviors` vlastnost [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) části a uzamčení elementu. (Instalace validátor na službu, musí být validátor <xref:System.ServiceModel.Description.IServiceBehavior> a přidat do `ServiceBehaviors` vlastnost.) Následující příklad kódu ukazuje správnou konfiguraci po provedení kroků. a b. s jedinou výjimkou, že není žádný silný název.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Uložení souboru machine.config. Následující příklad kódu provádět všechny úlohy v kroku 3, ale uloží kopii souboru machine.config upravené místně.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat společné chování k souboru machine.config a uložte jeho kopii disku. `InternetClientValidatorBehavior` Jsou převzaty z [ověření zabezpečení](../../../../docs/framework/wcf/samples/security-validation.md) ukázka.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Můžete také šifrování elementů souboru konfigurace. Další informace najdete v části Viz také.  
  
## <a name="see-also"></a>Viz také  
 [Šifrování souboru konfigurace – elementy pomocí rozhraní DPAPI](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [Šifrování RSA pomocí konfiguračních souborů elementů](http://go.microsoft.com/fwlink/?LinkId=94955)
