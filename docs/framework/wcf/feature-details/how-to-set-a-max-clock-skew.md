---
title: 'Postupy: Nastvení hodnoty vlastnosti MaxClockSkew'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 1a8d99e5d2bd21a74318718f43b5d1c091ed073e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322144"
---
# <a name="how-to-set-a-max-clock-skew"></a>Postupy: Nastvení hodnoty vlastnosti MaxClockSkew
Kritického pro čas funkce můžete kolejnic, pokud se nastavení hodin na dva počítače liší. Pro zmírnění této možnosti můžete nastavit `MaxClockSkew` vlastnost <xref:System.TimeSpan>. Tato vlastnost je k dispozici na dvou tříd:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Důležité pro zabezpečené konverzace, změní `MaxClockSkew` vlastnost musí vzít v úvahu si připravili službu nebo klienta. Chcete-li to provést, musíte nastavit vlastnost na <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácených <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Chcete-li změnit vlastnosti na jednom z vazeb poskytovaných systémem, musíte najít element vazby zabezpečení v kolekci vazby a nastavit `MaxClockSkew` vlastnost na novou hodnotu. Dvě třídy odvozovat <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Při načítání vazby zabezpečení z kolekce, musíte přetypovat na jeden z těchto typů aby bylo možné správně nastavená `MaxClockSkew` vlastnost. Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Seznam, který určuje, který typ zabezpečení vazby pro použití v jednotlivých vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>K vytvoření vlastní vazby s novou hodinami zkosení hodnotu v kódu  
  
1. > [!WARNING]
    >  Všimněte si přidat odkazy na následující obory názvů v kódu: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, a <xref:System.ServiceModel.Security.Tokens>.  
  
     Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>.  
  
2. Vytvořit novou instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> třídy voláním <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3. Použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metodu <xref:System.ServiceModel.Channels.BindingElementCollection> třídy najít element vazby zabezpečení.  
  
4. Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metoda přetypovat na skutečný typ. V příkladu níže přetypování <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.  
  
5. Nastavte <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnosti prvku vazby zabezpečení.  
  
6. Vytvoření <xref:System.ServiceModel.ServiceHost> typ a základní adresou příslušnou službu.  
  
7. Použití <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> způsob přidání koncového bodu a zahrnout <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Chcete-li nastavit maxclockskew – v konfiguraci  
  
1. Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) v [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekce prvku.  
  
2. Vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu a nastavte `name` atribut na odpovídající hodnotu. Následující příklad nastaví na `MaxClockSkewBinding`.  
  
3. Přidáte element kódování. Následující příklad přidá [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Přidat [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu a nastavte `authenticationMode` atribut se vhodným nastavením. V následujícím příkladu nastavte atribut na `Kerberos` určující, zda služba ověřování Windows.  
  
5. Přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavit `maxClockSkew` atribut na hodnotu ve formě `"##:##:##"`. Následující příklad nastaví ji na 7 minut. Volitelně můžete přidat [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavit `maxClockSkew` atribut se vhodným nastavením.  
  
6. Přidáte element přenosu. Následující příklad používá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. Pro zabezpečené konverzace, nastavení zabezpečení se musí vyskytovat na spuštění v [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
