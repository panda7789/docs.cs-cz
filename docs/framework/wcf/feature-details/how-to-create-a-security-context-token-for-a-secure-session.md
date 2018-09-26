---
title: 'Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
ms.openlocfilehash: 85954dd89bdb576b68d234a364a406a6e0d2145b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203745"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="ef98b-102">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="ef98b-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="ef98b-103">Pomocí tokenu kontextu zabezpečení stavové (SCT) v zabezpečené relaci dokázal relace neumožňovala recyklaci služby.</span><span class="sxs-lookup"><span data-stu-id="ef98b-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="ef98b-104">Například při bezstavové SCT se používá v zabezpečené relaci a obnovit Internetové informační služby (IIS), potom data relace, která souvisí se službou se ztratí.</span><span class="sxs-lookup"><span data-stu-id="ef98b-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="ef98b-105">Tato data relace zahrnují SCT mezipaměť tokenu.</span><span class="sxs-lookup"><span data-stu-id="ef98b-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="ef98b-106">Proto při příštím klient odešle službě bezstavové SCT vrátí chybu, protože klíč, který je přidružený k SCT nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="ef98b-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="ef98b-107">Pokud však použijete stavové SCT, klíč, který je přidružený k SCT obsažené v SCT.</span><span class="sxs-lookup"><span data-stu-id="ef98b-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="ef98b-108">Protože klíč je součástí SCT a proto v něm obsažené, nemá vliv službu neumožňovala recyklaci, zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="ef98b-109">Ve výchozím nastavení používá Windows Communication Foundation (WCF) bezstavové SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="ef98b-110">Toto téma podrobně popisuje, jak použít stavová SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef98b-111">Stavové SCTs nelze použít v zabezpečené relaci, která zahrnuje kontrakt, který je odvozen od <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="ef98b-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef98b-112">Pro aplikace, které používají stavové SCTs v zabezpečené relaci identitu vlákna služby musí být uživatelský účet, který se má profil přidruženého uživatele.</span><span class="sxs-lookup"><span data-stu-id="ef98b-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="ef98b-113">Když je služba spuštěna pod účtem, který nemá profil uživatele, jako například `Local Service`, může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ef98b-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef98b-114">Když zosobnění je potřeba na Windows XP, použijte zabezpečené relaci bez stavové SCT.</span><span class="sxs-lookup"><span data-stu-id="ef98b-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="ef98b-115">Když zosobnění, se používají stavové SCTs <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ef98b-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="ef98b-116">Další informace najdete v tématu [nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="ef98b-117">Použití stavové SCTs v zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="ef98b-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="ef98b-118">Vytvoření vlastní vazby, která určuje, že zprávy protokolu SOAP jsou chráněné službou, která používá stavové SCT zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="ef98b-119">Definujte vlastní vazbu tak, že přidáte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="ef98b-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="ef98b-120">Přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ef98b-121">Zadejte název vazby tak, že nastavíte `name` atribut jedinečný název v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ef98b-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="ef98b-122">Zadejte režim ověřování pro zprávy odeslané do a z této služby tak, že přidáte [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) podřízený element pro [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ef98b-123">Určí, že je použit zabezpečenou relaci tak, že nastavíte `authenticationMode` atribut `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="ef98b-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="ef98b-124">Určete, že se používají stavové SCTs nastavením `requireSecurityContextCancellation` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="ef98b-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="ef98b-125">Zadejte, jak je ověření klienta při vytvoření zabezpečené relace tak, že přidáte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element pro [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="ef98b-126">Zadejte, jak proběhne ověření nastavení klienta `authenticationMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="ef98b-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="ef98b-127">Určete kódování zprávy přidáním element kódování [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="ef98b-128">Zadejte přenos přidáním element přenosu [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="ef98b-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="ef98b-129">Následující příklad kódu používá konfigurace k určení vlastní vazby, zprávy můžete použít s stavové SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ef98b-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef98b-130">Example</span></span>  
 <span data-ttu-id="ef98b-131">Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování ke spuštění zabezpečenou relaci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="ef98b-132">Při ověřování Windows se používá v kombinaci s stavové SCT, WCF nevyplní <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost s skutečné volající vaší identity, ale místo toho vlastnost nastavena na anonymní.</span><span class="sxs-lookup"><span data-stu-id="ef98b-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="ef98b-133">Protože zabezpečení WCF muset znovu vytvořit obsah kontext zabezpečení služby pro každý požadavek z příchozí SCT, server přehled o zabezpečení relací v paměti.</span><span class="sxs-lookup"><span data-stu-id="ef98b-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="ef98b-134">Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instance do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> anonymní identity vrátí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ef98b-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="ef98b-135">Toto chování je třeba následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ef98b-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef98b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef98b-136">See Also</span></span>  
 [<span data-ttu-id="ef98b-137">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="ef98b-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
