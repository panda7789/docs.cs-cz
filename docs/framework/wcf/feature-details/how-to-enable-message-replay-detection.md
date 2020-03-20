---
title: 'Postupy: Povolení zjišťování opakování zpráv'
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
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184956"
---
# <a name="how-to-enable-message-replay-detection"></a>Postupy: Povolení zjišťování opakování zpráv
K útoku při přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran. Pokud to nebude zmírněno, počítače, které jsou předmětem útoku, zpracují datový proud jako legitimní zprávy, což má za následek řadu chybných důsledků, jako jsou například nadbytečné objednávky položky.  
  
 Další informace o detekci opětovného přehrání zpráv naleznete v [tématu Detekce opětovného přehrání zpráv](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Následující postup ukazuje různé vlastnosti, které můžete použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Řízení detekce přehrání na straně klienta pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> a pro <xref:System.ServiceModel.Channels.CustomBinding>použití v . Další informace naleznete v [tématu How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> s <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
2. Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnosti vrátíte odkaz <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> na třídu a podle potřeby nastavte některou z následujících vlastností:  
  
    1. `DetectReplay`. Logická hodnota To určuje, zda by měl klient zjistit záznamy ze serveru. Výchozí formát je `true`.  
  
    2. `MaxClockSkew`. Hodnota. <xref:System.TimeSpan> Určuje, kolik času zkosení mechanismus přehrání může tolerovat mezi klientem a serverem. Bezpečnostní mechanismus zkontroluje odeslané časové razítko a určí, zda bylo odesláno příliš daleko v minulosti. Výchozí hodnota je 5 minut.  
  
    3. `ReplayWindow`. Hodnota. `TimeSpan` To určuje, jak dlouho může zpráva žít v síti poté, co ji server odešle (prostřednictvím zprostředkovatelů) před dosažením klienta. Klient sleduje podpisy zpráv odeslaných nejpozději `ReplayWindow` pro účely detekce přehrání.  
  
    4. `ReplayCacheSize`. Hodnota celého čísla. Klient ukládá podpisy zprávy do mezipaměti. Toto nastavení určuje, kolik podpisů může mezipaměť uložit. Pokud počet zpráv odeslaných v posledním okně přehrávání dosáhne limitu mezipaměti, budou nové zprávy odmítnuty, dokud nejstarší podpisy uložené v mezipaměti nedosáhnou časového limitu. Výchozí hodnota je 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Řízení detekce přehrání ve službě pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> a pro <xref:System.ServiceModel.Channels.CustomBinding>použití v .  
  
2. Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnosti vrátit odkaz <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> na třídu a nastavit vlastnosti, jak je popsáno výše.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Řízení detekce přehrání v konfiguraci pro klienta nebo službu  
  
1. Vytvořte [ \<vlastní vazbu>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Vytvořte `<security>` prvek.  
  
3. Vytvořte [ \<>nastavení localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings ](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Podle potřeby nastavte následující hodnoty `detectReplays` `maxClockSkew`atributů: , , `replayWindow`a `replayCacheSize`. Následující příklad nastaví atributy `<localServiceSettings>` prvku `<localClientSettings>` a prvku a prvku:  
  
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
 Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody a nastaví vlastnosti přehrání vazby.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Rozsah přehrání: Pouze zabezpečení zpráv  
 Všimněte si, že následující postupy platí pouze pro režim zabezpečení zprávy. Pro přenos a přenos s režimy pověření zprávy, mechanismy přenosu rozpoznat záznamy.  
  
## <a name="secure-conversation-notes"></a>Zabezpečené poznámky k konverzaci  
 Pro vazby, které umožňují zabezpečené konverzace, můžete upravit tato nastavení jak pro kanál aplikace, tak pro zabezpečené konverzace bootstrap vazby. Můžete například vypnout záznamy pro aplikační kanál, ale povolit je pro zaváděcí kanál, který vytváří zabezpečenou konverzaci.  
  
 Pokud nepoužíváte zabezpečené relace konverzace, zjišťování přehrání nezaručuje zjišťování záznamů ve scénářích serverové farmy a při recyklaci procesu. To platí pro následující systémově poskytované vazby:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding>s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastností `false`nastavenou na .  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Ke kompilaci kódu jsou vyžadovány následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
