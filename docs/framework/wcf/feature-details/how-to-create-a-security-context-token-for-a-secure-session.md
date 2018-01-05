---
title: "Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci"
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
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3dc0e44e7f561e39128e32d3af5fbd495316fdd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci
Pomocí tokenu kontextu zabezpečení stavová (SCT) v zabezpečené relaci může relace odolat službu recyklovány. Například při bezstavové SCT se používá v zabezpečené relaci a Internetové informační služby (IIS) je obnovit, pak data relace, která souvisí se službou se ztratí. Tato data relace zahrnuje mezipamětí tokenů SCT. Ano při příštím klient odešle služba bezstavové SCT, vrátí se chyba, protože nelze načíst klíč, který je přidružen SCT. Pokud se ale používá stavová SCT, klíč, který je přidružen SCT obsažené v SCT. Vzhledem k tomu, že klíč obsažené v SCT a proto obsažené v zprávu, není služba recyklovány vliv zabezpečené relace. Ve výchozím nastavení [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] používá bezstavové SCTs v zabezpečené relaci. Toto téma podrobné informace o tom, jak použít stavová SCTs v zabezpečené relaci.  
  
> [!NOTE]
>  Stavová SCTs nelze použít v zabezpečené relaci, která zahrnuje kontraktu, která je odvozena z <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Pro aplikace, které používají stavová SCTs v zabezpečené relaci musí být přístup z více vláken identity pro službu uživatelský účet, který má profil uživatele. Když je služba spuštěna pod účtem, který nemá profil uživatele, jako například `Local Service`, může být vyvolána výjimka.  
  
> [!NOTE]
>  Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez stavová SCT. V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Použít stavová SCTs v zabezpečené relaci  
  
-   Vytvoření vlastní vazby, která určuje, že protokolu SOAP zprávy jsou chráněny zabezpečené relace, který používá stavová SCT.  
  
    1.  Definovat vlastní vazby přidáním [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) podřízený element [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Zadejte název vazby nastavením `name` atribut jedinečný název v rámci konfiguračního souboru.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Zadejte režim ověřování pro zprávy odeslané do a z této služby přidáním [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) podřízený element [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Zadejte, že zabezpečené relace používá nastavení `authenticationMode` atribut `SecureConversation`. Zadejte, že stavová SCTs používají nastavení `requireSecurityContextCancellation` atribut `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Zadejte, jak je ověřený klient během zabezpečené relace je vytvořeno přidáním [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Zadejte, jak se ověřit nastavení klienta `authenticationMode` atribut.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Určete kódování zpráv přidáním element kódování [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Zadejte přenos přidáním element přenosu, například [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Následující příklad kódu používá konfiguraci Pokud chcete zadat vlastní vazby, zprávy můžete použít s stavová SCTs v zabezpečené relaci.  
  
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
 Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování bootstrap zabezpečené relaci.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Při ověřování systému Windows se používá v kombinaci s stavová SCT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] není naplnit <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost s skutečné volající je identity, ale místo toho nastaví vlastnost na anonymní. Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení musíte znovu vytvořit obsah kontext zabezpečení služby pro každý požadavek z příchozí SCT, server není udržovat přehled o zabezpečení relací v paměti. Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instance do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrací anonymní identity.  
  
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
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
