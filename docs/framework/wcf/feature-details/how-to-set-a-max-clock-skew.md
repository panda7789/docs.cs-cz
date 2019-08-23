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
ms.openlocfilehash: 3bcd128e6e9f53f662dd3fc99336b5b45faebf5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943120"
---
# <a name="how-to-set-a-max-clock-skew"></a>Postupy: Nastvení hodnoty vlastnosti MaxClockSkew
V případě, že se nastavení hodin ve dvou počítačích liší, je možné časově kritické funkce dekolejnice. Pro zmírnění této možnosti můžete nastavit `MaxClockSkew` vlastnost <xref:System.TimeSpan>na. Tato vlastnost je k dispozici na dvou třídách:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> V případě zabezpečené konverzace je třeba provést změny `MaxClockSkew` vlastnosti při zavedení služby nebo klienta. K tomu je nutné nastavit vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácenou <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> vlastností.  
  
 Chcete-li změnit vlastnost u jedné z vazeb poskytovaných systémem, je nutné najít prvek vazby zabezpečení v kolekci vazeb a nastavit `MaxClockSkew` vlastnost na novou hodnotu. Dvě třídy jsou odvozeny <xref:System.ServiceModel.Channels.SecurityBindingElement>z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> : <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>a. Při načítání vazby zabezpečení z kolekce je třeba přetypovat na jeden z těchto typů, aby bylo možné správně nastavit `MaxClockSkew` vlastnost. Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>používá. Seznam, který určuje typ vazby zabezpečení, který se má použít v každé vazbě poskytované systémem, najdete v tématu [vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Vytvoření vlastní vazby s novou hodnotou asymetrie hodin v kódu  
  
> [!WARNING]
> Do kódu přidejte odkazy na následující obory názvů: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>a <xref:System.ServiceModel.Security.Tokens>.  
  
1. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.  
  
2. Vytvořte novou instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> voláním metody.  
  
3. K nalezení elementu vazby zabezpečení <xref:System.ServiceModel.Channels.BindingElementCollection> použijte metodutřídy.<xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>  
  
4. Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody přetypovat na skutečný typ. Níže uvedený příklad přetypování na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typ.  
  
5. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> Nastavte vlastnost na elementu vazby zabezpečení.  
  
6. <xref:System.ServiceModel.ServiceHost> Vytvořte s příslušným typem služby a základní adresou.  
  
7. Použijte metodu pro přidání koncového bodu a <xref:System.ServiceModel.Channels.CustomBinding>zahrnutí. <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Nastavení MaxClockSkew v konfiguraci  
  
1. Vytvořte > CustomBinding v části > elementu [ Bindings.\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
2. Vytvořte vazbu [ >elementuanastavteatributnaodpovídajícíhodnotu.\<](../../../../docs/framework/misc/binding.md) `name` Následující příklad nastaví na `MaxClockSkewBinding`.  
  
3. Přidejte element Encoding. Následující příklad přidá [ \<> textMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4. Přidejte element [Security > a nastavte atribut na příslušné nastavení. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `authenticationMode` Následující příklad nastaví atribut tak `Kerberos` , aby určoval, že služba používá ověřování systému Windows.  
  
5. Přidejte > `maxClockSkew` `"##:##:##"`localServiceSettings a nastavte atribut na hodnotu ve formě. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) V následujícím příkladu se nastaví na 7 minut. Volitelně přidejte [ \<> localServiceSettings](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atribut na příslušné nastavení.  
  
6. Přidejte transportní element. Následující příklad používá [ \<> HttpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7. Pro zabezpečenou konverzaci musí být nastavení zabezpečení provedeno při spuštění v [ \<elementu secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
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
