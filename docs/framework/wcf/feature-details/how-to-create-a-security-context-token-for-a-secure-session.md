---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 36cf5ce1aa6e0eef80123ac7008294062d7faf82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598902"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci
Při použití tokenu kontextového kontextu zabezpečení (SCT) v zabezpečené relaci může relace vydržet recyklaci služby. Například pokud se v zabezpečené relaci používá bezstavový SCT a resetuje se Internetová informační služba (IIS), data relace přidružená ke službě budou ztracena. Tato data relace zahrnují mezipaměť tokenů SCT. Takže když klient příště odešle službu bezstavový SCT, vrátí se chyba, protože klíč, který je přidružený k SCT, nejde načíst. Pokud se ale používá stavový SCT, pak klíč, který je přidružený k SCT, je obsažený v SCT. Vzhledem k tomu, že klíč je obsažen v SCT, a proto obsažený v rámci zprávy, není tato služba ovlivněna tím, že je zajištěna její zabezpečená relace. Ve výchozím nastavení používá Windows Communication Foundation (WCF) v zabezpečené relaci bezstavový SCTs. Toto téma popisuje, jak používat stav SCTs v zabezpečené relaci.  
  
> [!NOTE]
> Stavový SCTs nelze použít v zabezpečené relaci, která zahrnuje kontrakt odvozený od <xref:System.ServiceModel.Channels.IDuplexChannel> .  
  
> [!NOTE]
> Pro aplikace, které používají stav SCTs v zabezpečené relaci, musí být identita vlákna pro službu uživatelským účtem, který má přidružený profil uživatele. Když je služba spuštěna pod účtem, který nemá profil uživatele, například `Local Service` , může být vyvolána výjimka.  
  
> [!NOTE]
> Pokud je v systému Windows XP vyžadován zosobnění, použijte zabezpečenou relaci bez stavového SCT. Pokud se pro zosobnění použijí stavová SCTs, <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Použití stavového SCTsu v zabezpečené relaci  
  
- Vytvořte vlastní vazbu, která určuje, že zprávy SOAP jsou chráněny zabezpečenou relací, která používá stavový SCT.  
  
    1. Definujte vlastní vazbu přidáním [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. Přidejte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) podřízený element do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
         Zadejte název vazby nastavením `name` atributu na jedinečný název v rámci konfiguračního souboru.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. Zadejte režim ověřování pro zprávy odesílané do a z této služby přidáním [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) podřízeného elementu do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
         Určete, že se zabezpečená relace používá, nastavením `authenticationMode` atributu na `SecureConversation` . Určete, že stavová SCTs jsou použita nastavením `requireSecurityContextCancellation` atributu na `false` .  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. Určete, jak se má klient ověřovat, když je zabezpečená relace navázána přidáním [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízeného elementu do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .  
  
         Určete, jak se má klient ověřit, nastavením `authenticationMode` atributu.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Určete kódování zprávy přidáním elementu kódování, například [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Určete přenos přidáním elementu Transport, jako je například [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Následující příklad kódu používá konfiguraci k určení vlastní vazby, kterou mohou zprávy používat se stavovým SCTsem v zabezpečené relaci.  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří vlastní vazbu, která <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pro spuštění zabezpečené relace používá režim ověřování.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Pokud se používá ověřování systému Windows v kombinaci se stavovým SCT, WCF neplní <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost skutečným identifikátorem volajícího, ale místo toho nastaví vlastnost na hodnotu Anonymous. Vzhledem k tomu, že zabezpečení WCF musí znovu vytvořit obsah kontextu zabezpečení služby pro každý požadavek z příchozího SCT, server nesleduje relaci zabezpečení v paměti. Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instanci do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrací anonymní identitu.  
  
 Toto chování se projeví v následující konfiguraci.  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
        </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Viz také

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
