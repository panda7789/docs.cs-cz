---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 0b0da7e60cb54a1c3d6eb6d2d557f7312da1e9ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189336"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="7619a-102">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="7619a-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="7619a-103">Pomocí tokenu kontextu zabezpečení stavové (SCT) v zabezpečené relaci dokázal relace neumožňovala recyklaci služby.</span><span class="sxs-lookup"><span data-stu-id="7619a-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="7619a-104">Například při bezstavové SCT se používá v zabezpečené relaci a obnovit Internetové informační služby (IIS), potom data relace, která souvisí se službou se ztratí.</span><span class="sxs-lookup"><span data-stu-id="7619a-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="7619a-105">Tato data relace zahrnují SCT mezipaměť tokenu.</span><span class="sxs-lookup"><span data-stu-id="7619a-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="7619a-106">Proto při příštím klient odešle službě bezstavové SCT vrátí chybu, protože klíč, který je přidružený k SCT nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="7619a-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="7619a-107">Pokud však použijete stavové SCT, klíč, který je přidružený k SCT obsažené v SCT.</span><span class="sxs-lookup"><span data-stu-id="7619a-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="7619a-108">Protože klíč je součástí SCT a proto v něm obsažené, nemá vliv službu neumožňovala recyklaci, zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="7619a-109">Ve výchozím nastavení používá Windows Communication Foundation (WCF) bezstavové SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="7619a-110">Toto téma podrobně popisuje, jak použít stavová SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7619a-111">Stavové SCTs nelze použít v zabezpečené relaci, která zahrnuje kontrakt, který je odvozen od <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="7619a-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7619a-112">Pro aplikace, které používají stavové SCTs v zabezpečené relaci identitu vlákna služby musí být uživatelský účet, který se má profil přidruženého uživatele.</span><span class="sxs-lookup"><span data-stu-id="7619a-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="7619a-113">Když je služba spuštěna pod účtem, který nemá profil uživatele, jako například `Local Service`, může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7619a-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7619a-114">Když zosobnění je potřeba na Windows XP, použijte zabezpečené relaci bez stavové SCT.</span><span class="sxs-lookup"><span data-stu-id="7619a-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="7619a-115">Když zosobnění, se používají stavové SCTs <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7619a-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="7619a-116">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="7619a-117">Použití stavové SCTs v zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="7619a-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="7619a-118">Vytvoření vlastní vazby, která určuje, že zprávy protokolu SOAP jsou chráněné službou, která používá stavové SCT zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="7619a-119">Definujte vlastní vazbu tak, že přidáte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="7619a-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="7619a-120">Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="7619a-121">Zadejte název vazby tak, že nastavíte `name` atribut jedinečný název v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7619a-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="7619a-122">Zadejte režim ověřování pro zprávy odeslané do a z této služby tak, že přidáte [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="7619a-123">Určí, že je použit zabezpečenou relaci tak, že nastavíte `authenticationMode` atribut `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="7619a-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="7619a-124">Určete, že se používají stavové SCTs nastavením `requireSecurityContextCancellation` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="7619a-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="7619a-125">Zadejte, jak je ověření klienta při vytvoření zabezpečené relace tak, že přidáte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element pro [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="7619a-126">Zadejte, jak proběhne ověření nastavení klienta `authenticationMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="7619a-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="7619a-127">Určete kódování zprávy přidáním element kódování [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="7619a-128">Zadejte přenos přidáním element přenosu [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="7619a-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="7619a-129">Následující příklad kódu používá konfigurace k určení vlastní vazby, zprávy můžete použít s stavové SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7619a-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="7619a-130">Example</span></span>  
 <span data-ttu-id="7619a-131">Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování ke spuštění zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="7619a-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="7619a-132">Při ověřování Windows se používá v kombinaci s stavové SCT, WCF nevyplní <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost s skutečné volající vaší identity, ale místo toho vlastnost nastavena na anonymní.</span><span class="sxs-lookup"><span data-stu-id="7619a-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="7619a-133">Protože zabezpečení WCF muset znovu vytvořit obsah kontext zabezpečení služby pro každý požadavek z příchozí SCT, server přehled o zabezpečení relací v paměti.</span><span class="sxs-lookup"><span data-stu-id="7619a-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="7619a-134">Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instance do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonymní identity vrátí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7619a-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="7619a-135">Toto chování je třeba následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7619a-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7619a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7619a-136">See also</span></span>

- [<span data-ttu-id="7619a-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7619a-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
