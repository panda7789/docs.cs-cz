---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
ms.openlocfilehash: 85954dd89bdb576b68d234a364a406a6e0d2145b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030340"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci
Pomocí tokenu kontextu zabezpečení stavové (SCT) v zabezpečené relaci dokázal relace neumožňovala recyklaci služby. Například při bezstavové SCT se používá v zabezpečené relaci a obnovit Internetové informační služby (IIS), potom data relace, která souvisí se službou se ztratí. Tato data relace zahrnují SCT mezipaměť tokenu. Proto při příštím klient odešle službě bezstavové SCT vrátí chybu, protože klíč, který je přidružený k SCT nelze načíst. Pokud však použijete stavové SCT, klíč, který je přidružený k SCT obsažené v SCT. Protože klíč je součástí SCT a proto v něm obsažené, nemá vliv službu neumožňovala recyklaci, zabezpečenou relaci. Ve výchozím nastavení používá Windows Communication Foundation (WCF) bezstavové SCTs v zabezpečené relaci. Toto téma podrobně popisuje, jak použít stavová SCTs v zabezpečené relaci.  
  
> [!NOTE]
>  Stavové SCTs nelze použít v zabezpečené relaci, která zahrnuje kontrakt, který je odvozen od <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Pro aplikace, které používají stavové SCTs v zabezpečené relaci identitu vlákna služby musí být uživatelský účet, který se má profil přidruženého uživatele. Když je služba spuštěna pod účtem, který nemá profil uživatele, jako například `Local Service`, může být vyvolána výjimka.  
  
> [!NOTE]
>  Když zosobnění je potřeba na Windows XP, použijte zabezpečené relaci bez stavové SCT. Když zosobnění, se používají stavové SCTs <xref:System.InvalidOperationException> je vyvolána výjimka. Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Použití stavové SCTs v zabezpečené relace  
  
-   Vytvoření vlastní vazby, která určuje, že zprávy protokolu SOAP jsou chráněné službou, která používá stavové SCT zabezpečenou relaci.  
  
    1.  Definujte vlastní vazbu tak, že přidáte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru služby.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Zadejte název vazby tak, že nastavíte `name` atribut jedinečný název v konfiguračním souboru.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Zadejte režim ověřování pro zprávy odeslané do a z této služby tak, že přidáte [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Určí, že je použit zabezpečenou relaci tak, že nastavíte `authenticationMode` atribut `SecureConversation`. Určete, že se používají stavové SCTs nastavením `requireSecurityContextCancellation` atribut `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Zadejte, jak je ověření klienta při vytvoření zabezpečené relace tak, že přidáte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element pro [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Zadejte, jak proběhne ověření nastavení klienta `authenticationMode` atribut.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Určete kódování zprávy přidáním element kódování [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Zadejte přenos přidáním element přenosu [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Následující příklad kódu používá konfigurace k určení vlastní vazby, zprávy můžete použít s stavové SCTs v zabezpečené relaci.  
  
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
 Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování ke spuštění zabezpečenou relaci.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Při ověřování Windows se používá v kombinaci s stavové SCT, WCF nevyplní <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost s skutečné volající vaší identity, ale místo toho vlastnost nastavena na anonymní. Protože zabezpečení WCF muset znovu vytvořit obsah kontext zabezpečení služby pro každý požadavek z příchozí SCT, server přehled o zabezpečení relací v paměti. Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instance do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonymní identity vrátí vlastnost.  
  
 Toto chování je třeba následující konfiguraci.  
  
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
 [\<třídě customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
