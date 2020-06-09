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
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="1c4b2-102">Postupy: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci</span><span class="sxs-lookup"><span data-stu-id="1c4b2-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="1c4b2-103">Při použití tokenu kontextového kontextu zabezpečení (SCT) v zabezpečené relaci může relace vydržet recyklaci služby.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="1c4b2-104">Například pokud se v zabezpečené relaci používá bezstavový SCT a resetuje se Internetová informační služba (IIS), data relace přidružená ke službě budou ztracena.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="1c4b2-105">Tato data relace zahrnují mezipaměť tokenů SCT.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="1c4b2-106">Takže když klient příště odešle službu bezstavový SCT, vrátí se chyba, protože klíč, který je přidružený k SCT, nejde načíst.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="1c4b2-107">Pokud se ale používá stavový SCT, pak klíč, který je přidružený k SCT, je obsažený v SCT.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="1c4b2-108">Vzhledem k tomu, že klíč je obsažen v SCT, a proto obsažený v rámci zprávy, není tato služba ovlivněna tím, že je zajištěna její zabezpečená relace.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="1c4b2-109">Ve výchozím nastavení používá Windows Communication Foundation (WCF) v zabezpečené relaci bezstavový SCTs.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="1c4b2-110">Toto téma popisuje, jak používat stav SCTs v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c4b2-111">Stavový SCTs nelze použít v zabezpečené relaci, která zahrnuje kontrakt odvozený od <xref:System.ServiceModel.Channels.IDuplexChannel> .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c4b2-112">Pro aplikace, které používají stav SCTs v zabezpečené relaci, musí být identita vlákna pro službu uživatelským účtem, který má přidružený profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="1c4b2-113">Když je služba spuštěna pod účtem, který nemá profil uživatele, například `Local Service` , může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c4b2-114">Pokud je v systému Windows XP vyžadován zosobnění, použijte zabezpečenou relaci bez stavového SCT.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="1c4b2-115">Pokud se pro zosobnění použijí stavová SCTs, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="1c4b2-116">Další informace najdete v tématu [nepodporované scénáře](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="1c4b2-116">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="1c4b2-117">Použití stavového SCTsu v zabezpečené relaci</span><span class="sxs-lookup"><span data-stu-id="1c4b2-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="1c4b2-118">Vytvořte vlastní vazbu, která určuje, že zprávy SOAP jsou chráněny zabezpečenou relací, která používá stavový SCT.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="1c4b2-119">Definujte vlastní vazbu přidáním [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) do konfiguračního souboru pro službu.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-119">Define a custom binding, by adding a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="1c4b2-120">Přidejte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) podřízený element do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="1c4b2-121">Zadejte název vazby nastavením `name` atributu na jedinečný název v rámci konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="1c4b2-122">Zadejte režim ověřování pro zprávy odesílané do a z této služby přidáním [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) podřízeného elementu do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="1c4b2-123">Určete, že se zabezpečená relace používá, nastavením `authenticationMode` atributu na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="1c4b2-124">Určete, že stavová SCTs jsou použita nastavením `requireSecurityContextCancellation` atributu na `false` .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="1c4b2-125">Určete, jak se má klient ověřovat, když je zabezpečená relace navázána přidáním [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízeného elementu do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="1c4b2-126">Určete, jak se má klient ověřit, nastavením `authenticationMode` atributu.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="1c4b2-127">Určete kódování zprávy přidáním elementu kódování, například [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="1c4b2-128">Určete přenos přidáním elementu Transport, jako je například [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4b2-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="1c4b2-129">Následující příklad kódu používá konfiguraci k určení vlastní vazby, kterou mohou zprávy používat se stavovým SCTsem v zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1c4b2-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c4b2-130">Example</span></span>  
 <span data-ttu-id="1c4b2-131">Následující příklad kódu vytvoří vlastní vazbu, která <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pro spuštění zabezpečené relace používá režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="1c4b2-132">Pokud se používá ověřování systému Windows v kombinaci se stavovým SCT, WCF neplní <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost skutečným identifikátorem volajícího, ale místo toho nastaví vlastnost na hodnotu Anonymous.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="1c4b2-133">Vzhledem k tomu, že zabezpečení WCF musí znovu vytvořit obsah kontextu zabezpečení služby pro každý požadavek z příchozího SCT, server nesleduje relaci zabezpečení v paměti.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="1c4b2-134">Vzhledem k tomu, že není možné serializovat <xref:System.Security.Principal.WindowsIdentity> instanci do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost vrací anonymní identitu.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="1c4b2-135">Toto chování se projeví v následující konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1c4b2-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c4b2-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c4b2-136">See also</span></span>

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
