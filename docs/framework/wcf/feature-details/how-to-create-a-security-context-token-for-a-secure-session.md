---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 02e0403f9ae5bb437145fa3a015edc69b884c4d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185020"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci
Pomocí stavového tokenu kontextu zabezpečení (SCT) v zabezpečené relaci může relace odolat recyklované službě. Například při bezstavové SCT se používá v zabezpečené relaci a Internetové informační služby (IIS) je resetován, pak dojde ke ztrátě dat relace, která je přidružena ke službě. Tato data relace obsahuje mezipaměť tokenů SCT. Takže při příštím klient odešle službu bezstavové SCT, je vrácena chyba, protože klíč, který je spojen s SCT nelze načíst. Pokud se však používá stavové SCT, pak klíč, který je spojen s SCT je obsažen v SCT. Vzhledem k tomu, že klíč je obsažen v SCT a tedy obsažené ve zprávě, zabezpečené relace není ovlivněna služby recyklované. Ve výchozím nastavení Windows Communication Foundation (WCF) používá bezstavové SCT s v zabezpečené relaci. Toto téma podrobně popisuje, jak používat stavové st v zabezpečené relaci.  
  
> [!NOTE]
> Stavové scs nelze použít v zabezpečené relace, která zahrnuje <xref:System.ServiceModel.Channels.IDuplexChannel>smlouvu, která je odvozena od .  
  
> [!NOTE]
> Pro aplikace, které používají stavové ST v zabezpečené relaci, musí být identita vlákna pro službu uživatelský účet, který má přidružený profil uživatele. Při spuštění služby pod účet, který nemá profil `Local Service`uživatele, například , může být vyvolána výjimka.  
  
> [!NOTE]
> Pokud je v systému Windows XP vyžadováno zosobnění, použijte zabezpečenou relaci bez stavové sct. Při stavové ST s jsou používány <xref:System.InvalidOperationException> s zosobnění, je vyvolána. Další informace naleznete v tématu [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Použití stavových stes v zabezpečené relaci  
  
- Vytvořte vlastní vazbu, která určuje, že zprávy SOAP jsou chráněny zabezpečenou relací, která používá stavovou sct.  
  
    1. Definujte vlastní vazbu přidáním [ \<vlastní vazby>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. Přidejte [ \<podřízený](../../configure-apps/file-schema/wcf/bindings.md) prvek vazby>do [ \<>vlastní vazby ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Zadejte název vazby `name` nastavením atributu na jedinečný název v konfiguračním souboru.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. Zadejte režim ověřování pro zprávy odeslané do a z této služby přidáním [ \<>podřízeného](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku zabezpečení do [ \<>vlastní vazby ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Určete, že zabezpečená `authenticationMode` relace `SecureConversation`se používá nastavením atributu na . Určete, že stavové ST se `requireSecurityContextCancellation` používají `false`nastavením atributu .  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Určete, jak je klient ověřen při vytvoření zabezpečené relace přidáním [ \<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený prvek do [ \<>zabezpečení ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Určete způsob ověřování klienta `authenticationMode` nastavením atributu.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Zadejte kódování zprávy přidáním prvku kódování, například [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Zadejte přenos přidáním prvku přenosu, jako je například [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Následující příklad kódu používá konfiguraci k určení vlastní vazby, kterou mohou zprávy používat se stavovými st v zabezpečené relaci.  
  
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
 Následující příklad kódu vytvoří vlastní vazbu, která používá režim <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> ověřování k zavádění zabezpečené relace.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Při ověřování systému Windows se používá v kombinaci se <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> stavovou SCT, WCF nenaplní vlastnost s identitou skutečného volajícího, ale místo toho nastaví vlastnost anonymní. Vzhledem k tomu, že zabezpečení WCF musí znovu vytvořit obsah kontextu zabezpečení služby pro každý požadavek z příchozí hospo- Protože není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instanci do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrátí anonymní identitu.  
  
 Následující konfigurace vykazuje toto chování.  
  
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

- [\<vlastní vazba>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
