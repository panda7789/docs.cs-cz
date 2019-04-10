---
title: 'Postupy: Povolit zjišťování opakování zpráv'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: a7bdfc244b0ff1c2ed625235df7e74ced026c542
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343607"
---
# <a name="how-to-enable-message-replay-detection"></a>Postupy: Povolit zjišťování opakování zpráv
Opakování útoku nastane, pokud útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehrává datový proud na jeden nebo více stran. Pokud zmírnit, počítače v souladu s útok bude zpracovávat datového proudu jako legitimní zprávy, což vede k celou řadu chybný důsledky, jako je například redundantní objednávky položku.  
  
 Další informace o zjišťování opakování zpráv najdete v tématu [zjišťování opakování zpráv](https://go.microsoft.com/fwlink/?LinkId=88536).  
  
 Následující postup ukazuje různé vlastnosti, které můžete použít k řízení rozpoznání opětovného přehrání pomocí Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>K řízení rozpoznání opětovného přehrání na straně klienta pomocí kódu  
  
1. Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> používané <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
2. Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnost vrací odkaz <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy a nastavte libovolné z následujících vlastností, podle potřeby:  
  
    1.  `DetectReplay`. Logická hodnota. To se řídí, zda klient by měl zjistit riziko ze serveru. Výchozí hodnota je `true`.  
  
    2.  `MaxClockSkew`. A <xref:System.TimeSpan> hodnotu. Řídí, kolik času Nerovnoměrná distribuce mechanismus opakování může tolerovat možnost, mezi klientem a serverem. Mechanismus zabezpečení, který prověří časové razítko odeslání a určuje, zda byl odeslán příliš daleko v minulosti. Výchozí hodnota je 5 minut.  
  
    3.  `ReplayWindow`. A `TimeSpan` hodnotu. To se řídí jak dlouho zpráva může existovat v síti, jakmile server odešle ho (prostřednictvím zprostředkovatelů) před dosažením klienta. Klient sleduje podpisy některé zprávy odeslané v rámci nejnovější `ReplayWindow` za účelem rozpoznání opětovného přehrání.  
  
    4.  `ReplayCacheSize`. Celočíselná hodnota. Klient ukládá do mezipaměti podpisy zprávy. Toto nastavení určuje, kolik podpisy, které můžete ukládat do mezipaměti. Pokud počet zpráv odeslaných v rámci poslední období opakování dosáhne limitu mezipaměti, nové zprávy jsou odmítnuta, až do nejstaršího uložené v mezipaměti podpisy dosažení časový limit. Výchozí hodnota je 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>K řízení rozpoznání opětovného přehrání na služby promocí kódu  
  
1. Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> používané <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2. Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnost vrací odkaz <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy a nastavit vlastnosti, jak je popsáno výše.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>K řízení rozpoznání opětovného přehrání v konfiguraci klienta nebo služby  
  
1. Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Vytvoření `<security>` elementu.  
  
3. Vytvoření [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Nastavte následující hodnoty atributu, podle potřeby: `detectReplays`, `maxClockSkew`, `replayWindow`, a `replayCacheSize`. Následující příklad nastaví atributy obou `<localServiceSettings>` a `<localClientSettings>` element:  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metoda a nastaví vlastnosti opakování vazby.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Rozsah opakování: Pouze zabezpečení zpráv  
 Všimněte si, že následující postupy platí pouze pro režim zabezpečených zpráv. Pro přenos a dopravu s přihlašovacími údaji zprávy režimy rozpoznat mechanismy přenosu riziko.  
  
## <a name="secure-conversation-notes"></a>Zabezpečené konverzace poznámky  
 U vazeb, které umožňují zabezpečené konverzace můžete upravit tato nastavení pro kanál aplikace i pro zaváděcí vazbu zabezpečené konverzace. Můžete například vypnout riziko pro kanál aplikace ale povolit jejich spuštění kanálu, který vytvoří zabezpečené konverzace.  
  
 Pokud nepoužijete relací zabezpečené konverzace, rozpoznání opětovného přehrání nezaručuje zjišťování riziko v scénáře serveru farmy a když se proces recykluje. To platí pro následující vazeb poskytovaných systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenou na `false`.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Pro zkompilování kódu se vyžaduje následující obory názvů:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
