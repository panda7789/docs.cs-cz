---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 4e91580035d4de23ae90cd0d59a08f321ae70a1c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464140"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="ff65c-102">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="ff65c-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="ff65c-103">Pomocí stavového tokenu kontextu zabezpečení (SCT) v zabezpečené relaci může relace odolat recyklované službě.</span><span class="sxs-lookup"><span data-stu-id="ff65c-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="ff65c-104">Například při bezstavové SCT se používá v zabezpečené relaci a Internetové informační služby (IIS) je resetován, pak dojde ke ztrátě dat relace, která je přidružena ke službě.</span><span class="sxs-lookup"><span data-stu-id="ff65c-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="ff65c-105">Tato data relace obsahuje mezipaměť tokenů SCT.</span><span class="sxs-lookup"><span data-stu-id="ff65c-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="ff65c-106">Takže při příštím klient odešle službu bezstavové SCT, je vrácena chyba, protože klíč, který je spojen s SCT nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="ff65c-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="ff65c-107">Pokud se však používá stavové SCT, pak klíč, který je spojen s SCT je obsažen v SCT.</span><span class="sxs-lookup"><span data-stu-id="ff65c-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="ff65c-108">Vzhledem k tomu, že klíč je obsažen v SCT a tedy obsažené ve zprávě, zabezpečené relace není ovlivněna služby recyklované.</span><span class="sxs-lookup"><span data-stu-id="ff65c-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="ff65c-109">Ve výchozím nastavení Windows Communication Foundation (WCF) používá bezstavové SCT s v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ff65c-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="ff65c-110">Toto téma podrobně popisuje, jak používat stavové st v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ff65c-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff65c-111">Stavové scs nelze použít v zabezpečené relace, která zahrnuje <xref:System.ServiceModel.Channels.IDuplexChannel>smlouvu, která je odvozena od .</span><span class="sxs-lookup"><span data-stu-id="ff65c-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff65c-112">Pro aplikace, které používají stavové ST v zabezpečené relaci, musí být identita vlákna pro službu uživatelský účet, který má přidružený profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="ff65c-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="ff65c-113">Při spuštění služby pod účet, který nemá profil `Local Service`uživatele, například , může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ff65c-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff65c-114">Pokud je v systému Windows XP vyžadováno zosobnění, použijte zabezpečenou relaci bez stavové sct.</span><span class="sxs-lookup"><span data-stu-id="ff65c-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="ff65c-115">Při stavové ST s jsou používány <xref:System.InvalidOperationException> s zosobnění, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="ff65c-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="ff65c-116">Další informace naleznete v tématu [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="ff65c-117">Použití stavových stes v zabezpečené relaci</span><span class="sxs-lookup"><span data-stu-id="ff65c-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="ff65c-118">Vytvořte vlastní vazbu, která určuje, že zprávy SOAP jsou chráněny zabezpečenou relací, která používá stavovou sct.</span><span class="sxs-lookup"><span data-stu-id="ff65c-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="ff65c-119">Definujte vlastní vazbu přidáním [ \<vlastní vazby>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="ff65c-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="ff65c-120">Přidejte [ \<podřízený](../../configure-apps/file-schema/wcf/bindings.md) prvek vazby>do [ \<>vlastní vazby ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ff65c-121">Zadejte název vazby `name` nastavením atributu na jedinečný název v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ff65c-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="ff65c-122">Zadejte režim ověřování pro zprávy odeslané do a z této služby přidáním [ \<>podřízeného](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) prvku zabezpečení do [ \<>vlastní vazby ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ff65c-123">Určete, že zabezpečená `authenticationMode` relace `SecureConversation`se používá nastavením atributu na .</span><span class="sxs-lookup"><span data-stu-id="ff65c-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="ff65c-124">Určete, že stavové ST se `requireSecurityContextCancellation` používají `false`nastavením atributu .</span><span class="sxs-lookup"><span data-stu-id="ff65c-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="ff65c-125">Určete, jak je klient ověřen při vytvoření zabezpečené relace přidáním [ \<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený prvek do [ \<>zabezpečení ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="ff65c-126">Určete způsob ověřování klienta `authenticationMode` nastavením atributu.</span><span class="sxs-lookup"><span data-stu-id="ff65c-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="ff65c-127">Zadejte kódování zprávy přidáním prvku kódování, například [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="ff65c-128">Zadejte přenos přidáním prvku přenosu, jako je například [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="ff65c-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="ff65c-129">Následující příklad kódu používá konfiguraci k určení vlastní vazby, kterou mohou zprávy používat se stavovými st v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ff65c-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ff65c-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff65c-130">Example</span></span>  
 <span data-ttu-id="ff65c-131">Následující příklad kódu vytvoří vlastní vazbu, která používá režim <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> ověřování k zavádění zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="ff65c-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="ff65c-132">Při ověřování systému Windows se používá v kombinaci se <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> stavovou SCT, WCF nenaplní vlastnost s identitou skutečného volajícího, ale místo toho nastaví vlastnost anonymní.</span><span class="sxs-lookup"><span data-stu-id="ff65c-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="ff65c-133">Vzhledem k tomu, že zabezpečení WCF musí znovu vytvořit obsah kontextu zabezpečení služby pro každý požadavek z příchozí hospo-</span><span class="sxs-lookup"><span data-stu-id="ff65c-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="ff65c-134">Protože není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instanci do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrátí anonymní identitu.</span><span class="sxs-lookup"><span data-stu-id="ff65c-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="ff65c-135">Následující konfigurace vykazuje toto chování.</span><span class="sxs-lookup"><span data-stu-id="ff65c-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff65c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff65c-136">See also</span></span>

- [<span data-ttu-id="ff65c-137">\<vlastní vazba></span><span class="sxs-lookup"><span data-stu-id="ff65c-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
