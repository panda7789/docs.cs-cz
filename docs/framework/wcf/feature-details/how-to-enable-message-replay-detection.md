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
ms.openlocfilehash: 5c761a23d2560f40a0121d684dcb411a716de5a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497136"
---
# <a name="how-to-enable-message-replay-detection"></a>Postupy: Povolení zjišťování opakování zpráv
Opakování útoku nastane, když útočník zkopíruje datového proudu zpráv mezi dvěma účastníky a replays datový proud na jeden nebo více stran. Pokud omezeny, budou počítače podřízené útoku zpracovat datového proudu jako legitimní zprávy, což vede k řadu chybný důsledky, jako je například redundantní objednávky položky.  
  
 Další informace o zjišťování opakování zpráv najdete v tématu [zjišťování opakování zpráv](http://go.microsoft.com/fwlink/?LinkId=88536).  
  
 Následující postup ukazuje různé vlastnosti, které můžete použít k řízení rozpoznání opětovného přehrání pomocí služby Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>K řízení rozpoznání opětovného přehrání na straně klienta pomocí kódu  
  
1.  Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>. Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
2.  Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnost vrací odkaz na <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy a podle potřeby nastavte následující vlastnosti:  
  
    1.  `DetectReplay`. Logická hodnota. To řídí, zda klient by měl zjistit opětovná přehrání ze serveru. Výchozí hodnota je `true`.  
  
    2.  `MaxClockSkew`. A <xref:System.TimeSpan> hodnotu. Řídí, kolik času zkosení mechanismus opakování tolerovat mezi klientem a serverem. Tento mechanismus zabezpečení prověří časové razítko odesílají a určuje, zda byl odeslán příliš daleko zpět v minulosti. Výchozí hodnota je 5 minut.  
  
    3.  `ReplayWindow`. A `TimeSpan` hodnotu. To řídí, jak dlouho zprávu můžete za provozu v síti po server odešle (přes prostředníci) dříve, než dorazila klienta. Klient sleduje podpis zprávy odeslané v rámci nejnovější `ReplayWindow` pro účely rozpoznání opětovného přehrání.  
  
    4.  `ReplayCacheSize`. Celočíselná hodnota. Klient ukládá do mezipaměti podpisů zprávy. Toto nastavení určuje, kolik podpisy může ukládat do mezipaměti. Pokud počet zpráv odeslaných v rámci poslední období opakování dosáhne limitu mezipaměti, jsou odmítnuta nové zprávy, dokud nejstarší uložené v mezipaměti podpisy nezobrazí časový limit. Výchozí hodnota je 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>K řízení rozpoznání opětovného přehrání na úrovni služby pomocí kódu  
  
1.  Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnost vrací odkaz na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy a nastavte vlastnosti, jak je popsáno výše.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>K řízení rozpoznání opětovného přehrání v konfiguraci pro klienta nebo služby  
  
1.  Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Vytvoření `<security>` elementu.  
  
3.  Vytvoření [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Podle potřeby nastavte následující hodnoty atributu: `detectReplays`, `maxClockSkew`, `replayWindow`, a `replayCacheSize`. Následující příklad nastaví atributy i `<localServiceSettings>` a `<localClientSettings>` element:  
  
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
  
## <a name="scope-of-replay-message-security-only"></a>Rozsah opětovného přehrání: pouze zabezpečení zpráv  
 Všimněte si, že následující postupy platí pouze pro režim zabezpečení zprávy. Mechanismy přenos pro přenos a přenos s pověřením zpráv režimy rozpoznat opětovná přehrání.  
  
## <a name="secure-conversation-notes"></a>Zabezpečené konverzace poznámky  
 U vazeb, které umožňují zabezpečené konverzace můžete upravit tato nastavení pro aplikace kanál i pro vazbu bootstrap zabezpečené konverzaci. Například můžete vypnout opětovná přehrání pro kanál aplikace ale mohly pro spouštěcí kanál, který stanoví k zabezpečené konverzaci.  
  
 Pokud nepoužijete zabezpečené konverzaci relací, rozpoznání opětovného přehrání nezaručuje zjišťování opětovná přehrání v scénáře serveru farmy a když se proces recykluje. To platí pro následující vazby poskytované systémem:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> pomocí <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost nastavena na hodnotu `false`.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Následující obory názvů jsou nezbytné pro kompilaci kódu:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Zabezpečené konverzace a zabezpečené relace](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
