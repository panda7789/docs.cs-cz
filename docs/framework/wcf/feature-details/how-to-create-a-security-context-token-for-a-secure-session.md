---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 579a980d8d71b5fe3e21e49e84a602b3be37eff1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="b129d-102">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="b129d-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="b129d-103">Pomocí tokenu kontextu zabezpečení stavová (SCT) v zabezpečené relaci může relace odolat službu recyklovány.</span><span class="sxs-lookup"><span data-stu-id="b129d-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="b129d-104">Například při bezstavové SCT se používá v zabezpečené relaci a Internetové informační služby (IIS) je obnovit, pak data relace, která souvisí se službou se ztratí.</span><span class="sxs-lookup"><span data-stu-id="b129d-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="b129d-105">Tato data relace zahrnuje mezipamětí tokenů SCT.</span><span class="sxs-lookup"><span data-stu-id="b129d-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="b129d-106">Ano při příštím klient odešle služba bezstavové SCT, vrátí se chyba, protože nelze načíst klíč, který je přidružen SCT.</span><span class="sxs-lookup"><span data-stu-id="b129d-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="b129d-107">Pokud se ale používá stavová SCT, klíč, který je přidružen SCT obsažené v SCT.</span><span class="sxs-lookup"><span data-stu-id="b129d-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="b129d-108">Vzhledem k tomu, že klíč obsažené v SCT a proto obsažené v zprávu, není služba recyklovány vliv zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="b129d-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="b129d-109">Ve výchozím nastavení [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] používá bezstavové SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="b129d-109">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="b129d-110">Toto téma podrobné informace o tom, jak použít stavová SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="b129d-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b129d-111">Stavová SCTs nelze použít v zabezpečené relaci, která zahrnuje kontraktu, která je odvozena z <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="b129d-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b129d-112">Pro aplikace, které používají stavová SCTs v zabezpečené relaci musí být přístup z více vláken identity pro službu uživatelský účet, který má profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="b129d-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="b129d-113">Když je služba spuštěna pod účtem, který nemá profil uživatele, jako například `Local Service`, může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b129d-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b129d-114">Když zosobnění je potřeba na systému Windows XP, použijte zabezpečené relace bez stavová SCT.</span><span class="sxs-lookup"><span data-stu-id="b129d-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="b129d-115">V případě stavová SCTs používají s zosobnění, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b129d-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="b129d-116">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="b129d-117">Použít stavová SCTs v zabezpečené relaci</span><span class="sxs-lookup"><span data-stu-id="b129d-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="b129d-118">Vytvoření vlastní vazby, která určuje, že protokolu SOAP zprávy jsou chráněny zabezpečené relace, který používá stavová SCT.</span><span class="sxs-lookup"><span data-stu-id="b129d-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="b129d-119">Definovat vlastní vazby přidáním [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="b129d-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="b129d-120">Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) podřízený element [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="b129d-121">Zadejte název vazby nastavením `name` atribut jedinečný název v rámci konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b129d-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="b129d-122">Zadejte režim ověřování pro zprávy odeslané do a z této služby přidáním [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) podřízený element [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="b129d-123">Zadejte, že zabezpečené relace používá nastavení `authenticationMode` atribut `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="b129d-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="b129d-124">Zadejte, že stavová SCTs používají nastavení `requireSecurityContextCancellation` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="b129d-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="b129d-125">Zadejte, jak je ověřený klient během zabezpečené relace je vytvořeno přidáním [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="b129d-126">Zadejte, jak se ověřit nastavení klienta `authenticationMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="b129d-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="b129d-127">Určete kódování zpráv přidáním element kódování [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="b129d-128">Zadejte přenos přidáním element přenosu, například [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="b129d-129">Následující příklad kódu používá konfiguraci Pokud chcete zadat vlastní vazby, zprávy můžete použít s stavová SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="b129d-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b129d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b129d-130">Example</span></span>  
 <span data-ttu-id="b129d-131">Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování bootstrap zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="b129d-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="b129d-132">Při ověřování systému Windows se používá v kombinaci s stavová SCT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] není naplnit <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost s skutečné volající je identity, ale místo toho nastaví vlastnost na anonymní.</span><span class="sxs-lookup"><span data-stu-id="b129d-132">When Windows authentication is used in combination with a stateful SCT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="b129d-133">Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení musíte znovu vytvořit obsah kontext zabezpečení služby pro každý požadavek z příchozí SCT, server není udržovat přehled o zabezpečení relací v paměti.</span><span class="sxs-lookup"><span data-stu-id="b129d-133">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="b129d-134">Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instance do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrací anonymní identity.</span><span class="sxs-lookup"><span data-stu-id="b129d-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="b129d-135">Následující konfigurace vykazuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="b129d-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b129d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="b129d-136">See Also</span></span>  
 [<span data-ttu-id="b129d-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b129d-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
