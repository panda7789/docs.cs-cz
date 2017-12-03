---
title: "Postupy: Sada zkosení max. frekvence"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31548f3190425f4c50e68369320828b11ee3928c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-set-a-max-clock-skew"></a>Postupy: Sada zkosení max. frekvence
Kritický pro čas funkce můžete kolejnic, pokud se nastavení hodin na dva počítače liší. Pro zmírnění této možnosti, můžete nastavit `MaxClockSkew` vlastnosti <xref:System.TimeSpan>. Tato vlastnost je k dispozici na dvě třídy:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Důležité pro zabezpečenou konverzaci, změny `MaxClockSkew` vlastnost musí být provedeny, když je připravili služba nebo klienta. K tomuto účelu musí nastavit vlastnost na <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácený <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Chcete-li změnit vlastnost na jednom z vazby poskytované systémem, je nutné vyhledat prvku vazby zabezpečení v kolekci vazby a nastavit `MaxClockSkew` vlastnost na novou hodnotu. Dvě třídy odvozovat <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Při načítání vazby zabezpečení z kolekce, musíte vysílat na jeden z těchto typů Chcete-li správně nastavit `MaxClockSkew` vlastnost. Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, které používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Seznam, který určuje typ zabezpečení vazby pro použití v každé vazby poskytované systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Chcete-li vytvořit vlastní vazby s novou hodin zkreslit hodnotu v kódu  
  
1.  > [!WARNING]
    >  Všimněte si, přidat odkazy na následující obory názvů v kódu: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, a <xref:System.ServiceModel.Security.Tokens>.  
  
     Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Vytvořit novou instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> třída voláním <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metoda.  
  
3.  Použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metodu <xref:System.ServiceModel.Channels.BindingElementCollection> třída pro vyhledání prvku vazby zabezpečení.  
  
4.  Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody přetypovat na typ skutečný. V příkladu níže přetypování k <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.  
  
5.  Nastavte <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnost u prvku vazby zabezpečení.  
  
6.  Vytvoření <xref:System.ServiceModel.ServiceHost> adresu typu a základní příslušnou službu.  
  
7.  Použití <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda přidání koncového bodu a zahrnout do odpovědi <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Chcete-li nastavit maxclockskew – v konfiguraci  
  
1.  Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) v [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) část elementu.  
  
2.  Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu a sadu `name` atribut na odpovídající hodnotu. Následující příklad ji nastaví na `MaxClockSkewBinding`.  
  
3.  Přidáte element kódování. Příklad dole přidá [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Přidat [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu a sadu `authenticationMode` atribut vhodné nastavení. Následující příklad nastavením atributu na `Kerberos` k určení, že služba použít ověřování systému Windows.  
  
5.  Přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atributu na hodnotu ve formě `"##:##:##"`. Následující příklad ji nastaví na 7 minut. Volitelně lze přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atribut vhodné nastavení.  
  
6.  Přidá prvek přenosu. Následující příklad používá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Pro zabezpečenou konverzaci, musí dojít nastavení zabezpečení na bootstrap v [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
