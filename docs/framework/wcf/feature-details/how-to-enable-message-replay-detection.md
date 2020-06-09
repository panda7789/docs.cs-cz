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
ms.openlocfilehash: bf45b39f59e2fe38fec88d1fac23ab824c009546
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597082"
---
# <a name="how-to-enable-message-replay-detection"></a>Postupy: Povolení zjišťování opakování zpráv
K útoku opakovaného přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran. V případě, že počítače, které jsou předmětem útoku, zpracuje datový proud jako legitimní zprávy, což vede k celé řadě špatných důsledků, jako je například redundantní objednávka položky.  
  
 Další informace o detekci opětovného přehrání zpráv najdete v tématu zjištění opětovného [přehrání zprávy](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Následující postup ukazuje různé vlastnosti, které lze použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Řízení zjišťování opakování v klientovi pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding> . Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md). V následujícím příkladu je použita <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Třída vytvořená s <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> třídou.  
  
2. Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnosti vraťte odkaz na <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídu a podle potřeby nastavte libovolné z následujících vlastností:  
  
    1. `DetectReplay`. Logická hodnota Tím se určuje, zda má klient detekovat hry ze serveru. Výchozí formát je `true`.  
  
    2. `MaxClockSkew`. <xref:System.TimeSpan>Hodnota. Určuje, kolik času se má v případě, že je možné mezi klientem a serverem tolerovat mechanismus opakovaného přehrávání. Mechanismus zabezpečení prověřuje odeslané časové razítko a určí, zda byl v minulosti odeslán příliš daleko zpátky. Výchozí hodnota je 5 minut.  
  
    3. `ReplayWindow`. `TimeSpan`Hodnota. To určuje, jak dlouho může zpráva v síti fungovat poté, co ji server pošle (prostřednictvím zprostředkovatelů) před tím, než se dopustí klientovi. Klient sleduje podpisy zpráv odeslaných v rámci nejnovějších `ReplayWindow` pro účely detekce opětovného přehrání.  
  
    4. `ReplayCacheSize`. Celočíselná hodnota. Klient ukládá podpisy zprávy do mezipaměti. Toto nastavení určuje, kolik podpisů může mezipaměť ukládat. Pokud počet zpráv odeslaných v rámci posledního opětovného přehrávání dosáhne limitu mezipaměti, nové zprávy jsou odmítnuty, dokud nedosáhnou nejstarších podpisů v mezipaměti. Výchozí hodnota je 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Řízení zjišťování opakování u služby pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding> .  
  
2. Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnosti vraťte odkaz na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídu a nastavte vlastnosti tak, jak je popsáno výše.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Řízení zjišťování opětovného přehrání v konfiguraci pro klienta nebo službu  
  
1. Vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
2. Vytvořte `<security>` element.  
  
3. Vytvořte [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .  
  
4. Nastavte následující hodnoty atributu podle potřeby: `detectReplays` ,, a `maxClockSkew` `replayWindow` `replayCacheSize` . Následující příklad nastaví atributy prvku `<localServiceSettings>` a i `<localClientSettings>` elementu:  
  
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
 Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody a nastaví vlastnosti opětovného přehrání vazby.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Rozsah přehrání: pouze zabezpečení zprávy  
 Následující postupy platí pouze pro režim zabezpečení zpráv. Pro přenos a přenos s režimem přihlašovacích údajů zpráv zjišťují mechanismy přenosu.  
  
## <a name="secure-conversation-notes"></a>Zabezpečené poznámky ke konverzaci  
 U vazeb, které umožňují zabezpečenou konverzaci, můžete tato nastavení upravit pro kanál aplikace i pro spouštěcí vazby zabezpečené konverzace. Můžete například vypnout přehrávání pro kanál aplikace, ale povolit je pro spouštěcí kanál, který vytváří zabezpečenou konverzaci.  
  
 Pokud nepoužíváte zabezpečené relace konverzace, detekce opětovného přehrání nezaručuje detekci přehrání ve scénářích serverové farmy a při recyklaci procesu. To platí pro následující vazby poskytované systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding>s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastností nastavenou na `false` .  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Pro zkompilování kódu jsou vyžadovány následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Zabezpečené konverzace a zabezpečené relace](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
