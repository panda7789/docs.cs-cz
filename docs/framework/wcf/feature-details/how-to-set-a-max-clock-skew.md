---
title: 'Postupy: nastavení maximálního zešikmení času'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141656"
---
# <a name="how-to-set-a-max-clock-skew"></a>Postupy: nastavení maximálního zešikmení času
V případě, že se nastavení hodin ve dvou počítačích liší, je možné časově kritické funkce dekolejnice. Pro zmírnění této možnosti můžete nastavit vlastnost `MaxClockSkew` na <xref:System.TimeSpan>. Tato vlastnost je k dispozici na dvou třídách:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> V případě zabezpečené konverzace se musí při spuštění služby nebo klienta provést změny vlastnosti `MaxClockSkew`. Chcete-li to provést, musíte nastavit vlastnost u <xref:System.ServiceModel.Channels.SecurityBindingElement> vráceného vlastností <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.  
  
 Chcete-li změnit vlastnost u jedné z vazeb poskytovaných systémem, je nutné najít prvek vazby zabezpečení v kolekci vazeb a nastavit vlastnost `MaxClockSkew` na novou hodnotu. Dvě třídy jsou odvozeny od <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Při načítání vazby zabezpečení z kolekce je třeba přetypovat na jeden z těchto typů, aby bylo možné správně nastavit vlastnost `MaxClockSkew`. Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Seznam, který určuje typ vazby zabezpečení, který se má použít v každé vazbě poskytované systémem, najdete v tématu [vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Vytvoření vlastní vazby s novou hodnotou asymetrie hodin v kódu  
  
> [!WARNING]
> Do kódu přidejte odkazy na následující obory názvů: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>a <xref:System.ServiceModel.Security.Tokens>.  
  
1. Vytvořte instanci třídy <xref:System.ServiceModel.WSHttpBinding> a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.  
  
2. Vytvořte novou instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> voláním metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.  
  
3. K nalezení elementu vazby zabezpečení použijte metodu <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> třídy <xref:System.ServiceModel.Channels.BindingElementCollection>.  
  
4. Při použití metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> přetypování na skutečný typ. Níže uvedený příklad přetypování na typ <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
5. Nastavte vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> v elementu vazby zabezpečení.  
  
6. Vytvořte <xref:System.ServiceModel.ServiceHost> s příslušným typem služby a základní adresou.  
  
7. Použijte metodu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> pro přidání koncového bodu a zahrnutí <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Nastavení MaxClockSkew v konfiguraci  
  
1. Vytvořte [\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) v části [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
2. Vytvořte [\<vazbu >](../../configure-apps/file-schema/wcf/bindings.md) elementu a nastavte atribut `name` na odpovídající hodnotu. Následující příklad nastaví `MaxClockSkewBinding`.  
  
3. Přidejte element Encoding. Následující příklad přidá [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Přidejte prvek [> zabezpečení\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) a nastavte atribut `authenticationMode` na příslušné nastavení. Následující příklad nastaví atribut tak, aby `Kerberos` určit, že služba používá ověřování systému Windows.  
  
5. Přidejte [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte atribut `maxClockSkew` na hodnotu ve formě `"##:##:##"`. V následujícím příkladu se nastaví na 7 minut. Volitelně přidejte [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte atribut `maxClockSkew` na příslušné nastavení.  
  
6. Přidejte transportní element. Následující příklad používá [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. Pro zabezpečenou konverzaci musí být nastavení zabezpečení provedeno při spuštění v prvku [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
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
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
