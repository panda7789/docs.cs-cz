---
title: 'Postupy: Nastavení hodnoty vlastnosti MaxClockSkew'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586911"
---
# <a name="how-to-set-a-max-clock-skew"></a>Postupy: Nastavení hodnoty vlastnosti MaxClockSkew
V případě, že se nastavení hodin ve dvou počítačích liší, je možné časově kritické funkce dekolejnice. Pro zmírnění této možnosti můžete nastavit `MaxClockSkew` vlastnost na <xref:System.TimeSpan> . Tato vlastnost je k dispozici na dvou třídách:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> V případě zabezpečené konverzace je `MaxClockSkew` třeba provést změny vlastnosti při zavedení služby nebo klienta. K tomu je nutné nastavit vlastnost <xref:System.ServiceModel.Channels.SecurityBindingElement> vrácenou <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> vlastností.  
  
 Chcete-li změnit vlastnost u jedné z vazeb poskytovaných systémem, je nutné najít prvek vazby zabezpečení v kolekci vazeb a nastavit `MaxClockSkew` vlastnost na novou hodnotu. Dvě třídy jsou odvozeny z <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . Při načítání vazby zabezpečení z kolekce je třeba přetypovat na jeden z těchto typů, aby bylo možné správně nastavit `MaxClockSkew` vlastnost. Následující příklad používá <xref:System.ServiceModel.WSHttpBinding> , který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Seznam, který určuje typ vazby zabezpečení, který se má použít v každé vazbě poskytované systémem, najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Vytvoření vlastní vazby s novou hodnotou asymetrie hodin v kódu  
  
> [!WARNING]
> Do kódu přidejte odkazy na následující obory názvů: <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> a <xref:System.ServiceModel.Security.Tokens> .  
  
1. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .  
  
2. Vytvořte novou instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy voláním <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> <xref:System.ServiceModel.Channels.BindingElementCollection> K nalezení elementu vazby zabezpečení použijte metodu třídy.  
  
4. Při použití <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody přetypovat na skutečný typ. Níže uvedený příklad přetypování na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typ.  
  
5. Nastavte <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnost na elementu vazby zabezpečení.  
  
6. Vytvořte <xref:System.ServiceModel.ServiceHost> s příslušným typem služby a základní adresou.  
  
7. Použijte <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metodu pro přidání koncového bodu a zahrnutí <xref:System.ServiceModel.Channels.CustomBinding> .  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Nastavení MaxClockSkew v konfiguraci  
  
1. Vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) v [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) oddílu element.  
  
2. Vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) prvek a nastavte `name` atribut na odpovídající hodnotu. Následující příklad nastaví na `MaxClockSkewBinding` .  
  
3. Přidejte element Encoding. Následující příklad přidá [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .  
  
4. Přidejte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element a nastavte `authenticationMode` atribut na příslušné nastavení. Následující příklad nastaví atribut tak, aby `Kerberos` určoval, že služba používá ověřování systému Windows.  
  
5. Přidejte [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atribut na hodnotu ve formě `"##:##:##"` . V následujícím příkladu se nastaví na 7 minut. Volitelně přidejte [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte `maxClockSkew` atribut na příslušné nastavení.  
  
6. Přidejte transportní element. Následující příklad používá [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .  
  
7. Pro zabezpečenou konverzaci musí být nastavení zabezpečení provedeno při spuštění v [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.  
  
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

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
