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
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964658"
---
# <a name="how-to-enable-message-replay-detection"></a>Postupy: Povolení zjišťování opakování zpráv
K útoku opakovaného přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran. V případě, že počítače, které jsou předmětem útoku, zpracuje datový proud jako legitimní zprávy, což vede k celé řadě špatných důsledků, jako je například redundantní objednávka položky.  
  
 Další informace o detekci opětovného přehrání zpráv najdete v tématu zjištění opětovného [přehrání zprávy](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 Následující postup ukazuje různé vlastnosti, které lze použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Řízení zjišťování opakování v klientovi pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vraťte odkaz na třídu <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> a podle potřeby nastavte některou z následujících vlastností:  
  
    1. `DetectReplay`. Logická hodnota Tím se určuje, zda má klient detekovat hry ze serveru. Výchozí hodnota je `true`.  
  
    2. `MaxClockSkew`. Hodnota <xref:System.TimeSpan>. Určuje, kolik času se má v případě, že je možné mezi klientem a serverem tolerovat mechanismus opakovaného přehrávání. Mechanismus zabezpečení prověřuje odeslané časové razítko a určí, zda byl v minulosti odeslán příliš daleko zpátky. Výchozí hodnota je 5 minut.  
  
    3. `ReplayWindow`. Hodnota `TimeSpan`. To určuje, jak dlouho může zpráva v síti fungovat poté, co ji server pošle (prostřednictvím zprostředkovatelů) před tím, než se dopustí klientovi. Klient sleduje podpisy zpráv odeslaných v rámci nejnovější `ReplayWindow` pro účely detekce opětovného přehrání.  
  
    4. `ReplayCacheSize`. Celočíselná hodnota. Klient ukládá podpisy zprávy do mezipaměti. Toto nastavení určuje, kolik podpisů může mezipaměť ukládat. Pokud počet zpráv odeslaných v rámci posledního opětovného přehrávání dosáhne limitu mezipaměti, nové zprávy jsou odmítnuty, dokud nedosáhnou nejstarších podpisů v mezipaměti. Výchozí hodnota je 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Řízení zjišťování opakování u služby pomocí kódu  
  
1. Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2. Pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vraťte odkaz na třídu <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> a nastavte vlastnosti tak, jak je popsáno výše.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Řízení zjišťování opětovného přehrání v konfiguraci pro klienta nebo službu  
  
1. Vytvořte [\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Vytvořte `<security>` element.  
  
3. Vytvořte [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Nastavte následující hodnoty atributu podle potřeby: `detectReplays`, `maxClockSkew`, `replayWindow`a `replayCacheSize`. Následující příklad nastaví atributy `<localServiceSettings>` a `<localClientSettings>` elementu:  
  
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
 Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> a nastaví vlastnosti opětovného přehrání vazby.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Rozsah přehrání: pouze zabezpečení zprávy  
 Následující postupy platí pouze pro režim zabezpečení zpráv. Pro přenos a přenos s režimem přihlašovacích údajů zpráv zjišťují mechanismy přenosu.  
  
## <a name="secure-conversation-notes"></a>Zabezpečené poznámky ke konverzaci  
 U vazeb, které umožňují zabezpečenou konverzaci, můžete tato nastavení upravit pro kanál aplikace i pro spouštěcí vazby zabezpečené konverzace. Můžete například vypnout přehrávání pro kanál aplikace, ale povolit je pro spouštěcí kanál, který vytváří zabezpečenou konverzaci.  
  
 Pokud nepoužíváte zabezpečené relace konverzace, detekce opětovného přehrání nezaručuje detekci přehrání ve scénářích serverové farmy a při recyklaci procesu. To platí pro následující vazby poskytované systémem:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding> s vlastností <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenou na `false`.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Pro zkompilování kódu jsou vyžadovány následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
